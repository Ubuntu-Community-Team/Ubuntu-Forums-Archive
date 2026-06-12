---
title: "What's the best format for a hard drive?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-01-18
I have just installed Ubuntu to act as a server and have taken a drive out of a Windows machine which contains all my videos and music. This is the second drive in the Ubunu machine and is an NTFS file system. I can access all of the data on it ok and am in the process of setting it up so it can be shared by my other Windows mahines (and office machine and a media centre machine).

What is the best format to have this drive in. Will it be best to leave it as NTFS or will it work better / faster if I reformat it to FAT32 or something else? I want to use it to store all my media and also be used for backups from the office machine.

---

### Post by monte48lowes on 2008-01-18
If the only machine that will have direct access to the drive is the ubuntu server, then formatting it in ext3 would be my recommendation. I am sure you will get many others as well.

Mike

---

### Post by vikram on 2008-01-18
+1 for ext3.

Fat32 has a 4GB limit on filesize which could be an issue for DVD ISOs.

---

### Post by kellemes on 2008-01-18
I'd leave it as it is.. no need to spend the time formatting etc.. when it works.

---

### Post by thelatinist on 2008-01-18
If you don't have data on it already, then I would suggest reformatting to ext3.  If you do, then I would say that ntfs should work fine and formatting wouldn't be worth the hassle of having to back everything up and restore it.

---

### Post by Twizzle on 2008-01-19
I have already backed every thing up 'just in case' so I will give reformatting a go.

I take it that I will still be able to read and write to the drive from XP as a shared drive?

---

### Post by asmoore82 on 2008-01-19
+1 ext3

Faster, Stronger, Better.
Perfect for Network Shares managed by Linux.
Western Digital's newest line of "My Book" NAS(Network Attached Storage)
blocks are actually ext3 internally: [http://en.wikipedia.org/wiki/Western_Digital_My_Book#Physical_design_4](http://en.wikipedia.org/wiki/Western_Digital_My_Book#Physical_design_4)

---

### Post by bethebunny on 2008-01-19
You will need to download a special program in XP for it to recognize and read/write to ext3 filesystems. Go to [www.fs-driver.org](www.fs-driver.org) for more info. The program there adds an item to your control panel that allows you to turn on and off visibility on ext3 partitions in windows; once they are on, windows treats them as their own drive device, and can read/write to them as though they were fat32 or ntfs.

---

### Post by asmoore82 on 2008-01-19
you only need the Windows fs driver if you are actually going to take the drive out
and put it in a Windows machine; over the network via Samba it's all good.

---

