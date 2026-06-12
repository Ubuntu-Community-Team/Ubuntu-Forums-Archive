---
title: "Unable to mount a Fusion Drive partition"
date: 2018-08-21
forum: Apple Hardware Users
---

### Post by kalagan on 2018-08-21
Hi there!

Sorry if this topic has been seen a lot before, I did searches but didn't find any related topic…
After 30 years with MacOS, I decided to move to Ubuntu (xubuntu).
I'm using a MacBook Pro from 2012 with homemade Fusion Drive (a SSD replaced my DVD player).

On MacOS, it was quite easy to change the partitions, and create a 60GB partition for Linux.
Then I installed Xubuntu on it, it works well, dual-boot using alt-key is perfect, Wifi is working, everything is fine.

What I'm struggling with is the ability to mount the Fusion Drive HFS+ partition on Ubuntu. I installed the HFS+ drivers, other external HFS+ harddrives mount easily, but I can't see this partition.
I tried to add some lines in /etc/fstab, indicating what seems to be the "virtual" full HFS+ partition (/dev/sdb2 in my case), I did the same with the UUID of this partition, with no success.

Did anyone succeed in mounting Fusion Drive partitions on Ubuntu?
Does anyone has a piece of advice?

Thanks, a lot, in advance!

Kalagan

---

