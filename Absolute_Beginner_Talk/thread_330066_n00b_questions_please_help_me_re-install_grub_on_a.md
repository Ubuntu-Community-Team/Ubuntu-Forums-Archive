---
title: "n00b questions: please help me re-install grub on a Dapper install"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by klokwyze on 2007-01-02
I had to re-install a funked up windows install. Just replaced Windows XP Pro SP2 with the same thing. This obviously wrote over the boot file.

I have searched all over the place for information on how to re-install this, but no 2 answers are the same. I know I need to mount the Dapper install partition and somehow reinstall the grub, but can't seem to figure this out.....?

If anyone could post a link to a good guide to do this or just tell me I would appreciate it.

:D

---

### Post by bernied on 2007-01-02
[This](http://www.ubuntuforums.org/archive/index.php/t-24113.html) howto should work. 

There are no two answers the same, because there are many ways to achieve this.

---

### Post by klokwyze on 2007-01-02
How do I mount a partition? How do I find out exactly which partition the Ubunu install is on? Nothing in that link clearly states how to find this.

The Ubuntu 6.06 partition is on one internal HD, its like 3rd or 4th partition on that HD.

How do I get a root terminal?

All these "easy guides" tell me to get a "root shell" or "root terminal", but none explain how to do it. When I go into a terminal and type "su" (I guess this is how you go into super user mose,is this the same thing as root?) and it asks me for a password!!!! why would it ask me for a password when being run from a cd???

[B]RANT:
man.... every single "easy guide" in there is different so full of holes and use jargon I don't understand.

if people list "mount the partition" as a  step without explaining how to do it, it isn't exactly "newbie friendly".

Sorry if I come off rude, but the process of getting this OS to work correctly is EXTREMELY frustrating when all the people who try to help assume "noobs" know everything in the 1st place!!!! So its like everytime I run into a problem, I search for about an hour two, NEVER find a fix and then post a thread trying to get help. Must users of Ubuntu read a 500 page manual to get this thing to work correctly?[/B]

---

### Post by Patrick K on 2007-01-02
Super Grub is what I used to do it. A bit daunting for a beginner like me but it worked.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GnuLinux_Advanced](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GnuLinux_Advanced)

You can get the file here:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)
Pick the media and language you want then burn the img or iso to floppy or cd. The floppy version is command line only but who uses floppies these days. 

Boot from the CD, and follow the instructions. It isn't as confusing as the first link makes it seem.

---

### Post by Sef on 2007-01-02
> I have searched all over the place for information on how to re-install this, but no 2 answers are the same. I know I need to mount the Dapper install partition and somehow reinstall the grub, but can't seem to figure this out.....?


Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").  If you only installed XP, then there is no need to remount Dapper.  Just restore grub.

---

### Post by klokwyze on 2007-01-03
> **Sef said:**
> Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").  If you only installed XP, then there is no need to remount Dapper.  Just restore grub.

awww yeah. that was EASY and that is what i am talking about!!!

These great programs are out there, but hard to find... one day I hope a Linux distro can replace my windows... its just too much of a pain right now to learn all this stuff. I actually respect windows more now cause I remember how shitty it was back @ 3.11 lolz....

---

