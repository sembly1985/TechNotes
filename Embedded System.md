************************ ARM 浮点选项 ************************

-mfloat-abi=soft
-mfloat-abi=softfp
-mfloat-abi=hard


"soft"选项：表明不使用FPU硬件，而是使用GCC的整数算术运算来模拟浮点运算。
"softfp"选项：表明要使用FPU硬件来做浮点运算，只是，函数的参数传递到整数寄存器（r0-r3）中，然后再传递到FPU中。
"hard"选项：表明要使用FPU硬件来做浮点运算，并且，函数的参数直接传递到FPU的寄存器（s0、d0）中。
用-mfloat-abi=soft编译的app或者库，在用-mfloat-abi=softfp编译的OS中是可以跑的；
用-mfloat-abi=softfp编译的app或者库，在用-mfloat-abi=soft编译的OS中，如果SoC中没有FPU，那么是不能跑的。
而-mfloat-abi=softfp/soft与-mfloat-abi=hard，是互不兼容的。

* c28x 编译 fp_mode应设置为 relax，编译自动调用FPU或TMU进行浮点运算；求倒数、开根号，TMU更快

* c28x 函数调用和中断调用的入栈操作参考文件spru403f。其中RPC寄存器用于保存返回地址。
