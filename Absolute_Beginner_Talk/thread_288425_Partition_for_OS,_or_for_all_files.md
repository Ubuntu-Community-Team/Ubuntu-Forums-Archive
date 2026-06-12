---
title: "Partition for OS, or for all files?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by CallMeZoot on 2006-10-29
Hi,

I'm interested in installing Ubuntu as a dual boot with WinXP.  When I create the Ubuntu partition, am I creating it JUST for Ubuntu OS, or am I creating a partition for all of the files and documents that I will use within Ubuntu?

Problem is, I'm on a laptop that's pretty much maxed out for storage space, and I don't want to partition it any more -- I have a 100gb hard drive that's already partitioned into two.  Can Ubuntu read files on my existing Windows partitions, or does it exist in a bubble?  

In other words, can I create a partition with just enough space for the Ubuntu OS, and then use my existing partitions for all saving and downloading within Ubuntu?

Sorry if this is a newbie question -- I'm pretty fluent in Windows but I've never tried Linux before.

Thanks,
chris.

---

### Post by Marsolin on 2006-10-30
You can make a single partition to install Ubuntu to. By default, user files get installed to the /home directory. You will need to leave some space there for configuration files, browser cache, etc.

Ubuntu can read your Windows drive, but may have trouble writing depending upon which file system is formatted as. There are no issues with FAT32, but you may have trouble writing to NTFS. There have been some improvements in it recently, but it isn't full proof yet.

If your Windows partition is FAT32 then you could mount it as /home/username/files and us it just like any other folder. You could name it whatever you like, but it should be in your home directory.

---

### Post by rccharles on 2006-10-30
> **Marsolin said:**
> You can make a single partition to install Ubuntu to. By default, user files get installed to the /home directory. You will need to leave some space there for configuration files, browser cache, etc.

I did a fresh install of Ubuntu. I noticed that the install took 1.9gig. I am not sure if this included file system overhead. This does not include the swap partition. 

With this data for an minimalistic install that relies on using other partitions for more data , I'd suggest 3.5gig main partition and 0.5 gig swap partition.

Robert

---

### Post by Sef on 2006-10-31
You should not do just the bare minimum; otherwise your system will not boot up one day after an update or two.

> Sorry if this is a newbie question -- I'm pretty fluent in Windows but I've never tried Linux before.


No apologies necessary.  This forum is for any Ubuntu questions that a newbie might have.

---

