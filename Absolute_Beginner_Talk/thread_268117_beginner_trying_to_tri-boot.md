---
title: "beginner trying to tri-boot"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by ballyhoo on 2006-09-29
this may be a lot to ask but i'm trying to tri-boot:
1) xp pro on 80gb hard drive already installed
2) ubuntu on 2nd drive (250gb sata)--empty (no data)
3) edubuntu on 2nd drive

i've already partitoned the 2nd drive:
a) 80gb (for ubuntu)
b) 20gb (another function)
c) 100gb (pics)
d) 40gb (web dev)
e) 10gb (edubuntu

am i going about this in the correct way?
thanks

---

### Post by bodhi.zazen on 2006-09-29
You need to add a swap partition, size ram X 2, 1-2 GB max.

The swap partition can be shared.

---

### Post by thephantomlinguist on 2006-09-29
You'll probably be okay with your partitioning scheme. A couple of recommendations, though:

1. Cut back on how much you're giving Ubuntu and make a separate partition for /home--then you can share it between Ubuntu and Edubuntu. Along the same lines, you might want (or heck, need) to pull your /boot out onto a separate partition as well.
2. Give yourself a swap partition in there somewhere. How big you want it will depend on how much RAM you have and how you'll use your computer. A general rule-of-thumb is twice your RAM (256MB RAM = 512MB swap).
3. Since you'll have more than four partitions on that second drive, be sure you set up an extended partition on there and create a couple of those partitions as logicals on it.

At the risk of giving you too much advice, the following might be a good way to set up your disks:

hda1 -> Windows (primary)
hdb1 -> /boot (primary)
hdb2 -> extended
hdb5 -> swap (logical)
hdb6 -> /home (logical)
hdb7 -> /pics (logical)
hdb8 -> /other_function (logical)
hdb9 -> /web_dev (logical)
hdb10 -> / (ubuntu root)
hdb11 -> / (edubuntu root)

Ubuntu and Edubuntu roots are at the end of the disk in case you ever decide to get rid of one or change entirely. Then you can resize the partition(s) without borking your home, pics, web_dev, etc. partitions.

This is all just a suggestion. There is no warranty on any of this advice. Use at your own risk.

But, as always...

Hope this helps!

---

### Post by ballyhoo on 2006-10-04
thanks for all your help.  i printed out your suggestions and failed trying to figure everything out (mounting ect.)  i visited a local linux support group and boy were they helpful.  I'm now up and running-well crawling actually.

i only dual booted as ubuntu/edubuntu are so simular.

next stop---dual monitors!!!

---

