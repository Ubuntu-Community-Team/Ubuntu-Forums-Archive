---
title: "Want to resize a windows partition with gparted.."
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-10
My laptop came with windows taking up just about all of the hard drive space ntfs.. No free space left for a great linux os!! There is a fat32 3 gig section for my ibm system restore.. but...

I need to resize the windows partition to leave enough room for a linux distro such as ubuntu or redhat or whatever.. So i figure i can boot from the live cd and run gparted from ubuntu correct? Simply resize the windows ntfs one down by about 7 gigs to leave room for a linux os!? Is it really this simple with gparted? The thing is.. when i install a linux distro what will it ask me? Where i want to install linux? Would i say "over the free space that i just chopped off of my windows ntfs" ? Also, once i chop off that 7 gigs of windows disk, i want about 1.5 gigs of that chopped off part to be partitioned for sharring between both my linux os and my windows os... But the rest of the 7 gigs should be just for linux.. 


How should i do this.. What type of file system should that 1.5 gigs be formatted to.. What about the rest of that 7 gigs? What type of file system?

---

### Post by kwaanens on 2006-02-10
I've always used system rescue cd (sysresccd.org) for this. It uses qtparted.
I've done it about 4 times, and it seems to be quite safe.
Just make sure you defrag your windows first.

- Ketil

---

### Post by az on 2006-02-10
By default, the breezy installer will find and offer to shrink your windows partition for you.  All you have to do is pick that option and tell it how big to make the new linux partition.

Just install ubuntu.  It will do this for you.  Don't worry.

---

### Post by systemintheglitch on 2006-02-10
[QUOTE=azz]By default, the breezy installer will find and offer to shrink your windows partition for you.  All you have to do is pick that option and tell it how big to make the new linux partition.

Just install ubuntu.  It will do this for you.  Don't worry.[/QUOTE]

But what about about having a partition that windows and linux can share? ideally for media files.

---

### Post by aragorn2909 on 2006-02-11
> But what about about having a partition that windows and linux can share? ideally for media files.

*partition magic* convert ntfs to fat32.  I did it on my windows partition, no problem.  Not very elegant, but it seems alot easier to me to manage 3 partitions (fat32/ext3/swap) on a disk instead of 4 (ntfs/fat32/ext3/swap).

---

### Post by cotcot on 2006-02-11
You can make a FAT partition too during the install of ubuntu.
Changing the NTFS to FAT is simple supposing you have partition magic. Consider however that the maximum size per file in FAT32 is 4 GB. You do not have this limit in NTFS.
Alternatively to fat you could consider to access ext2 or ext3 from XP by installing the ext2 driver (freeware available on [http://www.fs-driver.org/)](http://www.fs-driver.org/)). Please read about it to learn about the pro and cons such as file permissions)

---

### Post by systemintheglitch on 2006-02-11
[QUOTE=cotcot]You can make a FAT partition too during the install of ubuntu.
Changing the NTFS to FAT is simple supposing you have partition magic. Consider however that the maximum size per file in FAT32 is 4 GB. You do not have this limit in NTFS.
Alternatively to fat you could consider to access ext2 or ext3 from XP by installing the ext2 driver (freeware available on [http://www.fs-driver.org/)](http://www.fs-driver.org/)). Please read about it to learn about the pro and cons such as file permissions)[/QUOTE]

A couple questions.. In addition to shrinkingmy windows partition and installing ubuntu over the top of that, i can also create an additional FAT32 partition during the installation that will automatically be allowed access between both windows and ubuntu? If so, then cool.. Will ubuntu walk me through a dual boot as well?

What type of file system should i format the ubuntu partition to? ext3? I dont really know what that is.. :confused:

---

### Post by theturner on 2006-02-11
ext3 is a good choice, since there are Windows drivers for it. If you don't care about access to you Linux partition from Windows, ReiserFS has marginal speed advantages over ext3.

---

### Post by systemintheglitch on 2006-02-11
So, can someone give me a summary of all the options  i will be asked while installing as far as partitioning go... This isnt something I want to go unprepared into..

---

### Post by systemintheglitch on 2006-02-12
Noone?

---

### Post by aysiu on 2006-02-12
[QUOTE=systemintheglitch]So, can someone give me a summary of all the options  i will be asked while installing as far as partitioning go... This isnt something I want to go unprepared into..[/QUOTE] See the fifth link of my signature.

---

### Post by wbastien on 2006-02-12
[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")
someone suggested that to me in another thread, very detailed and it includes pictures

---

### Post by kwaanens on 2006-02-12
The other posters may very well be right, but I've never seen an (easy) option to resize ntfs on Ubuntu Breezy install.

On the other hand, I'm dead sure you can make it very easy by using sysresccd.org, as I have done this several times.

> Boot with sysresccd, make your changes, reboot and install Ubuntu.

- Ketil

---

### Post by aysiu on 2006-02-12
[QUOTE=kwaanens]The other posters may very well be right, but I've never seen an (easy) option to resize ntfs on Ubuntu Breezy install.[/QUOTE] The aforementioned link by Herman walks you through step by step with screenshots.

If you prefer point-and-click, I highly recommend [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by patrick295767 on 2006-02-12
[QUOTE=systemintheglitch]Noone?[/QUOTE]
  
For resizing NTFS , I am always using powerquest partition magic (9 minimum)
  
U can get it from p2p, from trial version, from a friend ... thne u can install linux.
  
(If you use knoppix live cd, u can use : qtparted that is working very fine not for all purposes ...)

Greetz

---

### Post by systemintheglitch on 2006-02-18
[QUOTE=systemintheglitch]A couple questions.. In addition to shrinkingmy windows partition and installing ubuntu over the top of that, i can also create an additional FAT32 partition during the installation that will automatically be allowed access between both windows and ubuntu? If so, then cool.. Will ubuntu walk me through a dual boot as well?

What type of file system should i format the ubuntu partition to? ext3? I dont really know what that is.. :confused:[/QUOTE]

So noone really answered this.. but i think it is important.. 

I am about to install ubuntu RIGHT NOW :-k   and i need to know how (upon instalation) will i be able to create a section that both ubuntu and windows can share..  FAT32 that is.. THanks guys.

---

### Post by Herman on 2006-02-18
> Originally Posted by **systemintheglitch**
                 A couple questions.. In addition to shrinkingmy windows partition and installing ubuntu over the top of that, i can also create an additional FAT32 partition during the installation that will automatically be allowed access between both windows and ubuntu? If so, then cool.. Will ubuntu walk me through a dual boot as well? 1) [Yes]("http://users.bigpond.net.au/hermanzone/p3.htm").
 2) Ext3 or reiserfs.
>  I am about to install ubuntu RIGHT NOW :-k and i need to know how (upon instalation) will i be able to create a section that both ubuntu and windows can share.. FAT32 that is.. THanks guys. 1) [Yes]("http://users.bigpond.net.au/hermanzone/p3.htm").

---

### Post by suRoot on 2006-02-24
[QUOTE=theturner]ext3 is a good choice, since there are Windows drivers for it. If you don't care about access to you Linux partition from Windows, ReiserFS has marginal speed advantages over ext3.[/QUOTE]

Just for the record, you can use reiser under windows, too.

[http://p-nand-q.com/e/reiserfs.html](http://p-nand-q.com/e/reiserfs.html)

and here's a GUI 'explorer' for reiser under windows (requires rfstool - link above)

[http://yareg.akucom.de/](http://yareg.akucom.de/)

---

