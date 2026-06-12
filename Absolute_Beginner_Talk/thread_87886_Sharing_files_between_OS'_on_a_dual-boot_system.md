---
title: "Sharing files between OS' on a dual-boot system"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Bonarges on 2005-11-09
Ok, I've tried the search function here and google and I can't quite find an answer to my question.  I probably just don't know how to properly phrase my question, so here it goes...

I am running an HP Pavilion ZV5434 dual-boot Ubuntu Breezy 5.10 (the latest) and XP Home.  What I want to do is to take my downloaded MP3s etc and play them in both windows and linux, without saving them in the partitions for each os (essentially having a copy of every one, one for xp and one for ub).  I've seen how to share over a server via samba, but not sharing files inside one computer.

This is probably a silly question that I should have found an answer for, but I've gotten this far on day 3 of my linux experience.

Also, dunno how to install ndiswrapper, but I'm working on it....  must get wireless going..

Bon

---

### Post by LHZ on 2005-11-09
There's a rather easy way, but it will require repartitioning your harddrive (and therefore, the reinstallation of Ubuntu and/or XP).

Both Linux and Windows can read/write to FAT32, so if you make a large FAT32 partition on your hardrive for data, both OSes will be able to use it. For instance, on a 80 GB harddisk, you could set up partitions as follows:

20 GB - Win XP (NTFS)
10 GB - Ubuntu (EXT3)
01 GB - Linux Swap (EXT3)
49 GB - Data (FAT32)

Of course, this will require repartitioning.

---

### Post by schdefan on 2005-11-09
Hi Bonarges!
Good choice to make your first steps with Linux!
Regarding your first questions to use your mp3 on both platforms you need to mount the partition in ubuntu where your songs are stored. To not run into any problems when you want to organize your archive it is good to format this partition (the song archive) with fat32 file system, cause as far as i know write operation on ntfs partitions from linux are still experimental and also the other way round write operations on ext2/3 or reiserfs from windows are not possible. Maybe i am wrong with that!

With fat32 you can read and write from linux without any problems.
How to mount partitions read this article from the starterguide: [ http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2515044]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2515044")
schdefan

---

### Post by Bonarges on 2005-11-09
Well, I was a little smart about this.  I have about 30 gb of free space from when I partitioned my hard drive. (When I first installed I screwed up and tried to switch my windows partition to fat32 so I could shrink it, of course deleting windows and all my files and such).  I repartitioned it like this:

15 GB XP
5 GB Linux
1.5 GB Swap
A small something for something else
30 some odd GB of free space and 
2 GB as a test drive

Now, when I used partition magic in XP it fails to load and says something like "partition letter can not be read" or something like that.  I've just gotten windows back up to spec how I like it and don't want to install again.

How do I get both platforms to "see" the little 2 gb part i have now?

CM

---

### Post by tomski on 2005-11-09
you may find this helpfull to copy the files from a reiserfs partition within windows

put this in program files
[http://p-nand-q.com/download/rfstool/rfstool-0.14.zip](http://p-nand-q.com/download/rfstool/rfstool-0.14.zip)

and put this in the same directory
[http://yareg.akucom.de/download.cgi/YAReG-0.9.9.zip](http://yareg.akucom.de/download.cgi/YAReG-0.9.9.zip)

if you have problems with those try this
[http://www.wolfsheep.com/map/rfsgui-2.0.zip](http://www.wolfsheep.com/map/rfsgui-2.0.zip)

i'll see if i can find similar tools for ex2 & ex3 partition and post the links
ok

---

### Post by Pablo_Escobar on 2005-11-09
1. You may have run out of primary partitions (that's a 4 max).
My partition setup :
Primary :
1. ext3 - Ubu 15GB
2. swap - 1,1 GB
Extended (rest of 120GB drive):
Logical volumes:
3 partitions of FAT32.

So that makes in my system 3 primary partitions (extended counts as 1). leaving one space left.

You need to think well how to setup Your partitions.

---

### Post by Bonarges on 2005-11-09
so does that mean I have too many partitions?  I thought I only had 4 and my free space.  The Windows, the Linux, the Swap and the Test drive, and then free space?  Can they not see each other or what?

CM "Mr. Confused"

---

### Post by Pablo_Escobar on 2005-11-09
I'd recommend :
Primary partitions :
15 GB XP
5 GB Linux
1.5 GB Swap

Extended partition (rest of the disk space):
Logical volumes:
30 some odd GB of free space and
2 GB as a test drive

---

