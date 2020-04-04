Sample Drivers

To debug the kernel oops refer:
~~~
http://opensourceforu.com/2011/01/understanding-a-kernel-oops/
~~~

GDB cmds:
~~~
#$]gdb oops.ko
#(gdb) add-symbol-file oops.o
#(gdb) disassemble my_oops_init
Dump of assembler code for function my_oops_init:
   0x000000000000004c <+0>:	callq  0x51 <my_oops_init+5>
   0x0000000000000051 <+5>:	mov    $0x0,%rdi
   0x0000000000000058 <+12>:	callq  0x5d <my_oops_init+17>
   0x000000000000005d <+17>:	mov    $0xa,%esi
   0x0000000000000062 <+22>:	mov    $0x0,%rdi
   0x0000000000000069 <+29>:	callq  0x6e <my_oops_init+34>
   0x000000000000006e <+34>:	xor    %eax,%eax
   0x0000000000000070 <+36>:	movl   $0x0,0x0     <========================= (NULL) pointer copy.
   0x000000000000007b <+47>:	retq
End of assembler dump.
#(gdb) list * 0x0000000000000070
{
	<CODE WILL BE VISIBLE HERE>
}
~~~
