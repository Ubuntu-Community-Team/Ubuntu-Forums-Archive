---
title: "How do I resize a partition when my CD drives don't work and I am not too technical?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-07-31
...in windows...

I have a 4gb  Partition and a 24GB partition. I want to make the 24gb partition 18GB and 4gb partition 10gb.

On the 24gb I have XP installed and on the 4GB I hope to make 10gb i want to install Ubuntu via Wubi as my CD drives don't work. How do I go about SAFELY resizing the partitions without LOOsING DATA!!!???

-thanks, 
another non-techincal future ubuntu user.

(Specs - 1.01GHZ PIII, 512mb RAM, 28gb HD)

EDIT: Ideally I would want to do this in Windows itself, then just use Wubi but I doubt this is possible.

Oh yeah, and free is the only price!

---

### Post by henriette_holm on 2007-07-31
Well, that's going to be a bit hard. I actually have no suggestion - sorry :(

Something else though. If somebody suggests some way you can do what you're looking to do, please do a backup first anyway. It will save you a lot of tears if something happens.

/Henriette

---

### Post by LaRoza on 2007-07-31
> **ajskhan said:**
> ...in windows...

I have a 4gb  Partition and a 24GB partition. I want to make the 24gb partition 18GB and 4gb partition 10gb.

On the 24gb I have XP installed and on the 4GB I hope to make 10gb i want to install Ubuntu via Wubi as my CD drives don't work. How do I go about SAFELY resizing the partitions without LOOsING DATA!!!???


You can use Windows to resize the partition.

---

### Post by henriette_holm on 2007-07-31
Are you sure about that? I thought you could only make and delete partitions. I think you need Patition Magic or something similar to alter a partition.

/Henriette

---

### Post by ddrichardson on 2007-07-31
[Ranish]("http://www.ranish.com/part/") from Windows or use the [System Restore]("http://www.sysresccd.org/Main_Page") Live CD

---

### Post by henriette_holm on 2007-07-31
His cd drive doesn't work :/

---

### Post by HKiCore on 2007-07-31
I have used a program called Gparted to make and resize partitions. For me it has worked very well. You can install Gparted using Synaptic. It's also included in Feisty Live CD. I like it because it's quite straightforward and simple tool. 

Since your CD-drives don't work, there is the LiveUSB version available in GParteds [homepage]("http://gparted.sourceforge.net/liveusb.php"). However I have no experience how to create LiveUSB.

Hope this helps or at least gives some directions.

[Here is also some basic info about partitioning]("http://ubuntuforums.org/showthread.php?t=282018&highlight=gparted")

---

### Post by ddrichardson on 2007-07-31
Can still use Ranish though :-)

---

### Post by louieb on 2007-07-31
> **ajskhan said:**
> ...CD drives don't work.... SAFELY resizing the partitions without LOOsING DATA!!!??? ... non-technical ...free is the only price!
Safety of data and resizing partitions :confused: Shrinking a partition can be done without loss of data. 1st   [See the prep Win partition Section here]("http://www.linuxdevcenter.com/lpt/a/6554") that will help reduce the chance of data loss. Without a CD drive looks like you are stuck with Ranish. I have never used it barely heard of it, don't know how reliable it is. Unless you have a way of backing up and restoring your data. Come to think of it without a working CD drive the restoration not going to happen if shrinking the partition messes up the operating system so bad it won't boot. 
You have to many negatives here my friend. If this PC absolutely has to function I would leave it as is and not try to resize its partitions.

---

### Post by ajskhan on 2007-07-31
Well basically it is a useless machine that no one uses... So I thought - install ubuntu, it'll be faster than xp, hook it up to the internet and BAM! makes a great online game computer for my bro... Well - might just wipe it!

---

### Post by henriette_holm on 2007-08-01
Well, if that's an option I would defiantly just wipe it - although I have no idea how you're going to install Ubuntu without a working cd drive.

/Henriette

---

### Post by ajskhan on 2007-08-01
one word- wubi!!!

---

