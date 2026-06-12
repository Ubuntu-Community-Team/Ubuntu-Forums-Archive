---
title: "Best Filesystem for USB drive"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-08-18
Hi,
I want to format my new USB 250Gb drive as a backup for both windows and linux systems. Both must have read and write access
I want large partitions, perhaps only 1 or 2.
All the partitions must be available to both systems as documents may move from one to the other if one is broken!

Whats the best filesystem for this. Is it NTFS with the new read/write stuff thats just emerging or is it ext2 or ext3 with a windows driver for them?

any ideas? and advice?

Ta
Jeff

---

### Post by anaconda on 2006-08-18
I use the ext3 with driver for windows
[http://www.fs-driver.org/](http://www.fs-driver.org/)

but because it is a removable drive I used the workaround in about the middle of this page.. (to get drive letters automatically on/off in windows.) read carefully.
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

I am sure someone will recommend fat32, which can also be good, but personally I dont like it.. too many limitatitons and problems.

But really. It is a matter of opinion, and your choise depends also of how much you use windows..  
If you use windows more than 70% of the time, then you might consider even ntfs, and install the ext3 driver to windows, and when you want to copy files from ubuntu to ntfs-USB you boot to windows and do it from there.. (too) coplicated ? Or trust the (experimental) ntfs writing driver for linux..

The only time I have had a "problem" with fs-driver was when I tried to copy files to my (ext3) USB drive, and there wasn't enough room for the files I tried to copy.. And with the next boot ubuntu noticed some errors in that partition, and automatically fixed them.  So it wasn't very serious "problem"

I recommend the ext3 and fs-driver to windows.. Unless you mostly use windows, and just sometimes play with linux

---

### Post by jethro10 on 2006-08-18
THanks, I'll look at the ext driver for windows.
I use linux 90% of the time but want a fallback, hence windows reading it.
Dont' think Fat32 goes above 32Gb partition size so that out of the window (Ha! out of the window Get it :) )
Oh well.

so ext3 seems worth a format.

thanks
Jeff

---

### Post by frrobert on 2006-08-18
In terms of compatability FAT32 is the best but you have the standard issues with Fat32 on large drives such as file size limits.

There are drivers for windows XP, NT that will read Ext2 but I havn't used them yet.

Reading NTFS in linux is fine.  According to some, writing NTFS in Linux is 99% but is that good enough for important data?

I'm a bit of of a chicken so I would suggest FAT32 so you will be able to share that information with any machine but I've heard the Ext2 driver for windows works well too.

---

### Post by anaconda on 2006-08-18
Actually using fat32 is possible. Linux can make big fat32 partitions, and windowsXP can use them. I had problems with win2000, which tried to "fix" too big fat32 partition (after some use), and destroyed all data! (Happened 2 times).

Windows XP doesn't have the same problem...

But there is the problems with 4GB file size limit, and no permissions etc..

EDIT: and if you do make it an ext3.. you probaply dont want to reserve 5% of the space for root user.. Like qtparted does..

---

### Post by huygens on 2006-08-18
> **jethro10 said:**
> Dont' think Fat32 goes above 32Gb partition size

Not quite exact. I have a hard disk with one 320 GB FAT 32 partition :-)
The limitation you encountered _has been set by Microsoft_ on its Windows XP (and perhaps 2000 or 2003, I don't remember) to *help* people choosing NTFS rather than FAT32. NTFS has the advantages over FAT32 of (only major benefits are listed here): being journalised (checkdisk is really fast after a crash), handling user access (via ACL) and being able to handle files bigger than 4 GB.
You can found format tools to create partition bigger than 32 GB in FAT32. :-)

Why am I using FAT32 for my external HD? Well, I have Windows and Linux playing with it, and in a couple of days I will have a Mac... So I did not find any other solution than sticking to FAT32, as I did not find any ways to read ext2/3 under MacOS X...
The only drawback of this solution: I cannot put DVD iso on it if they are bigger than 4 GB ; I have to take care to split my backups in files not bigger than 4 GB ; the Mac will only see the first 128 GB of this partition ; it is not safe... if someone get a virus under Windows, all the data are compromised as there is no access safety with FAT32!!! ](*,)
So this is not the best solution I have now... But I'm still looking for other interesting one.

