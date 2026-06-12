---
title: "Special device /dev/scd0 does not exist"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Mornedhel on 2006-10-23
I cannot seem to get my DVD drive to run properly.

The thing is, I can get it to work with a ./MAKEDEV scd0 then reboot (just CtrlAltBksp won't do the trick)

Then I can mount DVDs and CDs and read them all right, but a few boots later scd0 disappears again (that is, it appears in fstab but not in /dev .)

This is my fstab :
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /media/sda1     ext3    defaults        0       2
/dev/sda7       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda4       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


I have an Acer Aspire 5672WLMi.

---

### Post by whizbaby on 2006-10-23
Two questions
(1)Did you ever try
sudo mount -t iso9660 /dev/hda /media/cdrom0 
?
(2)Why not trying to make it work the normal way (udev, ivman, hal)?
Check if the ordinateur finds the device with **lshal** or **dmesg**.

---

### Post by Mornedhel on 2006-10-23
The ordinateur does find the device. A dmesg | grep DVD gives me the line :
[17179572.916000] Vendor: PIONEER Model: DVD-RW DVR-K06RS Rev: 1.01

Yes, I did try to mount it with 'mount', but it keeps telling me that 'Special device /dev/scd0 does not exist'. So does the Disk Mounter utility.

The drive works perfectly under WinXP (grmh.)

---

### Post by whizbaby on 2006-10-23
Why you insist on this scd? I don't believe this to be a normal linux device name for a cd (or is the device connected in a special way, usb, firewire or so?). Or do I misunderstand and you already tried (literally)
sudo mount -t iso9660 /dev/**hda** /media/cdrom0
?
Try this first (if you didn't do it) and post the error message of this (if any).
(what goes on in my head is:
you have an IDE DVD drive internally connected to the mainboard and SATA hard drives. So your DVD is the first (and only) IDE device and is most likely to be put in /dev/hda)

---

### Post by christhemonkey on 2006-10-23
Seeing as most all of your devices are SCSI, i am assuming that the DVD player is also scsi.
An should be mounted like this:
```
sudo mount -t iso9660 /dev/sdb /media/cdrom0
```


If that doesnt work, please tell us the output of ```
lsusb
```

---

### Post by Mornedhel on 2006-10-23
Well, I've been insisting on the scd since there is a line in my fstab that uses scd0 :
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
(so yes, it seems to be an actual normal linux device name for a cd, since the installer put it there).

Yes, I have already tried to mount it to /dev/hda (same output : special device /dev/hda does not exist). It is _not_ an external drive (it's the laptop's drive, actually). Same goes for sdb

lsusb gives :Bus 005 Device 002: ID 046d:0892 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

(but again, mine is not an external drive).

The drive currently works, but there is no telling whether it will still work next time I boot (disappeared 3-4 times already).

Looks very bizarre to me, if you ask.

---

### Post by whizbaby on 2006-10-23
> **Mornedhel said:**
> 
(so yes, it seems to be an actual normal linux device name for a cd, since the installer put it there).

That is really strange (see it the first time and have to do with a lot of computers, though few laptops only). How many hard drives do you have and what kind (IDE/SCSI) of DVD drive is it?

---

### Post by Mornedhel on 2006-10-24
I have one SCSI hard drive and this SCSI DVD drive.

---

### Post by whizbaby on 2006-10-25
So it is the second device on SCSI and should (according to what I know) hang  on /dev/sdb (like christhemonkey says).

---

### Post by Mornedhel on 2006-10-26
I know that, but the default was scd0.

/dev/sdb doesn't exist either (same message). Should I create it with MAKEDEV and edit the fstab so the cdrom points to sdb?

---

### Post by whizbaby on 2006-10-26
> **Mornedhel said:**
> I know that, but the default was scd0.

/dev/sdb doesn't exist either (same message). Should I create it with MAKEDEV and edit the fstab so the cdrom points to sdb?
I read a bit about scsi cdroms now (didn't use them at all) and indeed /dev/scd0 is the standard entry in /dev/ for the first scsi cdrom, so I don't think it will help much to create sdb. At present I cant contribute anything else...

---

### Post by Mornedhel on 2006-10-29
Additional information.

If I boot the laptop with a CD in the drive, everything works fine.

If I eject it and reboot, scd0 is again missing.

Huh.

---

### Post by whizbaby on 2006-10-30
Try following:
in /boot/grub/menu.lst find the lilne starting your system, will be similar to:

kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash

add **noapic** to the end of the line, save and restart. Any changes?

---

### Post by Mornedhel on 2006-11-20
Looks so. First time I tried my cds were mounted just fine.

What does noapic do, exactly?

---

### Post by whizbaby on 2006-11-20
APIC is a sort of new interrupt controller. Look here:

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

There are some problems with it thanx to the industry not agreeing on a proper standard or ignoring such standards...
If it works fine now your mainboard may have a non-standard apic, switching it off with noapic kernel option will then cause less problems than having it turned on.

---

### Post by Mornedhel on 2006-11-21
Doesn't work after all.

---

### Post by diddy47 on 2007-08-26
> **whizbaby said:**
> Two questions
(1)Did you ever try
sudo mount -t iso9660 /dev/hda /media/cdrom0 
?
(2)Why not trying to make it work the normal way (udev, ivman, hal)?
Check if the ordinateur finds the device with **lshal** or **dmesg**.

that sound like a good lead but I am new to ubuntu..what du you do with

sudo mount -t iso9660 /dev/hda /media/cdrom0

can u pliz give step wise instructions...that will help loads


thanx

---

### Post by whizbaby on 2007-08-27
Some 'wise' instructions:
- look at the date of the last post...
- if you want a manual for a command u get it by typing (e.g. for mount)
man mount
into a terminal.

But to answer your request:
sudo mount -t iso9660 /dev/hda /media/cdrom0

means

take the device /dev/hda (I suspected an ide cdrom) and hang it into the folder /media/cdrom0 using the filesystem type iso9660 (for cds) and superuser rights (sudo).

---

### Post by wrightee on 2008-01-22
I'm having the same problem.

As suggested in another post, I switched from Grub to Lilo and the drive worked perfectly.  Unfortunately Lilo gave me lots of other problems so I've gone back to Grub..

Perhaps this might help someone wiser than me find a solution?  Fingers crossed..

[edit]
Adding noaipc to grub didn't work, but **noaipc acpi=off** did.  Problem is it kills eth (mercifully wireless networking still works though!)

---

