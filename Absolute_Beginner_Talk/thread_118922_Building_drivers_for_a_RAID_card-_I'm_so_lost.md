---
title: "Building drivers for a RAID card- I'm so lost"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by snoopaloop on 2006-01-18
Hello,

    I am trying to set up my new RAID array and I have a Highpoint 1640 RocketRAID card. The driver version is HPT374 and the directions that come with it say to build the drivers and whatnot by using make. It specifically says "# make KERNELDIR=/usr/src/linux-2.6.9-5". Unforunately I get a lot of error and from what I have looked up on the internet it mostly talks about loading a custom kernel, but I am not sure. If anyone has done this particular installation or knows what to do, any help would be appreciated.

Thanks!

---

### Post by snoopaloop on 2006-01-18
bump

---

### Post by student13 on 2006-01-19
Hi,

1.
[http://www.highpoint-tech.com/USA/bios_rr1640.htm](http://www.highpoint-tech.com/USA/bios_rr1640.htm)
[http://www.highpoint-tech.com/BIOS%20+%20Driver/rr1640/Linux/hpt374-opensource-v2.14-1101.tgz](http://www.highpoint-tech.com/BIOS%20+%20Driver/rr1640/Linux/hpt374-opensource-v2.14-1101.tgz)

2. 

$ mkdir hpt_374
$ cd hpt_374
$ gunzip hpt374-opensource-v2.14-1101.tgz
$ tar xf hpt374-opensource-v2.14-1101.tg

3. 

$ ls -l /usr/src/linux

/usr/src/linux -> linux-headers-2.6.15-12-686

4.

make KERNELDIR=/usr/src/linux

Result:

cp -f raid.o raid.obj
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-12-686'
  CC [M]  /home/student13/Download/hpt_374/hpt.o
  LD [M]  /home/student13/Download/hpt_374/hpt374.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/student13/Download/hpt_374/.raid.obj.cmd for /home/student13/Download/hpt_374/raid.obj
  CC      /home/student13/Download/hpt_374/hpt374.mod.o
  LD [M]  /home/student13/Download/hpt_374/hpt374.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-12-686'

and five new files in the source directory:

hpt.o
hpt374.ko <-- this is what you need
hpt374.mod.c
hpt374.mod.o
hpt374.o

5.

sudo modprobe hpt374.ko


I don't have this card so I can't tell anything how this will work for you.

---

### Post by borgenk on 2006-02-20
Didn't work for me. When i type: sudo modprobe hpt374.ko or sudo insmod ./hpt374.ko I get invalid sign -1 in module

I also get the same Warning: could not find */hpt_374/.raid.obj.cmd for */hpt_374/raid.obj

Don't know if that does mean anything?

I've tried serveral kernel versions (2.6.9, 2.6.12, 2.6.13), makes no difference.

Then i tried to compile the driver with my laptop with gentoo. No warning message and when i typed insmod ./hpt374.ko  i get "No such device" obviously because i don't have it installed on my laptop ;) but it seems like the driver is working?

Can't figure out how to get it work on my server though..

---

### Post by borgenk on 2006-02-20
I actually managed to get it to work with gentoo on my server.. hm

---

