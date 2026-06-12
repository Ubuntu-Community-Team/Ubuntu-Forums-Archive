---
title: "how do i dual boot my laptop with a blank hdd?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-07-06
right i have a blank hd to start with so how do i best go about setting up a dual boot probally 5gb for ubuntu the rest for windows

Cheers

---

### Post by mikeyphi on 2007-07-06
Do you have Windows already installed? 
If not  - install Windows and then install Ubuntu.
If yes just install Ubuntu and opt for the size you want during the install process.

---

### Post by hyper_ch on 2007-07-06
Windows is not yet installed and I tend to think that 5 GB aren't much for Ubuntu

---

### Post by davidjmayo on 2007-07-06
> right i have a blank hd to start with so how do i best go about setting up a dual boot probally 5gb for ubuntu the rest for windows

First read this [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

any question please post a reply

---

### Post by dptxp on 2007-07-06
You need to install Windows first.
5 GB is OK for Ubuntu / (root) if you have separate data partition.
Use 1-2 GB extra for SWAP.

---

### Post by TrevorRS on 2007-07-06
cheers so swap is the bit that can be assesed by windows and linux?

Cheers
Trevor

---

### Post by twiceasworn on 2007-07-06
Honestly there are a ton of walkthroughs and write-ups for this exact scenario.  I would suggest googling **Dual Boot Windows and Ubuntu Linux**.  No reason for us to re-invent the wheel.

---

### Post by TrevorRS on 2007-07-06
i found myself a simple guide now! ntfs of fat32 for windows as the guide dosent tell me the benefits of advantafes of each?

Cheers

---

### Post by twiceasworn on 2007-07-06
When I did mine i set the windows partition up as NTFS since linux didnt need access to any of those files, then I had a partition called Osshare that was fat 32 so I could save things to that and they could be manipulated by both OS's.

---

### Post by davidjmayo on 2007-07-06
> cheers so swap is the bit that can be assesed by windows and linux?

Sorry NO!. Swap is used by linux when RAM (memory) is full or near full but it's on your HD so it's slower. That's why it's only 1GB (or double your RAM)

Post here your HD size and what partitions and sizes you are planning to use before you start

---

