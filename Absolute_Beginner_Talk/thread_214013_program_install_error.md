---
title: "program install error"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-07-12
Hi all,
       getting the following error trying to install a program from the command line. Would appreciate any explanatons of what error nasm or error 127 is. Ta heaps
```
 -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -s -fomit-fram e-pointer -DHAVE_GETOPT_LONG=1 common/i386/predict.c -MM -g0 ) 1>> .depend;  ( e cho -n "`dirname x264.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MA LLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska .c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 matroska.c -MM -g0 ) 1>> .depend;
nasm -f elf -o common/i386/dct-a.o common/i386/dct-a.asm
make: nasm: Command not found
make: *** [common/i386/dct-a.o] Error 127
jeremy@ubuntu:~/jeremy/PSP/pspvc-install-0.2/work/x264_051028$ sudo make install nasm -f elf -o common/i386/dct-a.o common/i386/dct-a.asm
make: nasm: Command not found
make: *** [common/i386/dct-a.o] Error 127
jeremy@ubuntu:~/jeremy/PSP/pspvc-install-0.2/work/x264_051028$ pspvc v0.2
bash: pspvc: command not found
jeremy@ubuntu:~/jeremy/PSP/pspvc-install-0.2/work/x264_051028$ sudo install
install: too few arguments
Try `install --help' for more information.


```

---

### Post by croak77 on 2006-07-12
First, what are you installing?

Second, do you have nasm installed? sudo apt-get install nasm

---

### Post by mogelhead on 2006-07-12
Seems like you are compiling your program from source.

Is it PSP Video Converter?

Do you have all the needed packages installed?
Because it seems that you don't have nasm installed.

On the page [http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/), it says you need the following tools/libraries:     
* nasm
* libfaac
* libxvidcore
* gtk+2.0

---

### Post by carverj on 2006-07-12
Yup, should be the missing peice of the puzzle
Thanks hugely and yup, converting a vid to psp
maybe I should try running Ubuntu on the psp 
after that!! :mrgreen:

---

### Post by carverj on 2006-07-12
hmmm, its a brand new error.... error 1 :

```
jeremy@ubuntu:~/jeremy/PSP/pspvc-install-0.2/work/x264_051028$ sudo make install nasm -f elf -o common/i386/dct-a.o common/i386/dct-a.asm
nasm -f elf -o common/i386/cpu-a.o common/i386/cpu-a.asm
nasm -f elf -o common/i386/pixel-a.o common/i386/pixel-a.asm
nasm -f elf -o common/i386/mc-a.o common/i386/mc-a.asm
nasm -f elf -o common/i386/mc-a2.o common/i386/mc-a2.asm
nasm -f elf -o common/i386/predict-a.o common/i386/predict-a.asm
nasm -f elf -o common/i386/pixel-sse2.o common/i386/pixel-sse2.asm
nasm -f elf -o common/i386/quant-a.o common/i386/quant-a.asm
ar rc libx264.a common/mc.o common/predict.o common/pixel.o common/macroblock.o common/frame.o common/dct.o common/cpu.o common/cabac.o common/common.o common/m date.o common/csp.o common/set.o common/quant.o encoder/analyse.o encoder/me.o e ncoder/ratecontrol.o encoder/set.o encoder/macroblock.o encoder/cabac.o encoder/ cavlc.o encoder/encoder.o encoder/eval.o common/i386/mc-c.o common/i386/dct-c.o common/i386/predict.o common/i386/dct-a.o common/i386/cpu-a.o common/i386/pixel- a.o common/i386/mc-a.o common/i386/mc-a2.o common/i386/predict-a.o common/i386/p ixel-sse2.o common/i386/quant-a.o
ranlib libx264.a
gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SS E2 -DARCH_X86 -DSYS_LINUX -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1   -c -o x 264.o x264.c
x264.c: In function ‘Parse’:
x264.c:772: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:773: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:774: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:775: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:779: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:780: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:784: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:785: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:789: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:790: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:794: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:798: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:802: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:806: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:810: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
x264.c:814: warning: pointer targets in passing argument 2 of ‘parse_cqm’ differ  in signedness
gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SS E2 -DARCH_X86 -DSYS_LINUX -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1   -c -o m atroska.o matroska.c
gcc -o x264 x264.o matroska.o libx264.a -lm -s
libx264.a(encoder.o): In function `x264_encoder_encode':
encoder.c:(.text+0x51ff): undefined reference to `pthread_create'
encoder.c:(.text+0x5235): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
make: *** [x264] Error 1

```

---

### Post by mogelhead on 2006-07-12
Sorry, I haven't got a clue.

Try contacting the developers of the software.

[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

Although, their forums on sourceforge are empty.

---

