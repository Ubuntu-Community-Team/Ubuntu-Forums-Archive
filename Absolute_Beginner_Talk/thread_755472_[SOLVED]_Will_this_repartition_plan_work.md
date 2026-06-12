---
title: "[SOLVED] Will this repartition plan work?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by dmub82 on 2008-04-14
About to do a clean install of Gutsy. After a little dual booting, playing with the partitions and then deleting XP, my ~74gb hard drive currently looks like this (all partitions ext3):

<-hda1: 14Gb, empty->  <-hda5: ~48Gb, mostly full of must-keep data-> <-hda6: 5Gb, root-> <-hda7: 6Gb, home (nothing I need to keep)-> <-hda9: 1Gb, swap->

I want to end up with:

<-10Gb clean root install->  <-63Gb new home partition which contains that must-keep data-> <1Gb swap>

I was thinking what I'd need to do is this:
1) Boot LiveCD, use Partition Editor to delete hda6 and hda7 (the current root and home partitions) and grow hda5 into that space to the right.
2) Resize hda1 to 10Gb, leaving about a 4Gb unallocated gap between it and the other partition.
3) Install Ubuntu into the first partition.

Can I set the big data partition to mount as /home when I do the install, or would that erase the 40Gb of data I need to keep? Or do I need to just install into the first partition, using it as root and home, and then move /home to the second partition as described [here]("http://www.psychocats.net/ubuntu/separatehome") once I get running?

Then when I'm set up, reclaim that 4Gb gap by booting the LiveCD, using Partition Editor to move the second partition left into that space and then grow it back out to the right? Does this make sense? Will it work? Is there a more efficient way to do it?

eta: And no, I don't have a second hard drive I could move that data to so I could just wipe the whole thing.

---

### Post by Inxsible on 2008-04-14
I would advise on keeping a separate home drive.

and can you format hda5? if so, you dont have to merge the 4GB later. you can do it in the same session.

Or do you mean you have data on it which cannot be backed up on an external or something?

---

### Post by dmub82 on 2008-04-14
Thanks for the quick reply -- you mean you recommend:

<-root-> <-home-> <---------------------------data--------------------------->

or am I misunderstanding you? If that's what you mean, what's the benefit and how big does the home partition need to be at a minimum if that's not where I'll be keeping most of my data?

And yeah, hda5 is currently holding the ~40Gb of data that I need to keep (my entire music collection and more) and I don't have another drive to back that up to. That can't get formatted.

---

### Post by Inxsible on 2008-04-14
yes that's what i recommend. This is my system - just so you can guesstimate something for yourself

25GB Vista - NTFS
15GB Windows Data - NTFS
9 GB root - EXT3
19 GB home - EXT3
82 GB Shared data - EXT3
1GB swap

Of the 9 GB of root, 4.1 GB are full
Of the 19GB of home 1.57 GB are full, so you can imagine that since i have a separate drive for my music movies etc. home doesnt get that full.

I would recommend 15GB root, 10-15 GB home and rest as Shared data

Of course leave something for swap - maybe 1GB

As for the advantage of a separate home :
> Having a separate partition for /home is always a good idea, since it lets you reinstall your system without losing valuable personal data. This can be especially useful in a distro like Ubuntu, where users have the chance to upgrade their install quite often (every six months) and might want to perform a clean install to avoid potential problems. Nevertheless, and while some other distros out there already do this automatically, Ubuntu doesn't.  There is some reasoning behind it: creating separate partitions might lead to waste space in / if you leave too much space, or run out of space if you leave too little. But on the long run, it is one of those things seasoned users wish they had done since the very beginning. So why not at least tell them they CAN, and ask them about it?

---

### Post by dmub82 on 2008-04-14
Thanks again. Like you described, the only data I keep is mostly music and video and such so if I have a separate partition for that, how small can I go with my /home partition? Since I won't be dual booting, could I do like:

<-10Gb root-> <-4Gb home-> <- the rest for that big data partition with all my music and stuff -> <-1Gb swap->

or would I run into problems somewhere? I'd like to have the music/video partition as big as I can without squeezing root and home too small.

---

### Post by Inxsible on 2008-04-14
the more users you have on the system, the bigger /home you will need. The more software and programs you install, the bigger /root you will need.

I would still recommend
15 GB root
at least 10 GB home
rest as data
1gb swap

---

### Post by dmub82 on 2008-04-14
Cool think I got it now. Appreciate the help.

---

### Post by Inxsible on 2008-04-14
> **dmub82 said:**
> Cool think I got it now. Appreciate the help.you are welcome. Mark your thread solved if all questions have been answered :)

---

