---
title: "extended partition and backups"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-03-06
i'm kinda a belt and suspenders guy and before i do anything dangerous i want to make sure i have a good backup

so i have a Ubuntu only computer with a primary and a secondary hard drive
primary is the system and secondary is backup only
i use partimage to make a backup and am wondering about "extended partitions"

hda2 is the extended partition and it is showing a id of 5 with about 1.5 gig in it

so i figured i would have partimage back it up too, but can't says unidentifible file type.

so i googled about extended partitions and have a idea of them now .

i experimented with my old 6 gig disk with Ubuntu 6.06 on it and backed it up and restored it and all was well
so i thought i had a warm and fuzzy feeling (but i did not wipe it clean, just overwrote it) and it would have not gotten to hda2 extended partition.

so with just Ubuntu on my system ( no windoz or anything else)is there anything in the extended files i should worry about or that would prevent my idea of a backup of hda1 and i can have my system back in case of a crash or cockpit trouble?
sorry for being long winded but wanted to give details
mitch

---

### Post by kidders on 2007-03-06
Hi there,

> **the.phantom said:**
> hda2 is the extended partition and it is showing a id of 5 with about 1.5 gig in itWhat do you mean by this?

> **the.phantom said:**
> is there anything in the extended files i should worry aboutI'm not sure what you're asking here. :-( Creating an extended partition at /dev/hda2 is most likely unnecessary. Since it seems to be causing you confusion, I can't help wondering why you created it. Could you describe your partitioning scheme?

> **the.phantom said:**
> or that would prevent my idea of a backup of hda1If you want to back up a partition, it is probably advisable not to put the backup on the same physical device as the stuff being backed up.

In general terms, making filesystem backups is a good idea. Your questions are difficult to understand though ... are you having difficulty with something in particular?

---

### Post by indytim on 2007-03-06
Maybe this will help you out.  The extended partition is basically a placeholder for the partitions that extend beyond the count of primary partitions (limited to 4).  Once you bridge this number an extended partition is created.

What I have found with respect to Partimage is that it makes life a lot easier if you run your Partimage from a second ops.  For example if I have Kubuntu 6.10 running on sda2 and I want to back it up with Partimage, I might want to run Partimage from say, sda3 (xubuntu 6.10).  I'd reverse the process for backing up Xubuntu 6.10.

Since you already have an extended partition, if you have room on your h/d, I'd suggest installing another U-K-Xubuntu and subsequently installing Partimage on each of your ops.  This will also yield a fall-back if one of the upgrades sends your primary ops into "fault-land" :) .

This is just one approach.  There are certainly other ways to tackle this situation.  You will probably hear from the collective on other applications/approaches.

Hope this is of some benefit to you.

IndyTim

---

### Post by the.phantom on 2007-03-06
when i installed Ubuntu 6.1 i did a "default install" and it defined the partitions and that is where the hda2 came from .
 
i do like the idea of a second hard drive for the back up as i have had a drive fail in the past with the backup on it's partition ;-(

i'm having no problems and love Ubuntu and have accidently learned some linux commands in the process

i use the "system rescue cd " to do the partimage.

i see all the post about GRUB and dual boots, and i do believe in the KISS principal ( keep it simple stupid) 
and in a few months i will make a backup and then update to fiesty and if any major problems i can go back .

and feel better with not needing that extended partition

thanks for the replies and help !
mitch

---

