---
title: "Partitioning for Dual Boot with Vista"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by cmo220 on 2008-02-20
I have a 160GB HDD with Windows Vista already installed.  I have an external 1TB HDD that i want to use for Ubuntu.  I have done this before with another external drive but this time I want to make a separate Home partition, which I also want on the external drive.  I was wondering if I could make the home partition a fat or fat32 partition so I could use my music, movies, etc. on Ubuntu and Vista.  Is this possible?  If so what problems could it cause?

---

### Post by BigWoop on 2008-02-20
Find out everything you can about XOSL, it worked for me.
Worst case scenario, you may have to re-install XP as well. (Regarding dual boot)

I'm a noob, but I don't think there's any problem using a FAT32 for both Windows and Ubuntu like you describe.

---

### Post by mkoehler on 2008-02-20
No, the optimal configuration would be to use the ext3 format for your ubuntu installation.  This filesystem type is accessible from both windows and linux, and is much better than FAT[32].

*The download that you need in order to read or write to a ext3 drive in windows can be found here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by oedha on 2008-02-20
for /home.......ext3 ( can't be read by windows )
is you want to share......make it just ada data partition.....it can be fat32 or ntfs

---

### Post by cmo220 on 2008-02-20
Thanks for all the Replies.  
mkoehler, that sounds like an interesting idea.  Do you or have you used this program for windows?  Do you know how well it works?  Does it make windows run even slower?
Thanks.

---

### Post by cmo220 on 2008-02-20
Anyone have any suggestions for best ways to partition my 1TB drive?  The computer has 2GB of RAM and will mainly be used for storing and playing a lot of music and movies.   I will install some games too, including some windows games through wine.    Not too much else will be done on the computer.  How big should I make the root partition so I never have to worry about running out of space, yet don't waste too much either.  Also, how big should I make the swap partition.  Should I make any other separate partitions? Thanks.

---

### Post by Duck2006 on 2008-02-20
/ should be 15 to 20Gb
swap should be 1Gb
the rest should be for home
If at a later time you want to have some space for some thing else than partition that space aswell and leve it blank.

---

### Post by Nameless_one on 2008-02-20
Windows can read ext3 with [this driver](http://www.fs-driver.org) (it is actually treated as ext2, but that doesn't matter as ext3 is ext2 with journalling). It works very well.

---

