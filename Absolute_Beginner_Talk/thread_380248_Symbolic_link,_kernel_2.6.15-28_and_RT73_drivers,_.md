---
title: "Symbolic link, kernel 2.6.15-28 and RT73 drivers, how to?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by fuzZzball on 2007-03-09
Ello,
I just have a question (I'm quite new to linux), cause I'm bit confused..

I'm trying to install the RT73 driver for a wireless thingy .. Now the problem i have
is with te command *make*. 

It says "No target bla bla" : Stop

Now I've come this far that I need symbolic links, but I don't really get this .. :) .. 

I read on forums, in order to work with the *make* command correctly, I have to set a (soft) symbolic link with my kernel and some folder .. for example

sudo ln -s /usr/src/linux-2.6.15-28 /usr/src/linux

This is in order to find the Makefile? 

now first of all, i don't have the folder linux-2.6.15-28, only the folders linux-headers-2.6.15-28(-386), linux-headers-2.6.15-26(-386) and linux-source-2.6.15 .. 

Now i get it that you guys can't awnser on everything that's being asked here, especially when it's all nOOb stuff and so :D .. But is there a good tut or howto for explaining this? I've used the HOWTO from Wiki where the installation of the RT73 on Ubuntu is being explained .. but I get stuck where the *make all* command should be used .. above is the text, ***make sure you have all the right headers and sources for your kernel version*** .. but does not include a link to set this right .. quite funny :D ..

Well hope you can help .. I really would like to get into linux, so much cooler then windows .. muha! :D

Tnx!

---

### Post by Bachstelze on 2007-03-09
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Should give you everything you need. Do you have a readme in your driver tarball explaining what you need to do next ?

---

### Post by fuzZzball on 2007-03-09
Hi, tnx for helping :D

Already got build-essential's and headers .. tested it anyway's, here :

Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
linux-headers-2.6.15-28-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

um here is the link if you're interested .. [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

Well first i had to copy the Makefile.6 (for kernel 2.6) as a Makefile,
then i had to use the make all command to compile it .. but that doesn't work .. 

I've just dumped the package in some folder, i think it's usr/local/src .. from there i try to compile it .. dunno it this works, or perhaps this is the problem .. 

next it says :

sudo cp -v rt73.ko /lib/modules/`uname -r`/kernel/drivers/usb/net/
sudo mkdir -pv /etc/Wireless/RT73STA
sudo cp -v rt73.bin /etc/Wireless/RT73STA/
dos2unix rt73sta.dat
sudo cp -v rt73sta.dat /etc/Wireless/RT73STA/rt73sta.dat

But that's just driver specific .. I just can't get the *make* command get to work :( .. it says:

make -C /lib/modules/2.6.15-28-386/build SUBDIRS=/usr/local/src/RT73_Linux_STA_Drv1.0.3.6/Module modules
make: *** /lib/modules/2.6.15-28-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

:( .. do i have to symlink something? 

Tnx!

---

### Post by fuzZzball on 2007-03-09
Hmm k, I made a symbolic link between /usr/src/linux-headers-2.6.15-28 and /lib/modules/2.6.15-28-386/build   like this:

ln -s /usr/src/linux-headers-2.6.15-28 /lib/modules/2.6.15-28-386/build

(oh, i'm always logged as root)

now it does compile, magically .. only it stops at:

  LD [M]  /usr/local/src/RT73_Linux_STA_Drv1.0.3.6/Module/rt73.o
  Building modules, stage 2.
  MODPOST
/bin/sh: scripts/mod/modpost: No such file or directory
make[2]: *** [__modpost] Error 127
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28'
make: *** [all] Error 2

Well I found the modpost, it's in usr/src/linux-headers-2.6.15-28-386/scripts/mod/modpost (as an executable?)

hmm .. but hey, search continues .. it seems It can compile at least something :D ..

Yo

---

### Post by fuzZzball on 2007-03-09
Well .. 
I'm not a linux expert .. by far .. but in a few weeks I will be :D .. 

I think I solved the problem .. at least I think .. with the help from this post:
[http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00946.html](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00946.html)

below the posts you can read the followups .. 

Seems that I didn't had to make a symlink (symbolic link) with the linux-headers-2.8.15-28 folder but the linux-headers-2.8.15-28-386, in other words:

(if not logged as root) 
sudo ln -s /usr/src/linux-headers-2.6.15-28-386 /lib/modules/2.6.15-28-386/build

If someone would be kind enough to explain why this is? I mean it has the modpost executable, but it doesn't have all the folders and thingy's the linux-headers-2.8.15-28 has .. altought the linux-headers-2.8.15-28-386 has a bunch of symlinks, perhaps this is why it does work properly now ..

RT73 driver from ralink does moan a lot of warnings, but the howto file said I shouldn't pay any attention .. well .. I hope I don't have to :D

Well hope someone can still explain though .. would like to know .. or understand ..

tnx!

(p.s) great forum :D

---

