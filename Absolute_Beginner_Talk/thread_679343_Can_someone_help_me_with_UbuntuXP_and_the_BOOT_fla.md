---
title: "Can someone help me with Ubuntu/XP and the BOOT flag?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2008-01-26
Ok, so I installed Ubuntu-64amd on my SATA drive in the third partition.

I told Grub to install to hd(0,2)

I gave the Ubuntu partition the boot flag.  Everything goes great.

However, everytime I go in XP, it resets the boot flag to the first partition on the disk; namely the XP partition.  :confused:

Any way around this?  I want XP's MBR to stay there in case I decide to scrap Ubuntu later on, so I'd like to be able just to move that flag around when it becomes necessary.  

Any help is greatly appreciated!

---

### Post by Rocket2DMn on 2008-01-26
Don't worry about that, as long as you're still getting the GRUB boot menu.  If you decide to get rid of Ubuntu, you can fix the mbr after uninstalling Ubuntu.  It is something like booting from the XP disk, going into the recovery console and running "fixmbr"

---

### Post by gohanssjn on 2008-01-26
That's just it.  Right now, it goes straight into XP becasue the drive boots to hd(0) but Grub is on hd(0,2).

---

### Post by Rocket2DMn on 2008-01-26
OK, let's recover GRUB and overwrite the windows bootloader, you can get it back later if you need to with fixmbr at the windows recovery console.  Here's a little guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0) - just make sure you use the correct /dev locations for your system.

---

### Post by gohanssjn on 2008-01-26
Well, i can boot in on the live CD, can I just plainly install GRUB to hd(0) then?  I mean, it still exists on hd(0,2), it just doest go there when it boots.

Or do I need to install to hd(0) and remove from hd(0,2)?

---

### Post by gohanssjn on 2008-01-26
Ok, I think I got it.  i ust ran this thread's first post:

[http://ubuntuforums.org/showthread.php?p=121355#post121355](http://ubuntuforums.org/showthread.php?p=121355#post121355)

And we'll see what happens...ok, Ubuntu booted, see what happens when I try to load XP!

Thanks for the help!

---

### Post by willubunto on 2008-01-26
great. 
I started the thread and it seemed to me that Gruss suggestion was very safe.
I'v thanked him.

---

