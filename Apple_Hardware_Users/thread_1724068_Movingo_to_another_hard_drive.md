---
title: "Movingo to another hard drive"
date: 2011-04-07
forum: Apple Hardware Users
---

### Post by canhoto on 2011-04-07
I have:

- A 160 GB HD running Mac OS X
- A 10 GB :( HD running Ubuntu

I want to:

- Move Mac OS X to a new 400 GB HD
- Move Ubuntu to the 160 GB HD

What's the best way to do that?
Should I use Disk Utility on Mac to do all the copies (like 160 GB -> 400 GB (Mac OS), then 10 GB -> 160 GB (Ubuntu)) or is there a special way to do that in Linux? Will it get yaboot confused?

---

### Post by handy on 2011-04-25
I've cloned the original 320GB drive in my iMac to a 1.5TB drive, using Clonezilla.

The original 320GB drive had fat32, HFS+, ext3, ext3 & JFS & /swap partitions/file systems. It worked easily & perfectly.

The way I did it was I pulled the drive from the iMac & put both drives into an old AMD powered machine that I have (using IDE -> SATA adaptors) & booted with the Clonezilla LiveCD.

You could have a look & see if they make a LiveCD that runs on PPC, you might be lucky. 

If not & you have an x86 machine laying around or available to you you could do what I did.

Anyway, good luck with it.

---

