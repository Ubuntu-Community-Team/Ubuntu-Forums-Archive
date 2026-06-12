---
title: "Fresh Install Question (Dual Boot Windows/Ubuntu)"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by yacobito on 2006-11-30
Hello All,

   This will be my first run around with Ubuntu and Linux in general.  I have an desktop that I am wiping clean and what to start fresh with a dual boot system of windows 2000 and ubuntu.  I was wondering if which order I should install/partition the hard drive (60GB).

1.  I reformat the whole thing.  Create a partition (60GB) for windows 2000.  Install windows.  Then use the ubuntu disk to create new partitions form the 60GB and install ubuntu.


OR

2.  I reformat the whole thing.  Create separate partitions (2-3).  Install windows on one of them.  Install ubuntu on the others.

Any suggestions would be greatly appreciated.  I guess I am just looking for the order that will be the easiest for a newbie.

---

### Post by Bachstelze on 2006-11-30
Hi and welcome to Ubuntu :)

Here's what I usually do :

0) Delete all existing partitions with GParted.

1) Install Windows but *not* on the entire drive. The WinXP installer lets you create a partition with desired size before installing Windows on it, I think you can do that doo in 2000.

2) Install Ubuntu on the rest of the drive.

3) Enjoy :)

---

### Post by deadgobby on 2006-11-30
Here is a little vid to watch on dual booting
[http://video.google.com/videoplay?docid=-610449081131189](http://video.google.com/videoplay?docid=-610449081131189)
[http://www.linux.com/article.pl?sid=06/07/20/1654251](http://www.linux.com/article.pl?sid=06/07/20/1654251)
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=m9n&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=dual+booting+ubuntu+video&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=m9n&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=dual+booting+ubuntu+video&spell=1)

---

### Post by nandasunu on 2006-11-30
If you will be using both ubuntu and windows regularly you may find it useful to create a partition for storing your files and format it to fat32 so both OS's can read & write to it.

On my 60gb hard drive I first made a 12 gb windows partion, then 8 gb linux partion, 1gb swap partion, then a 39gb fat32 partion. Installed windows on the first one, then installed linux on the second, selecting the partions to use in gparted during the installation. The shared partion & windows partion should auto mount when booting ubuntu, the shared one will show up in "My Computer" on windows also.

---

### Post by nofrak on 2006-11-30
> **nandasunu said:**
> If you will be using both ubuntu and windows regularly you may find it useful to create a partition for storing your files and format it to fat32 so both OS's can read & write to it.

On my 60gb hard drive I first made a 12 gb windows partion, then 8 gb linux partion, 1gb swap partion, then a 39gb fat32 partion. Installed windows on the first one, then installed linux on the second, selecting the partions to use in gparted during the installation. The shared partion & windows partion should auto mount when booting ubuntu, the shared one will show up in "My Computer" on windows also.

If you're up for a bit of fun, you could also use ntfs for shared files, which requires you to use the new ntfs-3g driver. You could also use ext3 for your shared files if you want to use a windows ext driver (this is what I do). The reason you would want to do this is that fat32, at the end of the day, isn't that great of a filesystem, but if the other ideas seem like too much work, it'll do fine until you're more comfortable with linux.

---

### Post by TimelessRogue on 2006-11-30
Hey, you're gonna have fun with this one!  I've got Winlose 2k Pro on both my old HP n5000 AMD laptop and my home-built base station (with all sorts of esoteric goodies!) using ntfs ... why, I really don't know anymore since Ubuntu far surpasses anything Windoze can do for me.  But they're both there and sharing nicely ...

On the laptop, I got only a 30gb drive with 8 gigs allocated to Winlose and the rest for the Dapper Drake (which was set-up during the fresh install just the other day ... after a REALLY bad experience 'upgrading' from the original install to the Edgy Elf!)

With the desktop, I've got the benefit of six drives with one dedicated for 2k Pro to mess with, one for the Drake and one more for shared storage (the rest are just there to play around with at this point.)

All went well as far as setting up Ubuntu and letting it take care of partitioning all by itself ... which it does quite nicely, so you can feel comfortable about doing that.  For the dual boot, however, Windoze must be set up first on it's own partition, before installing Ubuntu ... then the Grub will recognize it and handle setting up the boot order just fine.

Good luck and have fun ...

---

### Post by yacobito on 2006-11-30
Thanks for all the replies!  That was the info I was looking for.  I am sure I will have more questions once I get everything up and running.  Have a good day.

---

