---
title: "Can't boot up Windows disk"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Kakiro on 2006-05-21
Hi! I've just started using Ubuntu, and I think that it's great! But some problems during the installation caused me to delete my Windows partition, which I still want for gaming. Now, when I try booting up the Windows installation disk, it just goes to GRUB and boots up Ubuntu! I've tried searching up the answer and booting up from a specific disk drive, but I still can't get it to work. Can anyone please help me? Thanks!

---

### Post by yager on 2006-05-21
Check your BIOS for the boot order of your hardware.  Set your CD drives to boot before any hard drives.  This should resolve your boot order problem.

---

### Post by Kakiro on 2006-05-21
I just tryed what you suggested, but for some reason, the setup still won't boot! I played around with the settings a bit, but it either boots up GRUB, or gives me a message telling me to insert something into the specified drive, even though there's already a disk in it.

---

### Post by confused57 on 2006-05-22
If you haven't changed anything in bios since installing Ubuntu, evidently your bios is set to boot from CD rom or you wouldn't have been able boot from the Ubuntu install CD.

It might be a problem with your windows install CD,  is it scratched or dirty?  You could try cleaning it, carefully of course, you could google for the correct way to clean.

You're sure windows is wiped out?  What does Ubuntu show for your disk partition table?  If you set up a dualboot, Grub would have more than likely been installed to the mbr in the windows partition...unless you selected install Grub to Ubuntu, then there could be a problem...

---

### Post by Kakiro on 2006-05-22
Yeah, I'm pretty sure that the Windows partition is wiped since I've rebooted (Ubuntu) a few times, and all there is are the Ubuntu partitions. There doesn't look like anything is wrong with my Windows disk either. Isn't it possible to get GRUB to boot the disk though?

---

### Post by confused57 on 2006-05-22
You could try booting up the Live CD(or the install CD, just don't install) just to make sure your computer is booting from the CD Drive.

---

### Post by Sef on 2006-05-22
To check if your Windows partition was wiped or not, open the terminal (Applications >Accessories > Terminal.)

Then type

sudo fdisk -l

That will list what partitions you have.  If you have one for NTFS, then you Windows would on the hard drive.

---

### Post by Kakiro on 2006-05-22
> Originally posted by **Sef**
To check if your Windows partition was wiped or not, open the terminal (Applications >Accessories > Terminal.)

Then type

sudo fdisk -l

That will list what partitions you have. If you have one for NTFS, then you Windows would on the hard drive.
I did the fdisk command in the terminal and got this:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

Then, I tried entering the fdisk commands it listed, but it just said unable to open.

---

### Post by yager on 2006-05-23
Getting back to your original problem, you checked the boot order of your hardware in the BIOS and does boot the CD first correct?  You were able to start Ubuntu in Live mode from the Ubuntu CD.

Since the boot order is correct, then you need to confirm that the Windows CD is a viable CD.  If you have access to another computer(s).  Put the CD in the other computer and try to boot it from the CD.  Did you have any luck?  If you had no luck with the other computers, you appear to have a dead CD.  You need to contact your hardware manufacturer to see if they can help you out.  I would not hold out much hope, but you never know.

One crazy thought, is it possible that the Windows CD is actually a DVD and therefore needs to be booted from a DVD drive?  I had an aggravating experience a few years back because I put a DVD in my CD drive.  Of course the CD drive had no idea what it was looking at, so it would not read.

---

### Post by costoa on 2006-05-24
[QUOTE=Kakiro]I did the fdisk command in the terminal and got this:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

Then, I tried entering the fdisk commands it listed, but it just said unable to open.[/QUOTE]

BTW, that's a lowercase "L". From my laptop (remember, you're win partition might be on another device):

```
costoa@hermes:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1825    14659281    c  W95 FAT32 (LBA)
/dev/hda2            1826        4742    23430802+  83  Linux
/dev/hda3            4743        4870     1028160    5  Extended
/dev/hda5            4743        4870     1028128+  82  Linux swap / Solaris
```

At that point you could try to mount the disk by
```

sudo mkdir /media/tmpmnt
sudo mount -r -t vfat /dev/hda1 /media/tmpmnt
nautilus /media/tmpmnt &

```
and unmount it by closing the Nautilus window and:
```

sudo umount /dev/hda1

```

---

### Post by Mustard on 2006-05-24
Could it be that the windows CD was never bootable, and that a boot floppy is needed to start the CD?

---

### Post by confused57 on 2006-05-24
[QUOTE=Mustard]Could it be that the windows CD was never bootable, and that a boot floppy is needed to start the CD?[/QUOTE]

Good point, I know win98 install CD requires booting up with a boot floppy first, if I remember correctly.

---

### Post by Mustard on 2006-05-24
[QUOTE=confused57]Good point, I know win98 install CD requires booting up with a boot floppy first, if I remember correctly.[/QUOTE]
Yes, that's my recollection of the win98 CD too.

---

