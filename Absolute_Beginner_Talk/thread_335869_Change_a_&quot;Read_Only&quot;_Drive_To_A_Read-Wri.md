---
title: "Change a &quot;Read Only&quot; Drive To A Read-Writeable Drive"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-10
Hey All!!

I was doing some cleaning out of my office and found a brand new Simple Tech USB 120 gig usb hard drive that I decided to plug in to my Ubuntu PC. I plugged in the USB cable, hooked up the power cables, and logged in. Not to my surprise, next to my Windows partition hda1, the new drive was mounted automatically as "usbdrive". I can read and access the files, but cannot delete, add new ones.... I need to have read/write permission like I do with my NTFS formatted Windows partition.... I downloaded Gparted, but I cannot format it this way.....

Any ideas?

Fingerz

---

### Post by taurus on 2007-01-10
You need to unmount it first before you can format it.

Applications -> Accessories -> Terminal
```
sudo umount /media/usbdrive
```

---

### Post by Fingerz91 on 2007-01-10
> **Fingerz91 said:**
> Hey All!!

I was doing some cleaning out of my office and found a brand new Simple Tech USB 120 gig usb hard drive that I decided to plug in to my Ubuntu PC. I plugged in the USB cable, hooked up the power cables, and logged in. Not to my surprise, next to my Windows partition hda1, the new drive was mounted automatically as "usbdrive". I can read and access the files, but cannot delete, add new ones.... I need to have read/write permission like I do with my NTFS formatted Windows partition.... I downloaded Gparted, but I cannot format it this way.....

Any ideas?

Fingerz

What I meant to say was I need to format the USB drive via FAT32 NOT NTFS!!!

What should I do after I unmount it? Cant I just right click on the drive an "eject" it and it does the same thing?

---

### Post by taurus on 2007-01-10
Don't eject it.  Just unmount it and fire up gparted from Ubuntu and format it to fat32.

---

### Post by Fingerz91 on 2007-01-11
I tried using the command you supplied, and the path is correct, but I cannot unmount the drive... I get a invalid location error...

---

### Post by steve.horsley on 2007-01-11
The command df -h should tell you what device and partition the thing is. Frinstance, it may well appear as /dev/sda1. In which case, **sudo umount /dev/sda1** should do the trick. And then you can format it to FAT with the command **sudo mkfs.vfat -F 32 /dev/sda1**. Leave it a few seconds before removing it after the format.

---

### Post by Fingerz91 on 2007-01-11
> **steve.horsley said:**
> The command df -h should tell you what device and partition the thing is. Frinstance, it may well appear as /dev/sda1. In which case, **sudo umount /dev/sda1** should do the trick. And then you can format it to FAT with the command **sudo mkfs.vfat -F 32 /dev/sda1**. Leave it a few seconds before removing it after the format.

Im not sure what you mean.

The device is /media/usbdisk

i tried sudo umount media/usbdisk and I get a directory doesnt exist error, when I know it does...

---

### Post by 3rr0r on 2007-01-11
maybe cd to the home directory?  (this is just my guess)

---

### Post by taurus on 2007-01-11
> **Fingerz91 said:**
> Im not sure what you mean.

The device is /media/usbdisk

i tried sudo umount media/usbdisk and I get a directory doesnt exist error, when I know it does...

It should be

```
cd 
sudo umount /media/usbdisk
```
And if there is an error message, please include it here.

---

### Post by steve.horsley on 2007-01-11
/media/usbdisk is the mount point, not the device. You will not be able to format the mount point.

Please can you plug the drive in, then while you can see it, open a terminal and use these two commands, and post the output back here:
[B]sudo fdisk -l
mount[/B]

---

### Post by Fingerz91 on 2007-01-11
here is the output for sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    c  W95 FAT32 (LBA)
/dev/hda2            7650       14593    55777680    f  W95 Ext'd (LBA)
/dev/hda5            7650        7682      265041   82  Linux swap / Solaris
/dev/hda6            7683       14593    55512576   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Here is the output for mount:

tommy@tomroom:~$ mount
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/usbdisk type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)

Hope this helps!

I understand now that the mount point is /media/usbdisk....

whatd ya know... you learn something new every day

---

### Post by Albi on 2007-01-11
looks like its /dev/sdb1

so then the commands would be

sudo umount /dev/sdb1
mkfs.vfat -F 32 /dev/sdb1

---

### Post by Fingerz91 on 2007-01-11
Actually I did it without the terminal at all :)

Gotta love Ubuntu and GNOME on this one :cool: 

I open Gparted, chose my USB device from the list, and right clicked.

Secondly, I chose unmount from the list

Formatted with FAT32

BINGO!!!!

Ubuntu has read-write access!

---

### Post by ctt1wbw on 2007-01-20
I just got an 80 gig usb drive myself and it came formatted NTFS.  I tried numerous ways in Windows to get it back to FAT32 and couldn't.  So bingo comes Ubuntu and gparted and it's done.  Man, I love linux.

---

### Post by jdzitro on 2007-02-23
.....So there's no way to change to a writeable disk without formatting?

Like, it doesn't have to do with permissions?

---