Huygens

---

### Post by Nrvnqsr on 2006-08-18
> **anaconda said:**
> 
EDIT: and if you do make it an ext3.. you probaply dont want to reserve 5% of the space for root user.. Like qtparted does..

I was wondering for a work around for that, some enlightment please

---

### Post by Thirsteh on 2006-08-18
In my opinion, you should always go with FAT32 over ext* (with third-party compability drivers for Windows). Custom-made drivers are unofficial and unreliable, at least more so than Linux's FAT32 compability -- and Windows' own, I would hope.

PS: Always choose this for scenario's like this. Obviously if it was solely being accessed from Linux, I'd strongly recommend ext3 or ReiserFS (if you have thousands of small files, and few large).

---

### Post by anaconda on 2006-08-18
> **Nrvnqsr said:**
> I was wondering for a work around for that, some enlightment please

Space reserved for root user can be adjusted afterwards by using tune2fs

tune2fs -m 0 /dev/sda4

before doing that you can first check  available space by df, and after tune2fs check again, and notice few gigabytes more  :)

It doesn't affect files on the disk..

---

### Post by mgscox on 2006-08-18
Most universally accessible format across operating systems is FAT16.
Many linux variants support FAT32, some support NTFS.
Generally, I've found that linux boot-from-USB-drive o/s's (e.g. puppy linux) offer limited support for anything other than FAT16.
At the end of the day, the choice is yours - FAT16 will be read on just about anything, FAT32 most things, NTFS not quite as many; the trade off is the size of the partitions. I'd recommend against ext as its less well supported by other o/s
Like most things in life, there is no "right" answer, just many options.

---

### Post by jdong on 2006-08-18
Just a quick warning: **Test the ext3 Windows driver thoroughly before putting serious data on the drive!**

I've seen many reports of corruption with the driver.

---

### Post by anaconda on 2006-08-19
> 
I've seen many reports of corruption with the driver.

Hmm.. I havent had any problems (execpt with the one with drive gettin full)
Can you give some pointers, I would be wery interested.

> 
Custom-made drivers are unofficial and unreliable,

I would say the same with ntfs-drivers, because ntfs is a CLOSED format, so the makers of the driver dont know how ntfs is really put together. 
BUT ext3 is public format, which the maker of the driver had all the info he needed. 

How come you use linux, which is also made "as a hobby"

---

### Post by jdong on 2006-08-19
> **anaconda said:**
> Hmm.. I havent had any problems (execpt with the one with drive gettin full)
Can you give some pointers, I would be wery interested.


Well, all I can tell you is that my friend has reinstalled Ubuntu twice while playing with the ext3 Windows read/write driver linked here. Maybe they fixed something since then.

---

### Post by orb9220 on 2006-08-19
I have a 112Gb fat32 partition which both xp and ubuntu can access. 

I don't understand why people keep saying you can only have a 32Gb size that is untrue. The single file limit is only like 3.99GB so for movies I use dvdshrink under wine and just have it saved as HD file instead of iso and it works like a champ.

And no matter how many times I want to use ext3 for an external it always ends up I need to copy a file to another computer that is only xp and end up kicking myself for not having it fat32.

Murphy Rules!

---

### Post by jdong on 2006-08-19
> **orb9220 said:**
> I have a 112Gb fat32 partition which both xp and ubuntu can access. 

I don't understand why people keep saying you can only have a 32Gb size that is untrue. The single file limit is only like 3.99GB so for movies I use dvdshrink under wine and just have it saved as HD file instead of iso and it works like a champ.

Because for some silly reason, Microsoft limited XP's formatting tool to only allow FAT32 volumes under 32GB. It's not a FAT32 limitation, it's a Windows XP limitation. XP has no problems reading/chkdsking larger FAT32 volumes, it just doesn't allow you to make them.

The real limit is the 4GB/file limit, which can get annoying at times.

---

