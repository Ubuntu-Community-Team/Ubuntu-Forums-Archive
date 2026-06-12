---
title: "must a partition be unmounted to use dd to clone/back it up?"
date: 2009-07-04
forum: Apple Hardware Users
---

### Post by Tommmyboy on 2009-07-04
Hi.

I've never seen it explicitly stated anywhere - maybe because it's common knowledge I don't have - and because I don't want to fool around with it testing it out because I've heard it's a very powerful command, but to use dd at the command line to back up a partition, or a full disk for that matter, must the partition/disk you wish to back up/clone be [COLOR="Red"]**un**[/COLOR]mounted first?  

If the answer is yes, does anyone know if dd could be used in an OS X terminal to back up a Linux partition on a dual boot Mac? My understanding, via the wisdom of Cyberdork, is that using Disk Utility to create DMG clones of partitions that are formatted with a system other than HFS+ or one of its variants isn't possible, which makes me question the use of dd in OS X to clone anything other than HFS+ volumes only because I have no idea if there is a relationship between the function of the Disk Utility app and dd. 

Thanks in advance. 

To those in the States, happy BBQ Day ("independence" is so subjective, lol).

---

### Post by nathanid95 on 2009-12-05
Yes, DD doesn't work on mounted volumes. It sounds like you can do what you need by creating a disk image of the disk from Disk Utility.

P.S. From what I've seen, Disk Utility is simply easier to use.

Correction: I was wrong. Thank you, Dennis, for pointing this out. And excuse me for attempting to answer a previously unanswered question.

---

### Post by buntuLo on 2009-12-06
dd is my standard backup tool, i use it for partitions and more often full disks. just run it from a linux livecd on unmounted partitions/disks. why do you need macosx to backup linux partitions?

---

### Post by dennis123123 on 2009-12-06
> **nathanid95 said:**
> Yes, DD doesn't work on mounted volumes. It sounds like you can do what you need by creating a disk image of the disk from Disk Utility.

P.S. From what I've seen, Disk Utility is simply easier to use.

You've bumped a topic from July, and replied with bogus information!

DD *does* work on mounted volumes, it is what is known in the forensics world as a "live acquisition"

test it if you like - ```
sudo dd if=/dev/sda bs=1k count=1 | xxd
```will show you the first kilobyte of your hard disk, in hex.

---

### Post by shortmort37 on 2010-08-29
> **dennis123123 said:**
> You've bumped a topic from July, and replied with bogus information!

DD *does* work on mounted volumes, it is what is known in the forensics world as a "live acquisition"

test it if you like - ```
sudo dd if=/dev/sda bs=1k count=1 | xxd
```will show you the first kilobyte of your hard disk, in hex.

OK - so, here's another question:  If I have a running system on /dev/sda0, and an available partition (same size) on /dev/sdb0 (both with swap space on sdx1) - and, I cron

sudo dd if /dev/sda0 /dev/sdb0

nightly, when the system is quiescent - do I have a reasonable expectation that, if sda were to fail - I could swap sdb in its place, and be able to boot from it?

Dan

---

