---
title: "Wow, I feel cheated"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by three_sixteen on 2005-12-18
So I chose Ubuntu as my first linux install after wrestling with myself over installing Knoppix from the CD as my first venture into linux.  So I give it a test run using VM Ware expecting to have a lot of trouble only to find out that I only really needed to hit Enter a bunch of times.

I feel cheated :rolleyes: 

:p 

Ah well, tis a good way to get my feet wet I guess.

---

### Post by lsald on 2005-12-18
VMWare has fully supported 'hardware'. Try a real install... ;) it'll be the same :)

---

### Post by three_sixteen on 2005-12-19
[QUOTE=lsald]VMWare has fully supported 'hardware'. Try a real install... ;) it'll be the same :)[/QUOTE]


Aye, all installed -- already have a new theme installed and everything.

I was cautious at first and left my windows filesystem intact, giving linux a rather small partition to work with -- wish I would have gone bigger now.

My only problem now will be getting in touch with all of my mp3s and stuff on my windows partition.

---

### Post by rooster on 2005-12-19
[QUOTE=three_sixteen]
My only problem now will be getting in touch with all of my mp3s and stuff on my windows partition.[/QUOTE]

Maybe create a new FAT32 partition (if you have the space) and use it to share data between WIN and Linux (both can read/write on it).

So you can copy your mp3-files to it from windows and read it from Linux.

Have fun with Ubuntu!

Rooster

---

### Post by Wolki on 2005-12-19
[QUOTE=three_sixteen]My only problem now will be getting in touch with all of my mp3s and stuff on my windows partition.[/QUOTE]

Here's a guide on how to read/write fat32 and read ntfs with ubuntu: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

Like many of the wiki guides, it seems very long and difficult, but it's actually just detailed. :)

---

### Post by MetalMusicAddict on 2005-12-19
[QUOTE=three_sixteen]My only problem now will be getting in touch with all of my mp3s and stuff on my windows partition.[/QUOTE]
You have more options.

-If you only need **read** access see [HERE]("http://ubuntuguide.org/#automountntfs"). (Im assuming your drive is NTFS)
-Instead of FAT32 you could format the drive Ext3. Read/write from linux is out of the box but for windows you will need to use [THIS]("http://www.fs-driver.org/"). It will give you read/write access in windows but without the filesize limit of FAT32.

---

### Post by rooster on 2005-12-22
[QUOTE=MetalMusicAddict]
-Instead of FAT32 you could format the drive Ext3. Read/write from linux is out of the box but for windows you will need to use [THIS]("http://www.fs-driver.org/"). It will give you read/write access in windows but without the filesize limit of FAT32.[/QUOTE]

Hi Addict - this link was great! Now I can use my USB-Drive with Ext3 on my Linux-Desktop and my Windows-Notebook! :D 

Thanks a lot,

Rooster

---

