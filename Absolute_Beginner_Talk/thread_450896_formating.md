---
title: "formating"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-05-21
what is the best format for a hard drive if you want to use it between linux and windows,
and how do you reformat it?

---

### Post by oilchangeguy on 2007-05-21
> **axemurder785 said:**
> what is the best format for a hard drive if you want to use it between linux and windows,
and how do you reformat it?

what version of ubuntu are you thinking of trying/already using?

---

### Post by taurus on 2007-05-21
You have numbers of options. Ubuntu can read and write to ntfs with ntfs-3g driver and can read and write to fat32/vfat as default.  And of course, you can read and write to ext3 (Ubuntu default filesystem) from Windows with fs-driver ([http://www.fs-driver.org](http://www.fs-driver.org)) so just pick whichever you want. 

However, most people go with the fat32/vfat filesystem to share between Ubuntu and Windows.  Remember, you cannot save files larger than 4GB with fat32/vfat.

---

### Post by lsalminen on 2007-05-21
axemurder785,
 
You need to use an ext3 format for a linux drive, mounted at " / ". However, linux makes it easy to create a fat32 partition so you can install windows (dual boot). When installing Ubuntu, at the format screen, click manual, then you have to create 2 partitions, one for linux (ext3), and one for windows (ntfs/fat32). Remember, the linux drive has to be mounted at " / " .

That's what I did anyways. I find it better than sharing a partition, because Linux will let you erase needed windows files, and vice versa

-Lee

---

### Post by axemurder785 on 2007-05-21
feisty

---

### Post by oilchangeguy on 2007-05-21
> **axemurder785 said:**
> feisty

see taurus' post. 7.04 is capable of reading and writing to ntfs, etc.

---

### Post by axemurder785 on 2007-05-21
so i can install linux on a ntfs formated drive?

---

### Post by taurus on 2007-05-21
No.  You cannot install Ubuntu on fat32 or ntfs.  It has to be ext3 or you will run into problems soon.  So if you want to share files between Ubuntu and Windows, create a partition and format it as fat32/vfat.

---

### Post by nerdman978 on 2007-05-21
yes taurus already said that
although mine works fine with ext3 and i believe you need at least a 256MB part formatted to "linux-swap"

---

### Post by axemurder785 on 2007-05-21
i have 3 hard drives. one is internal and is almost full. two are external and are 60GB and 320GB. what should i do to use the 60GB one and the internal one for windows, and use the 320GB for Ubuntu Linux Feisty Fawn 7.04?

---

### Post by drowner on 2007-05-21
> **axemurder785 said:**
> i have 3 hard drives. one is internal and is almost full. two are external and are 60GB and 320GB. what should i do to use the 60GB one and the internal one for windows, and use the 320GB for Ubuntu Linux Feisty Fawn 7.04?

Are they permanently attached to your computer?

---

### Post by axemurder785 on 2007-05-21
no

---

### Post by axemurder785 on 2007-05-21
should i format one external drive to ntfs and format the other to the linux one?

---

### Post by louieb on 2007-05-21
Seems like you have the normal windows user confusion about whats a drive? whats is a partition? Same thing right? Well no there not. You can live without knowing anything about partitions  as long as your only using Linux. Or only using  windows. Don't need to know any of that tech o babble  stuff.
But since you decided to Dual Boot windows and Linux a knowledge of partitions and there types (there are only three) is very helpful.  Heres aplace to start  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

