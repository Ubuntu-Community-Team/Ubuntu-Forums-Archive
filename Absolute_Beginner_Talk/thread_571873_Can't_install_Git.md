---
title: "Can't install Git"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Sam324 on 2007-10-09
Hi!  I'm totally new to Ubuntu and Linux as a whole, and I hope to learn some stuff about it here.  My problem is that I can't install Git.  I did the method I just learned:  in the console, typing ./configure in the correct dir, typing make, and then sudo make install.  I got as far as the ./configure part and at the Make it said error:  File not found.  I got the Tar.Bz2 of the latest version.  This is what it said:

```
sam@HP-Pavilion:~$ cd ./desktop/git-1.5.3.4
bash: cd: ./desktop/git-1.5.3.4: No such file or directory
sam@HP-Pavilion:~$ cd /home/sam/Desktop/git-1.5.3.4
sam@HP-Pavilion:~/Desktop/git-1.5.3.4$ ./configure
configure: CHECKS for programs
checking for cc... cc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ANSI C... none needed
checking for gar... no
checking for ar... ar
checking for gtar... no
checking for tar... tar
configure: CHECKS for libraries
checking for SHA1_Init in -lcrypto... no
checking for SHA1_Init in -lssl... no
checking for curl_global_init in -lcurl... no
checking for XML_ParserCreate in -lexpat... no
checking for iconv in -lc... yes
checking for socket in -lc... yes
configure: CHECKS for typedefs, structures, and compiler characteristics
checking for struct dirent.d_ino... yes
checking for struct dirent.d_type... yes
checking for struct sockaddr_storage... yes
checking for struct addrinfo... yes
checking for getaddrinfo... yes
checking how to run the C preprocessor... cc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether formatted IO functions support C99 size specifiers... yes
configure: CHECKS for library functions
checking for strcasestr... yes
checking for strlcpy... no
checking for setenv... yes
configure: CHECKS for site configuration
configure: creating ./config.status
config.status: creating config.mak.autogen
sam@HP-Pavilion:~/Desktop/git-1.5.3.4$ make
GIT_VERSION = 1.5.3.4
    * new build flags or prefix
    CC convert-objects.o
In file included from convert-objects.c:1:
cache.h:7:18: error: zlib.h: No such file or directory
make: *** [convert-objects.o] Error 1
sam@HP-Pavilion:~/Desktop/git-1.5.3.4$ make install
    CC convert-objects.o
In file included from convert-objects.c:1:
cache.h:7:18: error: zlib.h: No such file or directory
make: *** [convert-objects.o] Error 1
sam@HP-Pavilion:~/Desktop/git-1.5.3.4$ sudo make
Password:
    CC convert-objects.o
In file included from convert-objects.c:1:
cache.h:7:18: error: zlib.h: No such file or directory
make: *** [convert-objects.o] Error 1
sam@HP-Pavilion:~/Desktop/git-1.5.3.4$ 

```

---

### Post by llamakc on 2007-10-09
Are the versions of Git in the repositories too old?

---

### Post by Hospadar on 2007-10-09
you could install git through apt with ```
sudo apt-get install git
``` Or if you really want to build it, it looks like you need the zlib dev files, try doing a ```
 sudo apt-get install zlib1g-dev
``` to get the header files.

---

### Post by Sam324 on 2007-10-10
Thanks.  It installed okay, but when I try to open git://git.kernel.org/pub/scm/linux/kernel/git/linville/wireless-dev.git it says firefox can't open it b/c there is no associated program.

---

### Post by nick_h on 2007-10-10
Why are you using Firefox?  Have a read [here](https://wiki.ubuntu.com/KernelGitGuide). I think you need the git clone command.

---

### Post by Sam324 on 2007-10-11
> **nick_h said:**
> Why are you using Firefox?  Have a read [here](https://wiki.ubuntu.com/KernelGitGuide). I think you need the git clone command.

After installing the git-core package, I typed this into the Terminal:
```
sam@HP-Pavilion:~$ sudo git clone git://git.kernel.org/pub/scm/linux/kernel/git/linville/wireless-dev.git

git, the filemanager with GNU Interactive Tools, is now called gitfm.

If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).

This transition script will be removed in the debian stable
release after etch.

If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git

Press RETURN to run gitfm


GNU Interactive Tools 4.3.20 (x86_64-unknown-linux-gnu), 07:48:07 Nov 10 2006
GIT is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.
Copyright (C) 1993-1999 Free Software Foundation, Inc.
Written by Tudor Hulubei and Andrei Pitis, Bucharest, Romania

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.
sam@HP-Pavilion:~$ 

```
and that's what it gave me.  I tried prefixing it with "sudo" also and it yielded the same results.

---

### Post by nick_h on 2007-10-11
You need to add a target directory to the end of your command.

---

### Post by Steveway on 2007-10-11
Don't use sudo for that command!
Also look carefully in Synaptic for the git-packages you installed.
Afaik there is one also called git that spits that error out if it is installed and you try to git clone something.

---

### Post by nick_h on 2007-10-11
Yes, it is confusing that there is also another git package.  The one the OP needs is git-core and not git.

As you say there is also no need for sudo.  I install kernel source in a directory under my home directory.  Compilation does not need to be done as root.  Only the installation will require to be done as root.

---

