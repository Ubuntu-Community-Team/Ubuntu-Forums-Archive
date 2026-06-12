---
title: "make menuconfig error"
date: 2006-09-19
forum: Apple PPC Users
---

### Post by emkersyt on 2006-09-19
Hi all,
I'm trying to compile the kernel of Ubuntu Dapper Drake 6.0 6LTS on a 12"Powerbook G4, 1,5Ghz. I'm quite new to this so I'm a bit lost now even if the solution might be simple.  

After installing from the Live-Desktop-CD y just got the source 2.6.15 with Synaptics downloaded directly in the /usr/src dir. After decompressing I created the softlink "linux" in the same directory pointing to the new unpacked linux-source-2.6.15.
Then I tried to execute make menuconfig but it gives me the following error back:

emkersyt@kvlarsylix:/usr/src/linux-source-2.6.15$ sudo make menuconfig
Password:
/usr/src/linux-source-2.6.15/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-source-2.6.15/scripts/gcc-version.sh: line 12: gcc: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

So I locked up the compiler-version with:

cat /proc/version
Linux version 2.6.15-23-powerpc (buildd@ross) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Tue May 23 13:46:54 UTC 2006

This tells me that I'm using gcc version 4.0.3 which should be ok, I guess?

Synaptic tells me that the gcc-4.0-base package was already installed. I added also the gcc-4.0 package (C-compiler). 

Doesn't seem to change anything. The menuconfig-dialog won't come up. 

Somebody has got any idea how to fix that problem?

---

### Post by APU on 2006-09-20
You might miss the "kernel-package" and the "nurses-dev" packages. Install them using Synaptics and then try again. A good howto can be found at [URL="http://www.howtoforge.com/howto_linux_kernel_2.6_compile_debian"] (Yes it´s Debian but Ubuntu behaves exactliy alike it in this case).

BTW: I have a similar PowerBook and use a 2.6.17 kernel (might compile the 2.6.18 today). Since you don´t need any specific unfree driver modules on this Machine it is not really necessary to stick to the ubuntu sources.

---

### Post by stmiller on 2006-09-20
Try to apt-get install build-essential

---

### Post by emkersyt on 2006-09-22
Thanks alot! Problem solved. I installed first kernel-package but it didn't change. 
Then I got build-essential installed and finally it worked.

---

