---
title: "My laptop has quickplay by hp."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by pHEnomIC on 2007-04-30
I am using an HP dv6000 series laptop.  It has quickplay on it which allows you to watch dvds and listen to music without loading windows.  I was wondering if i should even bother trying to install this or not?  I am wondering if my media buttons and whatnot will work without loading quickplay.


I am going to be dual booting ubuntu and xp pro (I require this because i do some PCM tuning and my software is windows native and I don't want to risk anything by emulating it).  My hd is 120 gb, i plan to give 40 or so to xp. and the rest to ubuntu.

---

### Post by starcraft.man on 2007-04-30
Ummm, I'm not sure I understand... this quickplay feature, it plays DVDs without you booting into windows? So it turns your lab top into a dvd player? If it doesn't use anything in the XP install then I don't see why you would need to reinstall it after ubuntu. If you have a hidden partition that runs this, don't delete that partition and this feature should continue to work. If I got that wrong, please clarify what quickplay from HP is.

Whether or not you have this installed, Ubuntu supports DVD playback via the right gstreamer codecs that can be installed after you set up Feisty. As for the keyboard shortcuts if they are special buttons that require drivers from the keyboard maker they might not work, a hack for xorg might be available on the internet or you could just bind new shortcuts to regular keys.

As for dual booting, 40 is fine for XP. I'd give 6-8 GB to the root parition (/) , 4 GB (I assume you do intensive stuff) to the swap file and then if you want a big drive for storage make the rest /home in ext3 format. If you want to make this drive mountable in windows, make I'd make it fat32.

---

### Post by mikewhatever on 2007-04-30
With mine HP Pavilion, the quick play function does not work from Ubuntu, although the volume related buttons do. I haven't tried it from GRUB, since I really think it a useless kind of thing. It loads slowly and does exactly what any media player does.

---

### Post by rothfuss on 2007-04-30
Quickplay is a major pain...  See here: [http://forum.notebookreview.com/showthread.php?t=62357]("http://forum.notebookreview.com/showthread.php?t=62357"). 

Basically, you need to reinstall windows XP to install quickplay (if you've already wiped out the partition).

If you haven't wiped out the quickplay partition, you will have an easier time -- add a grub menu item in /boot/grub/menu.lst.

---

### Post by annda on 2007-04-30
my samsung laptop sports an 'AV Station' - probably an equivalent of your quickplay. it sits in its own partition and is actually a skimmed XP. it is rather useless, too, but i haven't deleted the partition because i'm not interested in reinstalling windows from the recovery cd - and i need it once a year for my tax program. plus reinstalling would probably repartition my drive.

before you install, see where this quickplay is located. type this in live cd's terminal:

```
sudo fdisk -l
```

if you have two NTFS partitions, like me, you probably have quickplay there. unless you want to get rid of windows altogether, i recommend you don't mess with it.

when installing ubuntu, choose resizing the LARGER windows partition. and defragment it first at least once!

---

### Post by mojo123 on 2007-04-30
same laptop same question 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

---

### Post by Grungydan on 2007-04-30
As an aside, the other media buttons on my HP Pavillion dv9000t work "out of the box" in Feisty.  (I mean the Play/Pause, forward, reverse, and stop buttons, in additoin to the volume buttons.)

I hadn't tried the Quick Play functionality, but then again I rarely used it prior to installing Ubuntu.

---

### Post by olavjunior on 2007-08-29
I've used my quickplay buttons to control volkume, skip tracks etc. But suddently now they don't respons at all. No clicks or anything :(

---

### Post by kornface13 on 2007-08-29
> **Grungydan said:**
> As an aside, the other media buttons on my HP Pavillion dv9000t work "out of the box" in Feisty.  (I mean the Play/Pause, forward, reverse, and stop buttons, in additoin to the volume buttons.)

I hadn't tried the Quick Play functionality, but then again I rarely used it prior to installing Ubuntu.

Your play/pause and all that works??  Only my volume up/down and mute works.  I'd love to be able to use my next track and play buttons.  What program are you using them with?  I unstalled the totem player and installed vlc.  Thanks in advance.

---

### Post by olavjunior on 2007-08-29
> **kornface13 said:**
> Your play/pause and all that works??  Only my volume up/down and mute works.  I'd love to be able to use my next track and play buttons.  What program are you using them with?  I unstalled the totem player and installed vlc.  Thanks in advance.

I've used my play, skip, pause, mute & volume out of the box with feisty, but now none of them suddently work anymore... They worked with all kind of players

EDIT: Booted into xp, and realized they doesn't work there eighter! Damn! Going to reinstall everything from scratch, so I'll see if they work after that. If not, it will be going straight back to hp!

---

### Post by kornface13 on 2007-08-30
Really??  Wow, mine sucks!  I wish I would have tried it with the default player but I didn't.  It definately doesn't work with VLC/songbird.  I even went into the System - Preferences - Keyboard Shortcuts, and manually put everything in, but Songbird completely ignores it.  Stupid thing!

If anyone has any suggestions please throw them out there.  Thanks!!

---

### Post by perfect_circle on 2007-09-05
i have the same problems, my buttons worked for a while, then all of a suddne they stopped, but i still have the beeps. any one know how to fix this?

---

