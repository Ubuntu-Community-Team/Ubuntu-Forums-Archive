---
title: "A Question about NTFS hard drives and Linux/Ubuntu"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by thadiusdean on 2007-01-21
Now, I know nothing about Linux or Ubuntu so try not to assume I know of anything you mention. I know I have a NTFS hdd in my computer, and I know there is another type (FAT32 perhaps?) my question is will I need a FAT32 or w/e it's called hdd to have Ubuntu on it, and if so, how am I able to make sure my hdd is that format? I've looked on Newegg and they don't mention NTFS or FAT32 in the specifications. I've also looked around on these forums and see that there is some type of problem with NTFS hard drives and Linux/Ubuntu.

Is there some way I can change or make a hard drive either/or?

---

### Post by jpeddicord on 2007-01-21
Hard drives do not come in a specific format. NTFS and FAT32 are Microsoft formats for Windows only. Linux uses Ext3 and ReiserFS (your choice on which) as a format. When you partition your drive to run multiple OSes, you can have more than one filesystem on the drive.

---

### Post by freebeer on 2007-01-21
To suplement with a bit more information: If you're installing Ubuntu from the Live CD, part of the process runs a partitioning program that will prompt you for the partitions you want to change/create and in which format.

---

### Post by thadiusdean on 2007-01-21
Thanks guys, that cleared up the subject rather nicely.

I've tried the early prototype windows installer thing on that Fiesty Fawn forum, and I keep getting the "Error 17: File not found" message. The wiki page says to try defragging the hdd, which I have done and it still doesn't work. I read about trying to copy the kernel, delete the old one, and have the copied one replace it in order to try to have the hdd assign the file a new (hopefully defragmented) location. I've considered trying this, but I don't know what a kernel is, let alone which file it is. I assume it's somewhere in the C:\ubuntu folder?

And if that isn't worth trying, what may be the problem? Sorry, I realize that this is somewhat off topic, but the whole reason I was asking about this was because I thought that my hard drive may have been completely incompatable, and therefore the root of the problem.

---

### Post by frotzed on 2007-01-21
Having just recently (in the last month) switched from full time Windoze to full time Ubuntu I've found it easiest to install Edgy from a CD.  Seriously, it's very easy.  If you've already defragged your hard drive then you're good to go.  Just download the image, burn the image to a disk, put the disk in your drive and reboot.  It's pretty much fool proof.  At this point in your "ubuntu career" you honestly don't have to worry about hdd formatting or kernels.  Just install and go baby!

---

### Post by punx45 on 2007-01-21
Still, be careful if you are installing on a drive that you plan keeping windows on.   always back up important files.


any hard drive can be formatted with any format, so dont worry about the compatability of your drives.   
try [reading this guide]("http://www.psychocats.net/ubuntu/partitioning") on planning partitions too if you plan on keeping windows.   the rest of the guides on that site are really good too for people that are just starting out.

---

### Post by freebeer on 2007-01-21
Well, first of all Feisty Fawn, I believe, is experimental.  Here Be Dragons!  I don't think an inexperienced user should be messing with that - it'll probably be messing with you back!  :D
I know I wouldn't be playing around with it.

Are you planning on doing an install of Ubuntu without keeping Windows on it?  That's certainly the easiest way.  If you don't have it, I'd recommend the Live CD of 6.06 (Dapper) or 6.10 (Edgy).  I use 6.06 and I've been able to successfully install in on a couple of machines without issue.

---

### Post by frotzed on 2007-01-21
> **punx45 said:**
> Still, be careful if you are installing on a drive that you plan keeping windows on.   always back up important files.

Good advice.  I know of at least one person whose hard disk was oddly formatted and when he went to dual boot ubuntu and windows found out that neither worked.  It was a very odd issue, but stuff like that does happen.  I guess I just lucked out ;).

---

### Post by deadimp on 2007-01-22
> **punx45 said:**
> Still, be careful if you are installing on a drive that you plan keeping windows on.   always back up important files.
Second on this. I say this after screwing over my partition table - I got lucky in that I posted my prior information on this site, and worked off of that to restore my partitions, somewhat (still need to reinstall Ubuntu, since I've corrupted it). It was an extremely painful experience (it was only a day ago, too).

---

### Post by thadiusdean on 2007-01-22
Thanks so much guys! Ya'll are awesome. :)

---

