---
title: "Error with make modules command plz hlp"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by webtrog on 2006-01-12
Hiya!

I'm trying to do the 'make modules' step in the wiki walkthrough and im getting an error, well a bunch of them, ive installed g++ and gcc and make but im still stuck - thanks!

I pasted the instructions from the wiki below followed by the error that I am getting.

:::::::::::::::::::::::::::::::::::::::::::::::::: ::::::::::::::::::::::::::
[https://wiki.ubuntu.com/OrinocoMonitorKismet2005Hoary/](https://wiki.ubuntu.com/OrinocoMonitorKismet2005Hoary/)

install kismet

# wget [http://mirror.aarnet.edu.au/debian/p....R1-1_i386.deb](http://mirror.aarnet.edu.au/debian/p....R1-1_i386.deb)

# apt-get install ethereal-common
# apt-get install libglib1.2 libgmp3
# dpkg -i kismet_2005.04.R1-1_i386.deb

Install the kernel sources

# apt-get install linux-source-2.6.10

go to the /usr/src directory

# cd /usr/src

extract the kernel-source

# tar -xjf linux-source-2.6.10.tar.bz2

make a link to the kernel source

# ln -s /usr/src/linux-source-2.6.10 /usr/src/linux

cd to the source dir

# cd /usr/src/linux

get the monitor mode patch

Hoary

# wget [http://www.kismetwireless.net/code/o...dragorn-1.diff](http://www.kismetwireless.net/code/o...dragorn-1.diff)

Breezy

# wget [http://www.kismetwireless.net/code/o...dragorn-1.diff](http://www.kismetwireless.net/code/o...dragorn-1.diff)

patch the kernel-source replace x with version number

# patch -p1 --dry-run < ./orinoco-2.6.x-rfmon-dragorn-1.diff

and if no errors appear

# patch -p1 < ./orinoco-2.6.x-rfmon-dragorn-1.diff

Make a directory to backup the existing drivers.

# mkdir /orinoco

Move orinoco drivers to backup location $(uname -r) references running kernel

# mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/orinoco* /orinoco

# mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/hermes.ko /orinoco

copy the config file to the source directory

# cp /boot/config-$(uname -r) /usr/src/linux/.config

compile the modules

# make modules

# make modules_install

<Question: Is there another way? This will probably take two days on my p120 laptop. -Jason>

copy the new modules to the proper directory

# cp /usr/src/linux/drivers/net/wireless/orinoco*ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/

# cp /usr/src/linux/drivers/net/wireless/hermes.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/

edit /etc/kismet/kismet.conf for your card

use orinoco,eth1,orinocosource as the capture source

*********************************************
***** and im getting this error :
************************************************** *******

trog@ubuntupo:/usr/src/linux$ sudo make modules
Password:
CHK include/linux/version.h
HOSTCC scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/3.4.5/include/syslimits.h:7,
from /usr/lib/gcc/i486-linux-gnu/3.4.5/include/limits.h:11,
from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/limits.h:122:61: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function `usage':
scripts/basic/fixdep.c:129: warning: implicit declaration of function `fprintf'
scripts/basic/fixdep.c:129: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function `exit'
scripts/basic/fixdep.c: In function `print_cmdline':
scripts/basic/fixdep.c:135: warning: implicit declaration of function `printf'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:138: error: `NULL' undeclared here (not in a function)
scripts/basic/fixdep.c: In function `grow_config':
scripts/basic/fixdep.c:151: warning: implicit declaration of function `realloc'
scripts/basic/fixdep.c:151: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:153: warning: implicit declaration of function `perror'
scripts/basic/fixdep.c: In function `is_defined_config':
scripts/basic/fixdep.c:169: warning: implicit declaration of function `memcmp'
scripts/basic/fixdep.c: In function `define_config':
scripts/basic/fixdep.c:182: warning: implicit declaration of function `memcpy'
scripts/basic/fixdep.c: In function `use_config':
scripts/basic/fixdep.c:201: error: `PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:215: warning: implicit declaration of function `tolower'
scripts/basic/fixdep.c:201: warning: unused variable `s'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:220: error: parse error before "size_t"
scripts/basic/fixdep.c:221: warning: function declaration isn't a prototype
scripts/basic/fixdep.c: In function `parse_config_file':
scripts/basic/fixdep.c:222: error: `map' undeclared (first use in this function)scripts/basic/fixdep.c:222: error: `len' undeclared (first use in this function)scripts/basic/fixdep.c:228: warning: implicit declaration of function `ntohl'
scripts/basic/fixdep.c:239: warning: implicit declaration of function `isalnum'
scripts/basic/fixdep.c: In function `strrcmp':
scripts/basic/fixdep.c:252: warning: implicit declaration of function `strlen'
scripts/basic/fixdep.c: In function `do_config_file':
scripts/basic/fixdep.c:263: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:267: warning: implicit declaration of function `open'
scripts/basic/fixdep.c:267: error: `O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:269: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:273: warning: implicit declaration of function `fstat'
scripts/basic/fixdep.c:275: warning: implicit declaration of function `close'
scripts/basic/fixdep.c:278: warning: implicit declaration of function `mmap'
scripts/basic/fixdep.c:278: error: `PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:278: error: `MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:287: warning: implicit declaration of function `munmap'
scripts/basic/fixdep.c:263: warning: unused variable `st'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:292: error: parse error before "size_t"
scripts/basic/fixdep.c:293: warning: function declaration isn't a prototype
scripts/basic/fixdep.c: In function `parse_dep_file':
scripts/basic/fixdep.c:294: error: `map' undeclared (first use in this function)scripts/basic/fixdep.c:295: error: `len' undeclared (first use in this function)scripts/basic/fixdep.c:297: error: `PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:299: warning: implicit declaration of function `strchr'
scripts/basic/fixdep.c:301: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:297: warning: unused variable `s'
scripts/basic/fixdep.c: In function `print_deps':
scripts/basic/fixdep.c:334: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:338: error: `O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:340: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:350: error: `PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:350: error: `MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:350: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:334: warning: unused variable `st'
scripts/basic/fixdep.c: In function `traps':
scripts/basic/fixdep.c:369: error: `stderr' undeclared (first use in this function)
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make: *** [include/linux/autoconf.h] Error 2
trog@ubuntupo:/usr/src/linux$

---

### Post by davmac on 2006-01-12
I think you might be missingsome of the stuff you need to compile. Try "sudo apt-get install build-essential" and this should make sure you've got everything you need to allow you to compile.

If this doesn't work have a good read through of any INSTALL or README docs that come with the package. If it needs anything "fancy" it should tell you.

Hope this helps,

Dave Mac

---

### Post by webtrog on 2006-01-12
thx for the help
looks like i had everything except libc6-dev
Once i installed that everything seemed to compile, of course trying to understand the situation and to avoid similar complications, is there a way for me to see what kind of dependencies a certain program will require?

I suspect it's in a man page somewhere, which is where I'll begin to look, but I was just wondering if there is a trick to it.

thx again for the help

---

