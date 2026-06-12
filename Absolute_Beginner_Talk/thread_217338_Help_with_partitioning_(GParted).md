---
title: "Help with partitioning (GParted)"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by darthvivi on 2006-07-17
This actually isn't for Ubuntu (it's for Slackware) but the Ubuntu community is so awesome, and I already have a forum account because I use Ubuntu on the computer I'm typing this post on. I'm using GParted (LiveCD), so it should be the same.

I have a 20GB hard drive with Windows ME on it, and I'm wanting to duel boot with Linux. Right now, Windows ME takes up about 4GB, and I want to leave another couple GB of free space for it. But GParted seems to have trouble recognizing my Windows partition...

On the GParted Live CD (Same as GParted in Ubuntu), it says /dev/hda1 is an "unknown filesystem" taking up "7.84 GiB" and that I have "11.25 GiB" of "unallocated space." I can't resize /dev/hda1, but I can create a new partition. I'm confused on what to do.

---

### Post by orb9220 on 2006-07-17
On the 11.25 create a 11 gig ext3 for root mount point would be / amd the rest make a linux-swap partion

so after creating the partions click next on the next screen is where you assign the mount points and format.

Make sure the / is assigned for the 11 Gb and is ext3 and the other which would be around 600-900 mb for linux-swap see that they have the check mark click to reformat also look to make sure that the unrecognized is not checked for reformat as that is probable yer win me partition.

---

