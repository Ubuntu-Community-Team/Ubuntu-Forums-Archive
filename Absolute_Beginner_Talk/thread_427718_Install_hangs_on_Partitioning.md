---
title: "Install hangs on Partitioning"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-04-29
Hey everyone, 

Sorry if this has been posted before, but I'm in a bit of a panic right now, so bear with me:

I decided to reinstall Ubuntu today (too much tinkering), and decided to make myself a /home partition so I wouldn't have to back up and rebuild my system from scratch. Ok, so I go into the LiveCD and start up GParted, as Ubiquity sucks :lolflag: I try to set up an extended partition manually, and it won't let me, only has the option to make a new primary partition. Fine, after a bit of thinking I decide to let the installer make a new extended partition (it did it with swap, why not with this?). I go to the screen where it asks how you want to partition the drive, and choose the first option (even though I already had an established Linux install). It promptly hanged. Can't move the mouse, no input, nothing. Am I in serious trouble here? Please tell me that my drive is untouched and I can just do a hard reboot and everything will be ok, please!!!! :( 

A somewhat related question:
Can you only have one extended partition on a drive? I remember reading somewhere that you can have more than one extended partition on a drive, otherwise I wouldn't have attempted this. 

Any and all help is gratefully appreciated! :D

---

### Post by LaurelLynn on 2007-04-29
Dear Happy_Man,

I've run into several problems with Gparted from LiveCD installs on my systems. I've used a couple of different workarounds. One of which usually works:

1.  Delete the install partition then recreate it. Sometimes the installer wouldn't accept an existing partition.

2.  Change the size or order of partitions.  Sometimes I found, particularly with extended partitions, that certain orders and sizes just wouldn't work. Failures came in several way, installer hangs, installs but won't boot. Tweaking the sizes and orders usually hit on a combination that worked.  So, it probably is something to do with the block alignment of the partitions.

At least those are what have worked for me.

You can only have one extended partition, but it can contain many partitions inside.

---

### Post by Happy_Man on 2007-04-29
Right, that answers why the installer hung. but my main question is if i reboot right now, will  my drive still be ok?

---

### Post by LaurelLynn on 2007-04-29
If you were not trying to change the size or location of the original partitions, most likely yes.

Gparted probably hung before, it rewrote the partition table. If it rewrote it gparted probably put the same values in the partition table for that partition and hung on the others.  Odds are that it did not scramble the partition table.

Try booting from the LiveCD if you have one to see if it can still mount and read the partitions. If not you need a new partition table. Which can be done with gparted only if you know the initial byte locations the partition began and ended at. There may be other more intelligent tools that can restore a scrambled partition table. Bottom line though, is that you need to know a least the byte the partition starts at.

Hopefully it won't come to that.

---

### Post by Happy_Man on 2007-04-29
Ok, I'll restart and see if everything works. Here goes nothing!

---

### Post by LaurelLynn on 2007-04-29
Oh, if it does come to that,  you manaully partitioned before, and  can remember the size entered then.

Running the same patitioner with the exact same entries, and no formatting should restore the table to it's old entries (I've done that once on a windows box using Qtparted).

---

### Post by davarino on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/111173/](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/111173/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having the same problems. I am running a dual-boot system and attempted to resize the Ubuntu partition.

I am running a dual-boot system and attempted to resize the Ubuntu partition. Windows partition /dev/hda1 ntfs was 116.21 GiB; Ubuntu was /dev/hda2 ext3 of (approx) 115.24GiB. In addition there was an extended /dev/hda3 of 1.44 GiB containing a linux-swap /dev/hda5 of 1.44 GiB.

Starting with Feisty Live CD, I initially tried to resize hda2 and gparted just didn't work, continually stating that hda2 had not been unmounted.

Not leaving well enough alone, I used the Dapper Live CD.

I told gparted to reduce the size of the Ubuntu partition and to make the new free area into another partition (a Primary partition because there was no other option offered). It took a long time to reduce the size (about 15 minutes), and then gparted soft crashed on the making of the new partition, with error message that the partition had not been created.

I rebooted the Dapper Live CD and opened up gparted again, only to have the original Ubuntu partition show its head again, undivided. And worse: listed as an "unknown" file system with no "used" areas showing.

The Ubuntu partition is inaccessible and the GRUB booter no longer works.

---

### Post by Happy_Man on 2007-04-30
Pseudo-related to this:

Can someone tell me how to get rid of the autocreated swap partition? It's locked, so I can't delete it using Gparted, and I'm NOT wiping the drive (just so nobody suggests it). Please? I really want a /home...

---

### Post by LaurelLynn on 2007-04-30
I've had the same problem. My quick and **very** dirty solution was to boot my old copy of XP on the other partition, and use Windows to delete it.

Problem is that every version of linux I've used, even live CDs grabs swap space at startup and says "oh! thank you don't mind if I do."

I know, there is a way to release it, but I can't for the life of me remember the command.

Maybe someone else will know?

---

### Post by LaurelLynn on 2007-05-01
Found it!

# swapoff /dev/hda8        (or whichever partition it is)

Well I feel pretty silly for forgetting somthing as simple as  that?

The command to turn it on again is equally simple "swapon".  Can use files
for space as well as partitions.  See the man page for more.

---

### Post by davarino on 2007-05-02
> **Happy_Man said:**
> Ok, I'll restart and see if everything works. Here goes nothing!

So, did you get it to work?

---

### Post by Happy_Man on 2007-05-05
Absolutely amazingly, if I boot from an Edgy livecd, it lets me delete just fine! Score one for old stuff!

---

### Post by davarino on 2007-05-08
"Absolutely amazingly..."

This is a phrase I agree with. I was able to restore everything by running **fsck**. My complaints about Ubuntu (and Linux) were completely vaporized.

I only wish that this kind of knowledge were a little better publicized. I suspect that a large number of gorked systems could be brought back to life simply by running fsck from the command line.

---

