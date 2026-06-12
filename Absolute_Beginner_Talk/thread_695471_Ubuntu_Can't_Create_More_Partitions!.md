---
title: "Ubuntu: Can't Create More Partitions!"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-13
On the first screenshot you'll see **GParted**.

On **sda2**, I have** 2 GB** of free space, so I then decided to *shrink* it down, so that I can have the free** 2GB** of disk space.

After that one, you'll see that it is **unallocated**.

The whole plan is to merge it to **sda5**, which my **Ubuntu** installation is located. How will I do that?

When I right-click the **unalocatted** partition and select new, it says the following message that you'll see on the 2nd  screenshot.

Third screenshot, I became curious what's **sda1**, and why is it *eating* up **3 GB** of space. So I explored it.

Fourth screenshot, I accessed that *mounted* **FAT32** hard drive and saw some windows programs.

Fifth and last screenshot, I think I figured it out, It is the **Disk to Recovery** thingy of *Acer*.

QUESTIONS, is it safe to delete it, I already have my own recovery disk? If I *delete* it, can I merge it onto my current **Ubuntu** partition? Take note all in all, I am just using a **100GB** Hard drive.

HELP! Need more space!:confused:

---

### Post by logos34 on 2008-02-13
If you delete sda1, the only thing you can do with the resulting empty space is grow sda2 to the left.  But you'll need to use Gparted (> vers. 0.3.3), preferably from the live cd.

As for unallocated space between sda2 and sda4 (extended partition), you'll also have to work from the live cd (root cannot be mounted)--grow/expand sda4 into the left, then grow sda5.

Note: growing partitions to the left takes a long time because all the files have to be copied and moved over.  So get a BIG book to read while waiting.

---

### Post by karlo on 2008-02-13
> **logos34 said:**
> If you delete sda1, the only thing you can do with the resulting empty space is grow sda2 to the left.  But you'll need to use Gparted (> vers. 0.3.3), preferably from the live cd.

As for unallocated space between sda2 and sda4 (extended partition), you'll also have to work from the live cd (root cannot be mounted)--grow/expand sda4 into the left, then grow sda5.

Note: growing partitions to the left takes a long time because all the files have to be copied and moved over.  So get a BIG book to read while waiting.

I see, I thought **GParted** can't do any of the moving and resizing, which in my opinion, that program must do it, because it's as easy as transfering etc...

I don't need to defrag anything, right?

Speaking of LIVE CD, I install Ubuntu, I mean before doing that, I used GParted LIVE ...

Oh yeah, is it possible to use GParted LIVE via USB Flash Drive?

---

### Post by housam on 2008-02-13
> **karlo said:**
> I see, I thought **GParted** can't do any of the moving and resizing, which in my opinion, that program must do it, because it's as easy as transfering etc...

I don't need to defrag anything, right?

Speaking of LIVE CD, I install Ubuntu, I mean before doing that, I used GParted LIVE ...

Oh yeah, is it possible to use GParted LIVE via USB Flash Drive?

you have to reboot from Gparted live cd to do the job.

---

### Post by logos34 on 2008-02-13
> **karlo said:**
>  is it possible to use GParted LIVE via USB Flash Drive?

Yes, there's a usb version (see website).

No defrag needed.  

Gparted on the **Ubuntu live cd** will work as well (**7.10** that is, the earlier ones only have gparted 0.2.6, which can't resize left boundary)

---

### Post by hyper_ch on 2008-02-13
you have 4 primary partitions. you can't have more than 4 of those.

---

