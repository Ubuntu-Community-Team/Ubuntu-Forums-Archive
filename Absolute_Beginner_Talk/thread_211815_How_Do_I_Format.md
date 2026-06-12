---
title: "How Do I Format?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Breezy Badger on 2006-07-08
I have a 300 GB HDD, I want to put it into FAT32...It is now in NTFS.  I tried to use Qparted...but the only damn disk it detects is the 512MB memory card I have in my memory card reader...no hard drives, but the hard drives are very much there and accessable via the desktop etc

---

### Post by John.Michael.Kane on 2006-07-08
Try this [**gparted-livecd**]("http://gparted.sourceforge.net/livecd.php")

---

### Post by moffa on 2006-07-09
I don't think you can convert NTFS to FAT32 with Gparted.  You might have to use commercial software such as Partition Magic.

---

### Post by Handyman's Special on 2006-07-09
Hi,

Just bought a used 80 gig hard drive this afternooon, at the flea market. Hooked it up to the computer by itself, put the Ubuntu Live-CD in the drive and opened Gparted. I deleted all the partitions and made new ones. I was able to choose what I wanted to format them with, too. It was lightening fast, compared Windows, too.

If you don't get it right the first time, you can always do it over.

Having a ball learning this OS.
Handyman's Special

---

### Post by Breezy Badger on 2006-07-09
Ok well here is the problem.  I am using QTparted to try and format a hard drive, but I have to be logged in as the root for any hard drives to even appear....I can't log in as the root without the root password and I don't have it.

Any ideas?

---

### Post by John.Michael.Kane on 2006-07-09
A method was already posted. you can use the gparted live cd to do what your asking. [**Filesystems supported by GParted**]("http://gparted.sourceforge.net/features.php")

---

### Post by Breezy Badger on 2006-07-09
oh I got it thanks, had to unmount it first before I formatted it.  Now I just have to get it remounted

---

