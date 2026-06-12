---
title: "External hard disk"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-06-20
Hi

Having had a previous disaster when I lost a complete Linux installation, I'm determined to develop a sensible backup strategy. As a first step I've bought an external USB hard drive (a Western Digital 80GB My Book). The drive appears seamlessly on my desktop at start up, and I can drag and drop files into the drive without any problems. I'm eventually planning to use the tar command to save key directors, e.g. /home, but before I do that I'm wondering whether I need to do anything in the way of reformatting the drive. Gparted tells me that I've currently got a fat32 partition of 74.52 GB, with 7.84 MB unallocated.

My internal 80GB hard disk is split between Windows XP (using NTFS) and Linux (using reiserfs).

Do I need to create a reiserfs partition on my USB drive?
I've had a look at the drive using Gparted, but when I right click on the fat 32 partition, the only option I'm offered is unmount.

All advice much appreciated.

Roger D

---

### Post by kb3hkg on 2006-06-20
that would depend on what you want to do with it. If it is just going to be holding files fat32 is fine.

---

### Post by RogerD on 2006-06-20
I'm feeling my way here, because I'm not at all sure about the significance of these various file systems, but my intention is to use the hard disk to save key linux partitions, such as /home, so that I can recover from a hard disk crash or the inadvertant removal of my linux installation.

Will I be able to tar /home from a reiserfs partition to a fat32 partition, and then tar it back again? If you see what I mean.

Actually, I'm not sure while I need to use tar, I can't really see why a recursive copy wouldn't do just as well. Can you advise on that one please?

Regards

Roger D

---

### Post by caldaar on 2006-06-20
The different file systems are used for different concerns... Fat was suitable untill HD's expanded past its limitations which fat32 took its place, others are designed for speed, redundancy, security..... but for what you need, the main question is can you mount it, write to it and read from it... if the answers to those are yes then the file system is suitable.

The benifit of fat32 would be that you could see if from both Windows and Linux, backup files from both OS', and transfer files if needed.

---

### Post by kanem on 2006-06-20
Sometimes (but probably rarely) you might come across a file that has a name that fat32 doesn't like, and you won't be able to copy it to your external unless you rename the file. There's also something like a 4GB individual filesize limit on fat32.

Those are the only reason I can think of, but some experts here could probably tell you how it's just better to go with the better filesystem.

If it's no hassle, I'd go ahead and reformat that partition as reiserfs. You must have had some good reason to choose reiserfs in the first place right? I'd assume those benefits still hold weight on the external. Which filesystem is supposed to be more stable? I'd assume the one not invented by MS.

If you don't mind your backup drive being as large as your main drive, a recursive copy is fine I think, but you might want to look into the rsync command.

---

### Post by RogerD on 2006-06-20
Many thanks, this sounds like good advice. Yes I can mount it - from Computer in the Places menu - and I can certainly copy and read from it. Who knows, one day I might want to save Windows folders, so I think I'll stick with Fat32.

It looks as thougth System>Administration>Disks would give me the option of reformating to all manner of formats, but I don't feel like taking the risk.

---

### Post by kb3hkg on 2006-06-20
sounds like you are all set and everything should work just copied over or archived together in a tar file

---

### Post by eMcJagger on 2006-06-20
Hello,

I'm trying to do the same sort of thing, although I didn't see any auto-formatting when I connected my external drive.  Instead I followed the instructions here: [http://www.thelinuxpimp.com/main/mod...icle&sid=](http://www.thelinuxpimp.com/main/mod...icle&sid=) 561.

Everything looks in order, except that when I do a recursive copy of my home to the external drive, it appears to take up space on the root filesystem.  It has been suggested (if I understand correctly) that this is because I've mounted the external drive under / (/mnt/usbdrive, specifically).  Anyone know how to get around this?  I'm already at about 89% disk usage, so I can't afford to have another entire copy of my home on my root filesystem.

More details about this can be found on another thread I've already posted:  

[http://ubuntuforums.org/showthread.php?p=1161827#post1161827](http://ubuntuforums.org/showthread.php?p=1161827#post1161827)


Any help much appreciated.

---

### Post by eMcJagger on 2006-06-20
Oops, I'm not sure exactly what happened last time but it seems to be working now.  I'm guessing I didn't mount the external drive properly and was just copying to a regular directory on mnt.  Currently, "cp -r /home/jeremy/ usbdrive/jerBak" is processing and I can see the progress in the system monitor:  /dev/sda1 is getting slowly fuller while /dev/hda1 is sitting pretty at 89%.  All is well.


Sorry for my confusion.

---

