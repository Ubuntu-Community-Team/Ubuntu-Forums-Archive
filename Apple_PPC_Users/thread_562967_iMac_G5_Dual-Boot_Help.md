---
title: "iMac G5 Dual-Boot Help"
date: 2007-09-29
forum: Apple PPC Users
---

### Post by cheezle on 2007-09-29
OK, I think I might have posted this question in another thread, but I would feel better if I had a thread all to myself to get this question answered. :)

I have an iMac G5 rev. B, and I tested it with the Xubuntu live cd and everything works fine.  I  want to install Xubuntu, but want it to be a dual-boot system so that I can use all my precious osx programs I paid for/came with the system.

My friend told me that I can re-size my osx partition with a program on the Xubuntu live cd, and then use the free space to put Xubuntu on it.

Will this work?  What file system do I need for Xubuntu?  Can I re-size the partitions once I have Xubuntu Running alongside osx?  And is there anything extra I need to know (such as non-standard issues to work around).

Thanks in advance! :KS

---

### Post by Lo'oris on 2007-09-29
AFAIK first you have to disable journaling on the OSX partition, because the shrinker program (gparted) doesn't support it (you can re-enable it later, I guess).

Then you can do the resize thing from the live cd, and install *ubuntu into the free space.

What I haven't been able to understand is how much safe is this shrinking thing. A full backup is important, sure, but they will tell you this anyway both if it's 50% safe or if it's 99% safe : P

In past, I've often shrinked ext (linux) partitions and vfat (windows) partitions, but never tried neither hfs (mac) nor ntfs (xp).

---

### Post by cheezle on 2007-09-29
> **Lo'oris said:**
> AFAIK first you have to disable journaling on the OSX partition, because the shrinker program (gparted) doesn't support it (you can re-enable it later, I guess).

Then you can do the resize thing from the live cd, and install *ubuntu into the free space.

What I haven't been able to understand is how much safe is this shrinking thing. A full backup is important, sure, but they will tell you this anyway both if it's 50% safe or if it's 99% safe : P

In past, I've often shrinked ext (linux) partitions and vfat (windows) partitions, but never tried neither hfs (mac) nor ntfs (xp).

Of course I will be backing this up as soon as I get an external drive.  But what do you mean "shrinking"?  And what is this about journaling?  I know what it is, but why do I have to disable it, and why should I be able to re-enable It later?

---

### Post by cheezle on 2007-09-30
Sorry for the double post, but I have another question.

I should use the free space for the ext3 partition, the  swap partition, *and* the boot partition right?  And should all of those be formatted to ext3?

Thanks!

---

