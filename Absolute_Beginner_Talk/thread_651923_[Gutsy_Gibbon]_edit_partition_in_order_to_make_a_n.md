---
title: "[Gutsy Gibbon] edit partition in order to make a new one?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-12-28
Hi,
I'm currently installing Gutsy Gibbon and i'm at the point of setting up the partitions, with the Manual option. What i want to do is to make the new partitions (by the way, what partitions i have to make? ext3/ext2 and swap? at least this is how i remember) from an existing 70% free NTFS partition. I choose the partition i want to resize then i click on "Edit partition" and here i set up the "New partition size in megabytes" to whatever size i want to for the new partition ? (by the way, what sizes do you recommend for each partition? i know that for swap i only need like 500MB - or at least this was on 5.10, the last tried version)

It may sound logically enough but i really dont want to mess up any data on my partitions since i have very important data on it, and i haven't backed up anything yet :|

---

### Post by eternicode on 2007-12-28
I just setup a fresh Kubuntu Gutsy install on a desktop a little while ago, and my impression of Ubiquity's (the installation program's) partition editor remains the same.

I would highly recommend using QTParted or GParted, whichever you're more familiar with, to pre-partition the drive; then, during the installation, specify where X/K/Ubuntu should mount the new partitions.  SO much easier in my opinion.  My personal preference is GParted :)

And minimum partition setup is one linux fs (ext3, ext2, reiserfs, etc) and one swap.  As a reference, the way I set up my desktop was 40MB for /boot, 8GB for /, 509MB (originally 512MB, but I guess GParted thought differently) swap, and the rest for /home.  I got these numbers from my existing Kubu Feisty notebook installation, by exploring the directories' sizes with "du -h", but I think maybe the / partition is a little big, by at least 2GB.  A lot of what I've read on swap says twice the amount of RAM you have, or 512MB, whichever is smaller.  Though I've also read that hibernation writes to the swap, so, in order to hibernate, you have to have as much swap as you have ram. 

And I think Ubiquity said something about system partitions (/, /boot, etc) HAD to be formatted...not sure what that's all about, or which ones in particular it mentioned, but if you have an existing linux installation, I would recommend at least moving stuff like your /home to a separate partition...

In my editing: o_0 let me know if anything I've said doesn't make sense, I feel like I'm rambling.

---

