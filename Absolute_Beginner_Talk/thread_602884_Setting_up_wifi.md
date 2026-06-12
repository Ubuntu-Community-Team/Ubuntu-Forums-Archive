---
title: "Setting up wifi"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by COLiNx86 on 2007-11-04
I've followed Tons of tutorials on setting my wifi up but nothing seems to work. and when i run ```
sudo apt-get install bcm43xx-fwcutter
```  it gets to the part about getting wl_apsta.o from a website but the files not on that website anymore so it just gets an error. I also have the file on my desktop but how do i make it install using the file on my desktop?

sorry if that was a little hard to follow. oh and this is my first time installing ubuntu, i've tryed numerous times but failed everytime.

---

### Post by arkara on 2007-11-04
ok my friend if this is a ***_file.deb_*** then this is a package file
in order to install it you just double click it and you will easily install it
now if it is on tar you should decompress it by right click and extract here
then opoen a terminal and type

```
cd /path/to/file/directory
```

and then
```
./configure
```
then
```
make
```
then
```
sudo make install
```

and so with three commands you will get the job done. hope i hepled

---

### Post by gaston9x19 on 2007-11-04
Ok, I'm just trying to make my wireless adapter work, brand new to Linux, and I'm getting very frustrated. I know this isn't the same exact thing as this post, but if I can't even get a connection to the internet at all through Wifi, I'm going to just reformat this computer back to Windows (an OS that WORKS when you plug something new in) and give up on the stupid little upstart known as Linux.

I've tried following the guide on installing the Netger wg111v2 dongle shown here, [http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299), but several steps lock up my computer, and if I just skip past those and keep trying to add the MAC address, now my computer won't finish booting up, it gets stuck at the *Starting hotplug system, part of the boot sequence. I'm running Ubuntu 5.04 on a 32-bit Pentium III 886 mhz, are these instructions only for people lucky enough to be able to install newer Ubuntu versions???? I can't get mine to boot from CD on the downloaded 7.10 files from the internet.

Can someone please help me figure out how to just make the computer work? Isn't there a setup.exe you can run on Linux to install everything and make it nice and easy to get online when you don't have an ethernet card (Ubuntu couldn't figure out how to use one of those when I put it in either.... or my ATI Radeon 7000 video card, for that matter!).

Any ideas?

---

### Post by ub9876 on 2007-11-04
Arkara    show a picture of the multiple lines,, in one box ....

---

### Post by COLiNx86 on 2007-11-04
> **arkara said:**
> ok my friend if this is a ***_file.deb_*** then this is a package file
in order to install it you just double click it and you will easily install it
now if it is on tar you should decompress it by right click and extract here
then opoen a terminal and type

```
cd /path/to/file/directory
```and then
```
./configure
```then
```
make
```then
```
sudo make install
```and so with three commands you will get the job done. hope i hepled
thanks that helped me install a program i was looking at but it didn't really help with my wireless driver

---

### Post by COLiNx86 on 2007-11-04
Sorry for bumping this i just really need some help, right now i'm trying the ndiswrapper way and having ZERO luck.

---

### Post by mdpalow on 2007-11-04
did you install 7.10 with the cable (CAT5) plugged into your laptop? Install uses your cable connection to get drivers. Ubuntu 7.10 works with Broadcom, so you shouldn't have too many problems with this as long as you had your cable connected during install.

---

