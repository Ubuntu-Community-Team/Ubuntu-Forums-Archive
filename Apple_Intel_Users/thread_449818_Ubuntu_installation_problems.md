---
title: "Ubuntu installation problems"
date: 2007-05-20
forum: Apple Intel Users
---

### Post by PaaC on 2007-05-20
Hi there,

I have got some problems installing Ubuntu. Let me first explain what set-up I have.

Hardware: 
MacBook Pro C2D 2.33ghz 2Gb RAM.
Maxtor OneTouch III 750Gb connected with FireWire 800.

Partitions:
Internal HDD (GPT):
1.1) 86Gb HFS+ with Mac OS X 10.4.9 installed.
1.2) 26Gb NTFS with Windows XP Pro installed using Boot Camp.
External HDD (GPT):
2.1) 590Gb HFS+ with just random stuff
2.2) ~45Gb ext3 clean.
2.3) 30Gb clean
2.4) 30Gb clean

I have also rEFIt installed.

Now, here's what I would like:
Ubuntu on 1.2 for work stuff, Windows XP on 2.2 for gaming and random OS for testing on 2.3, I would like Vista there at the minute.
I know that it can be quite tricky to install XP on an external drive, I have tried but have not succeded, so I have to have XP on 1.2 for the time being.
So would I be able to install Ubuntu on 2.2? How would I do that?

I have actually a more serious problem with my installation. I have tried booting from the Ubuntu 7.04 x86 CD but it fails to initialise X window server, so I can't even install Ubuntu on 1.2...
I burned the CD from an image that I have used to installed to install Ubuntu in VMware under Mac OS successfully.

I am very grateful for any help or suggestions given. ;)

---

### Post by ronocdh on 2007-05-21
Check my sig for help with the X failure. As far as your partitioning setup goes, I recommend using FAT32 for Win XP and then installing Ubuntu internally on a very small partition, like 5-6GB or something. Then you can store all your media on the FAT32 partition, which is mutually r/w accessible by OS X and Ubuntu, without any permissions problems (of course this is the case in Win XP, too!). Booting XP from an external drive would be a heck of a job, and while I think Ubuntu externally is more of a possibility, you still have a headache ahead of you.

Search this forum for topics on booting Ubuntu from external drives; there's been much talk of it, but not *too* much fruit, from what I've seen. It doesn't interest me personally, though, so perhaps I've missed something valuable! Please post back with the results of your experimentation.

---

