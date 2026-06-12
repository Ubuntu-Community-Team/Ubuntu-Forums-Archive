---
title: "Setting File Server. How to partition?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by 6kwar on 2007-06-13
Hi all


I want to setup a file server. I got 500GB in Raid 1 = 250GB.

I want to know what is the best way to create the partitions? 

This is the server spec

Core Due 6600
Intel 965
2X WD 250GB YS (Raid Edition)
1 Gb Memory
Antec 430W Power supply.
WD 250 USB External for backups.

How much to give to swap partition?

How much to give to the Linux partition? 
Is it wiser to create only 1 partition? Or to create 2 and save everything on the 2nd?

Thanks guys.
I succeeded to do everything on a dummy server. 
Ubuntu is awesome! I just saved about 2000$ using Ubuntu and not using Windows Server 2003.

---

### Post by tchoklat on 2007-06-13
Usually you have up to 2Gb swap
You need about 4 Gb for Ubuntu - up to 10 doesn't hurt
Home partition - as much as you have left!

---

### Post by 6kwar on 2007-06-13
Thanks. That's what I thought to do.

---

