---
title: "Problems linking code on a G5"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by FatPhil on 2006-06-06
First post here - very quick intro: Linux user since 1993. Familiar working with and developing on Debian x86 and Alpha, but new to PPC-land. 

I have a long-term loan of a dual G5 'Mac', and wish to migrate from OSX to linux. I have to use a live-CD as I can't install a new OS on the HD. I have dselected gcc-4.0 and g++-4.0, with supporting libraries, and I looked hot to trot, but alas having a spot of bother building (my own package based on) DJBFFT ( [http://cr.yp.to/djb/](http://cr.yp.to/djb/) ).

All the compilation works correctly, it's just the linking that fails:
<<<
[FONT="Courier New"]./load accuracy djbfft.a  `cat math.lib`
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.0.2/../../.. /libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.0.2/../../.. /libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libm.so when searching for -l m
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libm.a when searching for -lm
/usr/bin/ld: cannot find -lm
collect2: ld returned 1 exit status
make: *** [accuracy] Error 1
ubuntu@ubuntu:~/Desktop/djbfft$ cat conf-cc
gcc-4.0 -O2 -g -fomit-frame-pointer -foptimize-sibling-calls -fregmove -fcaller-saves -mcpu=G5 -m64
ubuntu@ubuntu:~/Desktop/djbfft$ cat conf-ld
gcc-4.0 -g -m64
ubuntu@ubuntu:~/Desktop/djbfft$ cat math.lib
-lm[/FONT]
>>>

I tried bypassing gcc-4.0, but as everything in the past has almost always just worked out of the box (on about a dozen architectures, but noticably the other failure is OSX) I'm not completely au fait with ld's switches. I iterated towards the following, which is a failure, but seems closer to  working than the above:

<<<
[FONT="Courier New"]ubuntu@ubuntu:~/Desktop/djbfft$ ld -melf64ppc -o accuracy accuracy.o djbfft.a /usr/lib/libc.a /usr/lib/libm.a
ld: warning: cannot find entry symbol _start; defaulting to 0000000010026040
accuracy.o: In function `fill8':
/home/ubuntu/Desktop/djbfft/accuracy.c:78: undefined reference to `.nan'
accuracy.o: In function `err4':
/home/ubuntu/Desktop/djbfft/accuracy.c:109: undefined reference to `.sqrt'
accuracy.o: In function `err8':
/home/ubuntu/Desktop/djbfft/accuracy.c:123: undefined reference to `.sqrt'
accuracy.o: In function `doitr4':
/home/ubuntu/Desktop/djbfft/accuracy.c:157: undefined reference to `.printf'
accuracy.o: In function `doitr8':
/home/ubuntu/Desktop/djbfft/accuracy.c:191: undefined reference to `.printf'
accuracy.o: In function `doitc4':
/home/ubuntu/Desktop/djbfft/accuracy.c:215: undefined reference to `.printf'
accuracy.o: In function `doitc8':
/home/ubuntu/Desktop/djbfft/accuracy.c:240: undefined reference to `.printf'
accuracy.o: In function `main':
/home/ubuntu/Desktop/djbfft/accuracy.c:302: undefined reference to `.exit'
[/FONT]
>>>

If anyone could get DJBFFT building and working on their own Linux G5 I'd be most thankful for advice on what I'm doing wrong.

Shameless plug - the G5 is possibly one of the best architectures around for number-crunching, and if anyone wants to join my large-prime-number hunting projects, please do make yourself known. ( [http://primepages.org/](http://primepages.org/) , projects 'PIES', and 'Les GeneFermiers'). 

Phil

---

### Post by FatPhil on 2006-06-06
[QUOTE=FatPhil]
ubuntu@ubuntu:~/Desktop/djbfft$ cat conf-cc
gcc-4.0 -O2 -g -fomit-frame-pointer -foptimize-sibling-calls -fregmove -fcaller-saves -mcpu=G5 -m64
ubuntu@ubuntu:~/Desktop/djbfft$ cat conf-ld
gcc-4.0 -g -m64
>>>

-m64 was the problem. I was brainwashed by OSX dudes into thinking it was necessary, but it isn't. In fact, with it, even a simple helloworld.c fails to compile!

Close the ticket ;-)

---

