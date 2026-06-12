---
title: "Feisty wipes out Xp"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by xintol on 2007-04-29
I installed Feisty yesterday and it wipes out window XP. The config and autoexec and other system setup files are have 0 byte. I end up re-install Xp and recover most of my files, but Feisty still in the hardisk drive, untouch. How do I make it a dual booth system. My set up are.


Celeron 2.0GhZ
384 MB RAM
40 GB internal hardisk drive C: Window xp installed
300GB external hardisk drive with USB  E: Feisty installed. I also use this as storage for xp.

Any help will be appreciate.

---

### Post by xintol on 2007-04-29
Help please. :)

---

### Post by fwojciec on 2007-04-29
Fesity didn't wipe out your XP, it probably just misconfigured Grub (application which manages booting into multiple systems) - it sometimes happens, especially if one of your hard drives is SCSI/SATA and the other IDE.  It would have been easy to fix had you not reinstalled XP - or rather, I would have been able to help you to fix it ;)  It should be still fairly easy to fix it though.

Right now you'll need to boot using Ubuntu CD, restore Grub in the MBR (master boot record) and configure it correctly so that it boots into both Windows and Ubuntu.  I've never done it myself from the CD, so I don't know exactly how to do it - but I'm sure someone with more experience will be able to help you or point you to the solution.

BTW, that's perfectly normal that Autoexec.bat, Config.sys and other files in the root directory of Windows installation have 0 bytes.  Ubuntu doesn't even touch your Windows partition, unless you tell it to - it just overwrites the MBR.

---

### Post by Ganda_Melga on 2007-04-29
Sorry. I installed Xubuntu in a different HD to avoid complications such as that. I wish I could help you, but I'm a real nerd on this linux thing.

Will somebody come foward and help this member?

---

### Post by hardyn on 2007-04-29
how did you install... exactly?

autoexec, and config are supposed to be empty.

install windows.
install fiesty, but pay attention to the partitioner... many blast though this without paying attention, and likely why you wiped out your windows partition.

you have a somwhat unconventional install... read around for installation to external hard disk... it is also possible that a computer of that vintage may not boot an external drive! (a bios update may help tht)

---

### Post by xintol on 2007-04-29
Thank you for the info. Here is my partition in my external hard drive.

I use Xp to format the entire hard drive to NTFS  (ext drive)

Then use Gparted to do the following.

10GB format in ext3.
500 MB for swap
10GB format in  FAT32

The rest of it are NTFS

then use the live CD to install Feisty. At the end of the installation, it ask if I want to boot it up with CD or hard drive. I remove the CD and let it re-boot, and get an error  17 if try to boot it in Linux, or error 21 if try to boot it in Xp. 

I can't ask of help if my pc is down, because I only have 1 pc.

---

### Post by hardyn on 2007-04-30
okey... 

so you have an internal drive that did not get touched in this operation?
then on the external for formatted 100% NTFS
then resized the partition as above?

that is a really backwards way of doing things.

if i were to do it:
i would format what you need as NTFS (not the whole drive, do your maths ahead of time)
leave the rest of the disk as raw.
boot the fiesty disk.
manually patition the remaining drive.
make sure that grub is installed to sda

many many people have installed to external drives, i have not, im sure some instructions have been posted.

---

