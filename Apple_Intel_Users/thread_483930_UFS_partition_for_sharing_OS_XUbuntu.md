---
title: "UFS partition for sharing OS X/Ubuntu?"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by thully on 2007-06-25
I've been working on getting my system (MacBook Core Duo) set up how I like it for some time now, and I think I'm settling on a OS X (soon-to-be Leopard preview - don't ask, I'm under NDA) and Gutsy Gibbon pre-release dual-boot.  

Anyway, as I'm going to be testing OSes extensively on this MacBook, I figure I'm going to want a separate home partition for both OS X and Ubuntu. Due to limited space (60GB), I figure that a shared 30GB partition - with 15GB for each OS - would be good.  Would Ubuntu and OS X be able to use and share a UFS (BSD filesystem) home partition?  I figure that would be my best bet, as OS X supports UFS, it does permissions/etc (unlike FAT32) and I figure Ubuntu can handle it better than HFS+.  I know there could be some issues w/config files using the same names, but I don't plan on using MacPorts/the BSD subsystem much in OS X so this doesn't seem like much of a concern...

Any comments?  I know I've got quite a crazy setup here, but it seems like it may be the best setup for what I want to do which is test OSes while keeping my data separate.  I would just do VMware Fusion in OS X for Ubuntu (obviously can't run OS X in VMware on Ubuntu), but then I wouldn't be able to really help test Gutsy as well as I could due to insulation from the hardware and the issues VMware introduces.

---

### Post by ronocdh on 2007-06-25
I have never toyed around with UFS myself, but a quick Google yielded [this poor thread]("http://ubuntuforums.org/showthread.php?p=2869060") which has gone unanswered for about a week now. I encourage you to back up all your data and give it a whirl. I would think that after a day's tinkering, you'd have a feel for usability and whether it's viable, and then you can post back and let us all know, which would be ever so kind of you. :D

---

### Post by thully on 2007-06-25
I just created a UFS home partition just for kicks using OS X's nondestructive repartitioning (diskutil resizeVolume combined with Boot Camp Assistant).  Anyway, while using a UFS home partition works great in OS X (you actually use /etc/fstab and mount points to do it, just like Linux!), apparently Ubuntu has read-only support for UFS.  

Thus, I can't use it as a home partition for Ubuntu without recompiling my kernel (which I don't want to do - I prefer to just stick with stock rather than have to manually update things myself).  However, I do have a feeling that I *will* be able to use a case-sensitive, non-journaled HFS+ (as opposed to the default case-insensitive journaled HFS+) partition for this purpose.  Weird, but I do think it is a possibility - and it would be neat to be able to do this .

Now, doing this with Windows - THAT would be weird.  But you may be able to do it with good old FAT32...

---

### Post by ronocdh on 2007-06-25
> **thully said:**
> However, I do have a feeling that I *will* be able to use a case-sensitive, non-journaled HFS+ (as opposed to the default case-insensitive journaled HFS+) partition for this purpose.  Weird, but I do think it is a possibility - and it would be neat to be able to do this .
I use my OS X home directory (HFS+ non-journaled) as to store all my media for Ubuntu. I have r/w because journaling is disabled, but every now and then OS X reclaims permissions on the directories and I need to **sudo nautilus** to reenable them in Ubuntu. A pain, but it certainly works.
> Now, doing this with Windows - THAT would be weird.  But you may be able to do it with good old FAT32...
I used FAT32 on my Windows partition for a while to share media to all my system, but I wasn't in Windows enough to make it worthwhile. I've never seen decent HFS+ support on Windows, at least not for free.

---

