---
title: "another n00b having trouble with usb drives"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by sniffass on 2006-02-03
OK, under Unbuntu I plug in my USB flash drive and I get a pretty little icon appear on my desktop. Very neat. I prever KDE environment and as such I reinstalled with Kubuntu, it looks fab. I have an external Lacie harddrive and a USB flash drive. When I connect either of them Kubuntu tries to give me a window displaying their contents but it has an error that it cannot access them. I didn't have these devices connected during installation - but should I?

I opened up my fstab file to have a tinker but didn't know what to write apart from /dev/sda1. I had a similar problem in SuSe 10 and I could access the drive if I logged in as root, but in Kubuntu I don't even know how to do this. Also the external harddrive is NTFS formatted and the flash drive FAT32, but to read/write to them I shouldn;t need to be root. I tried Mandriva, SuSe9.3, DSL and something else, they all seem to be able to handle a USB device correctly. What is it that I must do in Kubuntu (by the way ubuntu seemed ok).

Regards,
Gabe

---

### Post by ace2005 on 2006-02-03
Open your /etc/fstab and add you will need to add something like this to the end:

> /dev/sda1	/mnt/disk	vfat	rw,user,noauto	0       0


vfat: replace vfat with the filesystem that the device uses

rw:this makes the drive writable, things like CD drives will not have this option, use only on the fat32 drive, can't write to NTFS

user: you won't have to be root to mount and unmount it

noauto:it won't be auto mounted

/mnt/disk: where it will be mounted, you will have to create an empty directory for this, as root do 

> mkdir /mnt/disk

For easy access to mounting it, run kwikdisk, which will put an icon in the system try which will let you mount and unmount it

---

### Post by sniffass on 2006-02-03
OK thank you for your fast reply, I will try this in just a minute. I'm just wondering though can't Ubuntu handle a USB storage device like the other linux versions or even w**dows? You plug it in and pull it out, no prob. Also why has it got this attitude with kubuntu no ubuntu, that really gets me.

Gabe

---

### Post by bscbrit on 2006-02-03
Well, Ubuntu _can_ handle USB drives just as easily as any other operating system.  On my computer and many others it just works.  I'm not sure why there is a problem under Kubuntu on your computer.  I've use Kubuntu in the past and not had problems but perhaps there is a problem with a recent update.

---

### Post by sniffass on 2006-02-03
Well after messing around with my fstab file i got the flash drive working but the usb hard drive gives the following error when i connect it:

Could not mount device etc
wrong fs type, bad option, bad superblock, missing code page etc.

my fstab is:
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda5       /windows        ntfs    r,user,defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/RETARDS       vfat rw,user,noauto     0       0
/dev/sdb1   /media/LACIE    ntfs   r,user,noauto     0       0

LACIE is my usb hard drive, i want to make it read only as it is ntfs. 
cheers.

---

### Post by bscbrit on 2006-02-03
> 
/dev/sdb1 /media/LACIE ntfs r,user,noauto 0 0


There's the problem - it should read ro,user,noauto - you have missed the 'o' out.  And don't forget that ntfs IS read-only unless you plan on trashing all the data on that drive.

---

