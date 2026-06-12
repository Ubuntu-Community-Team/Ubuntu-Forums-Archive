---
title: "Partitioning/Resizing NTFS"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-10-19
So i hear that linux isn't really able to do much with ntfs filesystems.  When trying to resize my primary partion for use in ubuntu for a dual boot setup, the program will constantly loop back to the partion [!!!] page.  This leaves me to believe i should fist partition the drive in windows before trying the ubuntu disc.  I don't have a windows disc, just recovery cd's, and they won't let me do anything.  I also can't seem to find a free partioning software out there.  Heard good things about partion magic, but i want free.  Any suggestions on what to do or how to go about doing it?

---

### Post by Kapre on 2005-10-19
[QUOTE=Griff]So i hear that linux isn't really able to do much with ntfs filesystems.  When trying to resize my primary partion for use in ubuntu for a dual boot setup, the program will constantly loop back to the partion [!!!] page.  This leaves me to believe i should fist partition the drive in windows before trying the ubuntu disc.  I don't have a windows disc, just recovery cd's, and they won't let me do anything.  I also can't seem to find a free partioning software out there.  Heard good things about partion magic, but i want free.  Any suggestions on what to do or how to go about doing it?[/QUOTE]

Griff - I would suggest to use a Live CD (Knoppix or Mepis) and then use the QTparted program that is included on the livecd. This is what I've used to partition my NTFS (XPPro). But please make sure to back up all your important stuff and run Defrag on your M$ system 3 times before running the live cd and doing the resize.

K

---

### Post by patrick295767 on 2005-10-19
[QUOTE=Kapre]Griff - I would suggest to use a Live CD (Knoppix or Mepis) and then use the QTparted program that is included on the livecd. This is what I've used to partition my NTFS (XPPro). But please make sure to back up all your important stuff and run Defrag on your M$ system 3 times before running the live cd and doing the resize.

K[/QUOTE]
small question by the way, is qtparted able to resize ext3 of linux ??
I tried last time with knoppix but It wasnt able to do so...

Thank you 

Pat'

---

### Post by Herman on 2005-10-20
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
Well it seems to me that different things work okay for some computers and not for others. This link above shows the Ubuntu partitioner being used to resize an NTFS partition.

My wife and I have twin computers that are both the same brand and model but made a couple of months apart. We both have dual boot Windows XP on FAT32 with Ubuntu. 
For some reason we have the same trouble you described when trying to make more partitions in hers, Griff, (looping back to the partition table panel). I tried using Qtparted from Knoppix and that wouldn't work for hers either. I haven't spent the time to investigate why not yet. But my computer is pretty near identical to hers and I can partition it how I like, (with any partitioner) I wonder if there's some BIOS setting or some Windows security setting in hers that's been set differently that we have forgotten about. Obviously it wasn't like that when we put Ubuntu in hers to make it dual boot. It must have been set like that later. Also I agree with Kapre, defragging needs to be repeated a number of times in some instances. A stray block of Windows data can 'chuck' the partitioner back.

Here's a link showing the use of Qtparted:
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)
(Notice how that fellow says you can't use the Ubuntu installer to resize NTFS.)

The Ubuntu instructions say to try the Ubuntu installer first and if it doesn't work try Qtparted:
[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

A good suggestion no matter which partitioner you decide to try out, for NTFS it's good to make a small FAT32  partition at the same time as you are partitioning anyway. You might want to use it later for a common partition that both operating systems can 'read' and 'write' to, for transferring files backwards and forwards between Ubuntu and Windows.

---

### Post by poofyhairguy on 2005-10-20
[QUOTE=Griff]So i hear that linux isn't really able to do much with ntfs filesystems.  When trying to resize my primary partion for use in ubuntu for a dual boot setup, the program will constantly loop back to the partion [!!!] page.  This leaves me to believe i should fist partition the drive in windows before trying the ubuntu disc.  I don't have a windows disc, just recovery cd's, and they won't let me do anything.  I also can't seem to find a free partioning software out there.  Heard good things about partion magic, but i want free.  Any suggestions on what to do or how to go about doing it?[/QUOTE]


Defrag your hard drive, then follow this guide:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Griff on 2005-10-25
Awesome guys.  Should have no problem now.  Been out of town a few days but i'll get on this later tonight after i get some much overdue work done.

---

