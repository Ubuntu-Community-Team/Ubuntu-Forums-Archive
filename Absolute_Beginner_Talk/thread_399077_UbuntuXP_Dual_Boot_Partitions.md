---
title: "Ubuntu/XP Dual Boot Partitions"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by billandsebastian on 2007-04-01
I am looking to dual boot Ubuntu and XP on my laptop. I have an 80GB HD and was mapping out how I will partition it out, but I want to make sure that what I am doing will work out. I have looked at various sites and come up with this plan:

1. Windows (NTFS) - 5GB
2. Shared Files (FAT32) ~60 GB
3. Ubuntu (EXT3) - 5GB
4. Swap - 2 GB

(Do I need/can I get an "Ubuntu /home" partition?)

Currently my HD has two partitions, a NTFS of 70.6GB with 38.8GB open and a system restore FAT32 of 3.88GB with 1.54GB open. I have installed PartitionMagic, but have not used it yet as I have heard that it might be safer to go with the Ubuntu installer partitioner. Thanks in advance for help.

---

### Post by oilchangeguy on 2007-04-01
you'll need to keep more than 5gb for windows. just windows and sp2 take up over 2gb, and that's not including any other programs. 60gb for shared files? at some point if you find you don't need windows just back up your files and do a clean install of ubuntu. 2gb swap? as in windows if your computer needs to use virtual/swap memory, you've got a computer with problems. your best bet is to let ubuntu take the largest un-used portion of the drive and do it's own thing. it does a fine job of setting it's own partitions.

---

### Post by mikewhatever on 2007-04-01
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Whether you want to have a separate home partition is up to you, also 2 GB of swap is quite a lot, I'd go for 1 GB.

---

### Post by billandsebastian on 2007-04-01
Maybe 10GB for Windows, 50 for Shared Files (Fat32), 10 for the Ubuntu (EXT3) and 1 for the swap then? Also should i use partition ghost or just wait until the Ubuntu install?

---

### Post by zvacet on 2007-04-02
Before install resize your partitions with this
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Wotching on 2007-04-02
If you download the program from [http://www.fs-driver.org/](http://www.fs-driver.org/), you don't have to deal with crappy FAT32 for shared files -- You can use ext3 and access it from both Windows and Ubuntu.

---

### Post by billandsebastian on 2007-04-02
That sounds good. I had heard of the prgram before but I was a little worried that I wouldn't mount something properly and be screwed until the end of time. I guess thats what disk backups are for.

---

