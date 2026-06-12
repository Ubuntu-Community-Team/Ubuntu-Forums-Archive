---
title: "adding a USB TV pen drive unable to follow instructions"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by famleon on 2008-02-11
I founded this site [http://www.linuxtv.org/v4lwiki/index.php/Trident_TM6000](http://www.linuxtv.org/v4lwiki/index.php/Trident_TM6000)

and it explain how to add the drivers, but I can not use it. this are the instructions

Step 1: Clone a v4l-dvb tree in a directory of your choice

$hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Step 2: Apply the Makefile patch to the tree (which allows to build the driver later on)

$ cd v4l-dvb
$ wget [http://colabti.de/~feb/tm6000-makefile-dvb-tree.patch](http://colabti.de/~feb/tm6000-makefile-dvb-tree.patch)
$ patch -p1 < tm6000-makefile-dvb-tree.patch

Step 3: Download the driver and extract it

$ cd linux/drivers/media/video/
$ wget [http://colabti.de/tm6000/tm6000.tar.gz](http://colabti.de/tm6000/tm6000.tar.gz)
$ tar xvzf tm6000.tar.gz

Step 4: Compile everything

$ cd ../../../../
$ make

Step 5: Install everything

$ su -c "make install"

Step 6: Remove all the V4L/DVB modules that are currently loaded (or alternatively reboot the system) and load the driver module

$ su -c "make rmmod; /sbin/modprobe tm6000"

    * Firmware 

The firmware necessary for the device currently needs to be extracted from the driver files on the installation CD.

Step 1: Copy the file "tridvid.sys" from the CD into a directory of your choice

Step 2: Extract the firmware files

$dd if=tridvid.sys ibs=1 skip=145441 count=2632 of=tm6000-firmware1
$dd if=tridvid.sys ibs=1 skip=148089 count=3870 of=tm6000-firmware2

Step 3: Copy the firmware files to the firmware directory

$su -c "cp tm6000-firmware1 /lib/firmware; cp tm6000-firmware2 /lib/firmware"

But when i try the step 1 it give me back a bash error. can someone tell me what I am doing wrong? i just copy and paste **_hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)_** in the terminal anf that is when i get the error, is there something i am missing, same with all the other steps. I need help on this.  thanks

---

### Post by famleon on 2008-02-11
I also found more info in this site [http://tiagovaz.wordpress.com/2007/11/24/pixelview-play-tv-405-dvd-makerusb-tv-tuner/](http://tiagovaz.wordpress.com/2007/11/24/pixelview-play-tv-405-dvd-makerusb-tv-tuner/)
but I am still more confused.  thanks for any help on this

---

