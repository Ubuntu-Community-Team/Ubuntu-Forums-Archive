---
title: "What use is NTFS?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by wmkok on 2008-02-24
I have just bought a new laptop with Vista, and out of frustration finally switched to Ubuntu. All is working well, but I still have some 'windows history' to deal with... So, I need some advice / help.

I have an external HDD 500 GB with all my movies, pictures, music, etc. Many files, total almost 250 GB,way more than the internal 80GB. This is an NTFS disk.

I have a dual boot laptop with an XP version of windows, uncompatible with most of the hardware, and a 'Data' partition of 55 GB in NTFS. I made this because I thought I needed it for the large movies (over 10 GB each) and to be accesible from Windows.

Now, my question:
 - read/write to ext HDD on NTFS, does this give any trouble
 - what is the best filesystem for the DATA partition, if I only want to access it from Ubuntu, and if I want to access it also from Windows

I have managed to add the ntfs partitions to /media with NTFs-3g, but cannot write more than six files in a folder... So this is not yet a solution.

Please, give me some advice / help...:(

Thanks,

Wouter

---

### Post by ChaosParser on 2008-02-24
Fat32 for both.  Ext2 or ext3 for just Ubuntu.

---

### Post by justsomedude on 2008-02-24
If you opt for a ext2 or ext3 file system, there is also the option of installing an ext2/3 driver for Windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I suggest you read the FAQ section on this site. :)

---

### Post by LaRoza on 2008-02-24
> **wmkok said:**
> 
Now, my question:
 - read/write to ext HDD on NTFS, does this give any trouble
 - what is the best filesystem for the DATA partition, if I only want to access it from Ubuntu, and if I want to access it also from Windows


0. No, I do it all the time. No problems.
1. EXT3 for Ubuntu, NTFS for Windows, and for both use NTFS.

Do not use FAT32, except for flash drives, if you are using Ubuntu 7.10 and up. 

FAT32 has severe limitations, and fragments like a grenade (not a plasma grenade)

---

### Post by cdtech on 2008-02-24
I use a dual boot system on my laptop, having a 250G drive for my Ubuntu and a 160G original drive for my Vista. Everything works great.

I partitioned my 250G drive to include an NTFS partition of 150G for downloads and storage so that my windows could read this partition as well. All of my media gets stored to this partition. I've had no problems reading or storing data to this partition.

---

