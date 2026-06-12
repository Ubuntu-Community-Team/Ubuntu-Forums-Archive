---
title: "Compiling a new Kernel"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by SierraKilo on 2007-02-21
Hi everyone, it's me again.
Since I couldn't solve the network problem I had earlier, I tried to update my kernel (for the last 5-6h). I currently use a fresh Ubuntu 6.10 installation.
I downloaded the newest kernel from kernel.org, and followed the instruction from this source:
[http://www.linuxheadquarters.com/howto/tuning/kernelsources.shtml]("http://www.linuxheadquarters.com/howto/tuning/kernelsources.shtml")
Problem is, everytime I try to start xconfig (or menuconfig) to configure my new kernel I just get this response:

root@skneidl-desktop:/usr/src/linux# make xconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:129: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:129: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:138: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:154: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:172: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:185: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:204: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:218: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:204: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:225: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:242: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:255: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:266: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:270: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:272: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:278: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:281: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:281: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:290: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:266: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:298: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:304: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:300: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:337: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:341: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:343: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:353: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:337: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:372: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

I already tried numerous different kernel-versions, all with the same result.
I hope someone can tell me what I've done wrong, because I have no clue what ubuntu is trying to tell me ;)

---

### Post by energiya on 2007-02-21
try [this]("http://www.ubuntuforums.org/showthread.php?t=311158"). Also you might not get it right the first time, and other compilations will be necessary.

---

### Post by tageiru on 2007-02-21
It is telling you that you have a screwed up compiler toolchain, install build-essential.

---

### Post by SierraKilo on 2007-02-21
That was quick... I'll try that right away, thanks!

---

### Post by SierraKilo on 2007-02-21
Okay, the problem persists. I get stuck at the first step of the instructions you posted...

root@skneidl-desktop:/usr/src/# apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev && cd /usr/src
Reading package lists... Done
Building dependency tree
reading state information... Done
E: Couldn't find package build-essential
root@skneidl-desktop:/usr/src/#

Any ideas?

---

### Post by george29 on 2007-02-21
have you made sure that you have all the repositories enabled - you need universe and multiverse.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by SierraKilo on 2007-02-21
now I have ;)
but i'm still getting some errors due to the missing internet-connection...
Now I get till:
root@skneidl-desktop:/boot/# cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
make: *** No rule to make target 'oldconfig'.  Stop.

Sorry to keep buging you, but for the most part i have no idea what I'm doing...

---

### Post by george29 on 2007-02-21
from what i'm seeing you - others will correct me if i'm wrong....

you need to change what you are typing in the console from

 cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig

and replace 'uname -r' 

if you type uname -r on it's own in a console and hit return it will tell you which kernel you are running - put that instead of uname -r.

edit: it'll be something like linux.2.6.18-25 

sorry i'm on my work xp computer so can't be more specific.

george

---

### Post by SierraKilo on 2007-02-21
Just tried it, and I keep getting the same response:
root@skneidl-desktop:/boot/# cp /boot/config-2.6.17-10-generic .config && sudo make oldconfig && sudo make xconfig
make: *** No rule to make target 'oldconfig'. Stop.

---

### Post by george29 on 2007-02-21
try this how to - 

[http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html)

i've used it successfully to update my debian etch laptop from kernel 2.6.15 to 2.6.20 and it should work with ubuntu too.  My desktop just runs the stock ubuntu kernel with no problems - so i've never needed to recompile it.

---

### Post by SierraKilo on 2007-02-21
sorry, didn't work either. As soon as I enter 'make menuconfig' I get an error-message similar to the one in my first post...
Could the problem be that I have no internet-connection due to the forcedeth-incompatibility? I don't see how it could be, but at this point I'm considering anything...

---

### Post by Bachstelze on 2007-02-21
You need to use sudo to *make menuconfig*. Are you sure you have build-essential installed ?

---

### Post by george29 on 2007-02-21
hmmm... i've got no idea i'm afraid... 

i don't see why having no internet connection should be a problem. if you have all the packages you need installed and the kernel source code then everything should work fine.

i would try removing everything that you've altered, so put the original kernel.bz2 file that you downloaded in a safe place.. delete everything else in that you created in /usr/src, reboot and start again with the technowizah tutorial.

see what happens.

then post up any error messages you get.

george

---

### Post by SierraKilo on 2007-02-21
I was logged-in as root, so I didn't have to input sudo for every single command.
Concerning the build-essentials: I'm not even sure what they are, how can I check if they are installed? Like I said, this is the second day I use linux..

---

### Post by SierraKilo on 2007-02-21
> **george29 said:**
> 
i would try removing everything that you've altered, so put the original kernel.bz2 file that you downloaded in a safe place.. delete everything else in that you created in /usr/src, reboot and start again with the technowizah tutorial.


I always started from scratch every time... but thanks for the help anyway...:(

---

### Post by Bachstelze on 2007-02-21
```
sudo apt-get install build-essential
```

---

### Post by george29 on 2007-02-21
when i compiled my new kernel for my etch laptop i did it all as a normal user the only time i used sudo was to at the beginning:

sudo adduser src

and at the end to install the built package.

build essential - [http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential)

---

### Post by SierraKilo on 2007-02-21
> **HymnToLife said:**
> ```
sudo apt-get install build-essential
```

skneidl@skneidl-desktop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7930kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main linux-libc-dev 2.6.17-10.33
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libc6-dev 2.4-1ubuntu12
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main g++-4.1 4.1.1-13ubuntu5
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main g++ 4:4.1.1-6ubuntu3
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main build-essential 11.3
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
skneidl@skneidl-desktop:~$

---

### Post by george29 on 2007-02-21
well that's the problem you're not able to download the required packages...

do you have any other way of connecting to the net - ie a working computer with functional internet connection?

you could then download each of the required packages as .deb files and install them by hand.

---

### Post by Bachstelze on 2007-02-21
No need for that, build-essential is on the Ubuntu CD.

---

### Post by george29 on 2007-02-21
wasn't aware of that... 

i guess you need to stick the CD in and make sure it's included in your sources list.

then install build essential

I'm off to my girlfriends now... so wont' be able to confuse you anymore.. hopefully hymntolife will be around if you get stuck or somebody else.

hope you get it all sorted out.

george.

---

### Post by Bachstelze on 2007-02-21
In a nutshell :

```

sudo apt-cdrom add
*insert your CD and press Enter, then when apt is done scanning it*
sudo apt-get install build-essential
```

If it still tries to get it from the network, delete - or comment out - all the net entries in your sources.list.

---

