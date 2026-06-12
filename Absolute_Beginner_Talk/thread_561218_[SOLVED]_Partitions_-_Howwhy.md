---
title: "[SOLVED] Partitions - How/why?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by gshockxc on 2007-09-27
[SOLVED] Do I need multiple partitions if I'm doing a clean install, not dual boot?  How do I know how much to make each partition?  Just do 50/50?  Why do I need them.  Totally don't get this.  I'm still on Windows ... for now, but I want to know what I need to do before making the move.

p.s. how do I subscribe to threads so I get email notices?

---

### Post by overdrank on 2007-09-27
> **gshockxc said:**
> Do I need multiple partitions if I'm doing a clean install, not dual boot?  How do I know how much to make each partition?  Just do 50/50?  Why do I need them.  Totally don't get this.  I'm still on Windows ... for now, but I want to know what I need to do before making the move.

p.s. how do I subscribe to threads so I get email notices?

Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
Good luck!

---

### Post by hyper_ch on 2007-09-27
Well, you need multiple partitions... and you can do this all from the install...

First of all, it depends on the system you have. You'll need at least two partitions (swap and root) and a home one is recommended.

Here is somethign to read:  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

During the install process select manual partitioning.

Then delete all the existing ones (if you want to do a clean install) and create those:

1x SWAP partition:  The type is "swap" and the size should be about twice your RAM. If you have like 2 GB ram then I think 2GB SWAP should be sufficient.

1x ROOT partition: Use as type "EXT3" and select as mounting point "/". Make the size at least 10 GB. I have 20 GB (but then I have a 500 GB and a 320GB drive).

1x HOME partition: use as type "EXT3" and select as mounting point "/home". This partition is intended to keep all your personal files like music, pictures, videos, documents.... so it will need a lot of space. Use the rest of your diskspace for it.

Regarding the threads: In the control panel you have somewhere the option of setting auto-subscription to threads you participate in (which I have enabled for myself) and for manual adding subscription you have on top those options " Thread Tools   Search this Thread   Display Modes   " --> select the Thread Tools one and then "Un/Subscribe to this threade".

---

### Post by madoracle on 2007-09-27
Partitions are really a personal choice, especially on a desktop setup. Having said that you'll need a swap partition and a boot partition at the very least. Personally I went with, on a system with two hard drives (60G and 80G):

sda - 60 GB drive
1 Partition
/ (This is my boot partition in addition to /)

sdb - 80 GB drive
2 Partitions
/swap is about 250 MB
/home is about 77 MB

In the past, on a Debian install, I had a 500 GB drive that I had split like:

hda 1 - 500 GB

/swap 300 MB
/home 200 GB
/tmp 20 GB
/ 100 GB

etc, etc. Every one of my top level directories had a seperate partition. I was bored.

---

### Post by gshockxc on 2007-09-27
Thanks for all the help.

---

