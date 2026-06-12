---
title: "[SOLVED] Just installed, can't mount/find CD-ROM"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Geezle on 2008-02-10
The story leading to my problem.  My machine shat the bed and I had to install a new motherboard, processor and RAM.  Once I'd installed the new hardware Ubuntu wouldn't boot up right, so I just reinstalled 7.10 from the Live CD and used that to download the amd-64 version.  

When it came time to burn the new CD I noticed my cdrom wasn't there anymore.  I asked in #Ubuntu and got some help, but nothing seemed to work, and then after one miraculous reboot it worked and I was able to install.  Since I've installed again, I can't get Ubuntu to find my cdrom and I don't know what to do.

It's not in:
/dev/cdrom
/dev/cdrom0
/dev/hdb (this is what it was set to in /etc/fstab to begin with)

I get the error:
```

mount: special device /dev/cdrom does not exist
mount: special device /dev/cdrom0 does not exist
mount: special device /dev/hdb does not exist

```

I made sure that I have permission to access the drive.  Is there a simple way I can check to see where the device is?

---

### Post by rkd on 2008-02-11
This might be a hardware problem, since you essentially rebuilt the computer. If you haven't checked to be sure the data cable between the CD drive and the motherboard is plugged in all the way at both ends, look at that.  If you use a ribbon cable to connect the CD drive, sometimes old ribbon cables give up the ghost when you move them around a lot, like you probably had to do when rebuilding your computer, so if you have another ribbon cable to try, swap it in. If you can connect the CD drive to a different port on the motherboard, that might be worth trying. If it is IDE and on the second IDE controller, try making it the slave on the primary controller (be careful the jumpers on the drive are set correctly if you move it).

When the computer is starting up, check the screen when it is reported the devices it has found to see whether it reports the CD drive. If your computer has a floppy drive, sometimes it helps to put a non-bootable floppy into the drive so the device recognition report doesn't disappear so quickly that you can't read it.

If you think the device just is getting mounted in some odd location, just enter a mount command with no arguments and that will list everything that is mounted. Look for any sign of your CD drive.

If you think the device isn't getting mounted, you could look for it in the output from:```
ls -l /dev/*
```Actually, maybe the output from:```
ls -l /dev/hd* 
ls -l /dev/sd*
```would be better to look at, since there will be a lot less to look at. 

In my system, the cd drive has major device number 22 and minor device number 64 (those are the two number just before the date). The numbers might be different on your system. I found a list of them here: [http://www.lanana.org/docs/device-list/devices-2.6+.txt](http://www.lanana.org/docs/device-list/devices-2.6+.txt) but it seems that there isn't just one major device number for CD drives. Search that page and you will find lots of numbers. But maybe it will give you some clues about identifying the devices you see in the ls output.

---

### Post by jan quark on 2008-02-11
please post your current fstab file

```
cat /etc/fstab
```

---

### Post by Geezle on 2008-02-13
Sorry I took so long following up on this, but work's been crazy lately.

It turns out it was in fact a dodgy IDE cable.  It's amazing how easy it is to overlook the obvious!  Thanks guys!

---

