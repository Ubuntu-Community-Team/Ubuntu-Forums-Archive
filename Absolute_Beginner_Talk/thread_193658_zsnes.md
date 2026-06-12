---
title: "zsnes"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by hauger on 2006-06-10
Hey everybody....

I'm looking to install zsnes & VICE (Versitile Commodore Emulator) on a fresh install of Kubuntu x86-64, but have had no luck.  I've edited /etc/apt/sources.list and un-"#" all the repositories as well as having added the multiverse, however, zsnes does not show up in a search.  Is it hiding in an obscure repository, or is it not available to x86-64 users?

I then downloaded the source, untarred it, sudo ./configure:

Output:

bison@bison-desktop:~/zsnes_1_42/src$ sudo ./configure
checking build system type... configure: error: cannot guess build type; you must specify one

I have no idea what that means.  A google search returned too many instances to be of any use.

Alright, stumped.  I then moxed on to installing VICE.  Luckily, it was listed in a repository.  I tried running it after install and was informed a kernal ROM was missing (very unusual for VICE as it ships with the commodore kernal ROM).  Fair enough, I thought, and uninstalled it.  Again, I downloaded and un archived the source, and again attempted to compile it.

Output:

bison@bison-desktop:~/vice-1.19$ emacs INSTALL
bison@bison-desktop:~/vice-1.19$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... x86_64-unknown-linux
checking host system type... x86_64-unknown-linux
no explicit checking for XFree86 fullscreen requested, disabling fullscreen...
using TextField widget.
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

What does that mean, "checking for C compiler default output... configure: error: C compiler cannot create executables"?  I have no idea how to fix this.  Again, googling led me to many forums which were beautifully employing the art of debating over various programming methodologies and test code to run and whatnot.  Really way above my head.

So, is this a GCC thing (I'm runnning I think GCC 4.0 with lib32gcc1 installed as well to give 32 bit support), or is this a result of running x86-64 and I need to seriously think about reverting back to a 32 bit platform.

Thanks for any help provided.
Rob.

---

### Post by richbarna on 2006-06-10
Hi,
Before compiling/installing you should :-
> sudo apt-get update
Then :-
> sudo apt-get install build-essential
For all the necessary tools

Also before running the install, in the terminal type :-
> su
CC=gcc-4.0
export CC
exit
CC=gcc-4.0
export CC

Also it may be an idea to look in Adept/Synaptic to see if you have installed the "Kernel Headers".

Good Luck !

---

### Post by camRW on 2006-06-10
I'm still quite new to Ubuntu as well, but did you install the build-essentials?

Edit: richbarna beat me to it.

---

### Post by echo $USER on 2006-06-10
I installed it through synaptic.  Runs great.  Using these sources:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

---

### Post by hauger on 2006-06-10
Thanks for the reply's guys,

rich, I did as you said (thanks for the insights), but the same errors were produced.  I'm wondering still if this could be an x86-64 thing, that maybe the packages are 32bit packages that won't compile on a 64 bit system.

Echo, I tried installing from the repositories (and all are un-"#"-ed), but again Zsnes doesn't show up.  I installed snes 9x, but found it buggy and it does not seem to support my gamepad.  My guess is again the 64bit vs. 32bit thing.

So, again, thanks for the replies....any additional help is appreciated.

---

### Post by antivert on 2006-07-06
You don't need to compile VICE. Install the one from the universe repositories, then get : 

[http://cvsup.de.openbsd.org/historic/comp/os/c64/VICE/vice-1.5-roms.tar.gz](http://cvsup.de.openbsd.org/historic/comp/os/c64/VICE/vice-1.5-roms.tar.gz)

Untar it, then cd to the data/ dir it makes, and sudo cp -R * /usr/lib/vice/ and you should be set. That just puts the files from the archive into the respective directories (C64, C128, etc) in /usr/lib/vice.

Sound works if you kill ESD. I'm running it now, no problems!

---

