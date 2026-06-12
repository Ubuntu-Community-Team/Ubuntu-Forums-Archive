---
title: "How to choose SYSTEM?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by bobetko on 2007-09-05
I am supposed to compile application executing "make clean SYSTEM", where my system is one of the items on the list below. The question is which one?

I tried generic, linux-x86-any, linux-x86-mmx, non of them work. I have Pentium4 dell PC withu Ubuntu Feisty.... Thanks for help.....


linux-x86-mmx            Linux, x86 with MMX (best)
linux-x86-any            Linux, x86
linux-x86-any-a.out      Linux, x86, a.out binaries (obsolete)
linux-x86-64             Linux, AMD x86-64, 64-bit native
linux-x86-64-mmx         Linux, AMD x86-64, 32-bit with MMX
linux-alpha              Linux, Alpha
linux-sparc              Linux, SPARC 32-bit
linux-ppc32-altivec      Linux, PowerPC w/AltiVec (best)
linux-ppc32              Linux, PowerPC 32-bit
linux-ppc64              Linux, PowerPC 64-bit
freebsd-x86-mmx          FreeBSD, x86 with MMX (best)
freebsd-x86-any          FreeBSD, x86
freebsd-x86-any-a.out    FreeBSD, x86, a.out binaries (obsolete)
freebsd-alpha            FreeBSD, Alpha
openbsd-x86-mmx          OpenBSD, x86 with MMX (best)
openbsd-x86-any          OpenBSD, x86
openbsd-x86-any-a.out    OpenBSD, x86, a.out binaries (obsolete)
openbsd-x86-64           OpenBSD, AMD x86-64
openbsd-alpha            OpenBSD, Alpha
openbsd-sparc64          OpenBSD, SPARC 64-bit (best)
openbsd-sparc            OpenBSD, SPARC 32-bit
openbsd-sparc-a.out      OpenBSD, SPARC 32-bit (obsolete)
openbsd-ppc32            OpenBSD, PowerPC 32-bit
openbsd-ppc64            OpenBSD, PowerPC 64-bit
openbsd-pa-risc          OpenBSD, PA-RISC
openbsd-vax              OpenBSD, VAX
netbsd-vax               NetBSD, VAX
solaris-sparc64-cc       Solaris, SPARC V9 64-bit, cc (best)
solaris-sparc64-gcc      Solaris, SPARC V9 64-bit, gcc
solaris-sparcv9-cc       Solaris, SPARC V9 32-bit, cc
solaris-sparcv8-cc       Solaris, SPARC V8 32-bit, cc
solaris-sparc-gcc        Solaris, SPARC 32-bit, gcc
solaris-x86-any          Solaris, x86, gcc
sco-x86-any-gcc          SCO, x86, gcc
sco-x86-any-cc           SCO, x86, cc
tru64-alpha              Tru64 (Digital UNIX, OSF/1), Alpha
aix-ppc32                AIX, PowerPC 32-bit
macosx-ppc32-altivec     Mac OS X, PowerPC w/AltiVec (best)
macosx-ppc32             Mac OS X, PowerPC 32-bit
macosx-ppc64             Mac OS X 10.4+, PowerPC 64-bit
macosx-x86-mmx           Mac OS X, x86 with MMX
hpux-pa-risc-gcc         HP-UX, PA-RISC, gcc
hpux-pa-risc-cc          HP-UX, PA-RISC, ANSI cc
irix-mips64-r10k         IRIX, MIPS 64-bit (R10K) (best)
irix-mips64              IRIX, MIPS 64-bit
irix-mips32              IRIX, MIPS 32-bit
dos-djgpp-x86-mmx        DOS, DJGPP 2.x, x86 with MMX (best)
dos-djgpp-x86-any        DOS, DJGPP 2.x, x86
win32-cygwin-x86-mmx     Win32, Cygwin, x86 with MMX (best)
win32-cygwin-x86-any     Win32, Cygwin, x86
beos-x86-mmx             BeOS, x86 with MMX
beos-x86-any             BeOS, x86
generic                  Any other Unix-like system with gcc

---

### Post by bobetko on 2007-09-05
hm... should I rephrase this question?

---

### Post by jerutley on 2007-09-05
This looks like the machine types output from trying to compile OpenSSL.  A lot depends on whether you have the 64-bit version of Ubuntu, or the 32-bit version.  There's a good chance that if you're using the 64-bit version, you may not get it to compile correctly without hacking the source code  - the problem is that *most* 64-bit distributions of Linux are "Multi-lib," meaning they include both 32-bit libraries in /usr/lib as well as 64-bit libraries in /usr/lib64 - and a lot of configure scripts will expect that.  However, Ubuntu is a "pure64" environment, and has no 32-bit compatibility, so configure scripts that expect a multi-lib 64-bit distro will fail.

However, if you're running the 32-bit version of Ubuntu, I'd bet the problem is you don't have some development packages installed - giving us error output from your compile might help.

---

### Post by bobetko on 2007-09-05
I have Feisty Fawn... Since my laptop is centrino 32-bit, OS should be 32 bit.
here is the error after **make clean generic**:

rm -f ../run/john ../run/unshadow ../run/unafs ../run/unique ../run/john.bin ../run/john.com ../run/unshadow.com ../run/unafs.com ../run/unique.com ../run/john.exe ../run/unshadow.exe ../run/unafs.exe ../run/unique.exe
rm -f ../run/john.exe *.o *.bak core
rm -f detect bench generic.h arch.h sparc.h tmp.s
rm -f DES_bs_s.c DES_bs_n.c DES_bs_a.c
cp /dev/null Makefile.dep
rm -f arch.h
gcc -c -Wall -O2 -fomit-frame-pointer detect.c
detect.c:10:19: error: stdio.h: No such file or directory
detect.c: In function ‘main’:
detect.c:22: warning: implicit declaration of function ‘puts’
detect.c:30: warning: implicit declaration of function ‘printf’
detect.c:30: warning: incompa

---

### Post by jerutley on 2007-09-05
> **bobetko said:**
> 
detect.c:10:19: error: stdio.h: No such file or directory



And we have a winner!  That right there is your error in the compile, and that tells me that you definately do not have an adequate software build environment installed.  stdio.h is a header file provided by glibc, and contains various standard function definitions for I/O (hence the name).  A good start will be to run the following at the command line:

sudo apt-get install build-essential

That will pull in a lot of the essential packages (including -devel packages which include the header files) for compiling software.

But, looking at this, it definately looks like you're building OpenSSL - there should already be a package available for that in the repository *shrug*

---

### Post by bobetko on 2007-09-05
thanks a lot. That helped.

---

