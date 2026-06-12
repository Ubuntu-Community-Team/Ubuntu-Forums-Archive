---
title: "Problems partitioning with alternate CD (Xubuntu 6.10)"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by freshofftheufo on 2006-11-29
Hi, I want to tell the partitioner on the Xubuntu alternate installation CD to use the same partitions (like just format, the partitions don't need to be recreated from scratch), but I can't figure out how to let it do that. Here's my story:

I'm now trying to install Xubuntu over an existing Ubuntu installation, and I'm using the Xubuntu alternate CD because my laptop doesn't have enough memory to run the LiveCD.

My hard-drive was originally partitioned by the Ubuntu installer so that there was a root drive (ex3) and a swap drive at the end. Later on, I used gparted to shrink the root drive a bit, creating a new (ex2?) partition in order to store my files while I reinstall xbuntu.

In the text menu for the alternate installation, it only gives me options to "erase" the entire hard disk (hda1), of which I only have one, but I don't want it to do that, I want it to use the same partitions after formatting and install in the same place that Ubuntu was installed in.

Isn't that possible? How can I make use the same partitions?

Please help! Thanks in advance!

---

### Post by Bachstelze on 2006-11-29
Don't you have the "Manual partitioning" option ?

---

### Post by freshofftheufo on 2006-11-29
Yeah, there's the option to "manually edit partition table", but that doesn't allow me to keep the same partitions, or at least I can't figure out how to get through it without rewriting the table. What should I do?

---

### Post by Bachstelze on 2006-11-29
Normally, when you select it, all your existing partitions will appear. All you have to do is to select each of them, format them if you wish, and enter the new mountpoint for them.

---

