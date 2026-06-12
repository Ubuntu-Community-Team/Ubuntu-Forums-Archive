---
title: "Hangs on boot screen after wiping hard drive"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by teknosexual on 2008-02-10
I probably went about this entirely the wrong way, so I will tell you what steps I have taken.

Initially, my machine was dual-booting XP and Ubuntu. My hard drive is 320GB total. I had XP on a 40GB NTFS partition, Ubuntu on (the rest)GB ext3, and a 2GB swap. I wanted to do a fresh install of both OSes on differently-sized partitions than what I currently had.

So I booted from the XP installation CD and choose to delete partitions. The partition that appeared on the XP screen said only 137GB. I choose to delete it. Then no other partitions appeared, so I thought that was odd. I then booted from GParted Live CD and looked at my partitions. The same 137GB partition was listed, and only that partition. I tried to delete it in GParted but it wouldn't let me perform any action on it (presumably because XP had already deleted it?).

I then rebooted, and, of course my normal boot menu was not there. I decided to wipe the drive then. I booted from Hirens Boot CD and used Boot & Nuke to wipe my hard drive. Once it finally completed, I removed the CD and powered down the machine. When I powered it back up, my blue HP boot screen (which appears briefly before either GRUB or XP boot menu would) appears. It is not responsive to my keyboard commands (tapping ESC or F10), and it just hangs there.

I have tried to boot from Hirens Boot CD, GParted, Ubuntu Live CD, but all results in hanging at that HP boot screen.

I am not sure where to go from here. I know I need to boot from CD. I know I can do that by configuring that option in the boot menu. But what do I do if the boot screen just hangs?

Thanks in advance for any help! I am really stumped here. :confused:

(By the way, I do not have a floppy drive.)

---

### Post by bumanie on 2008-02-10
The reason you could only see more than 137gb is due to a bios limitation whereby motherboards made before a certain year (can't remember the exact year, but about 2001 or 2002) would only recognise hard drives that large.
As far as your booting problem goes, are you able to enter bios settings when the system hangs? If so you should into bios and set your boot order to have your cd-rom as the first boot device. Then you should be able to get either the windows install cd or the ubuntu live cd to work.
(I assume the system hangs because there is nothing for it give instructions to ie nothing to boot).

---

### Post by teknosexual on 2008-02-10
Thank you for the quick response! I did not know that about the BIOS/motherboard limitation. Good to know!

As to boot screen, I am tapping ESC in order to enter BIOS (according to the boot screen ESC will get me to that screen), but it is unresponsive...just hangs.

---

### Post by tyggna1 on 2008-02-10
My guess is that boot and nuke screwed up some things in either your hard drive firmware or on your bios.  If it's the hard drive firmware--then you may have just turned an old hard drive in to a brand new brick!  If it's the BIOS, then there'll be a jumper (little plastic thing that covers two pins) on the inside of your computer that'll let you reset that.  If you pull the jumper off and it stops hanging, then you can breathe easier.  If it doesn't, then you may actually need a new hard drive (call the manufacturer of the hard drive before you do that, though. . .)

---

### Post by teknosexual on 2008-02-10
You are scaring me, tyggna1! lol

I have managed to make some progress. After letting the drive cool about 2 hours, I powered it back on and was able to enter BIOS settings from the hanging boot screen, and finally boot from CD. I am installing XP now, so yay!

I guess the hard drive was too hot?

I don't have a lot of experience or knowledge about hardware, so is the hard drive being too hot to function a common issue? Or should I be concerned that mine is on its way out?

---

### Post by bumanie on 2008-02-10
I began writing another reply about cmos, but as you have got your hard drive working, I stopped. I would personally be concerned if my hard drive was getting that hot. When you've finished installing windows, I would double check all connections and jumper settings just to make sure they are all correct and that you aren't getting funny voltages from poor connections. Excessive heat is electronics worst enemy. May be you need an extra fan inside the box. Proprietary boxes are renowned for being manufactured with the minimal components that are necessary, therefore if you add extra gear, often the default cooling is not enough. Check out whether there is room for extra fans or at least a cpu larger fan.

---

### Post by teknosexual on 2008-02-10
> **bumanie said:**
> I would personally be concerned if my hard drive was getting that hot. When you've finished installing windows, I would double check all connections and jumper settings just to make sure they are all correct and that you aren't getting funny voltages from poor connections.

You know, I have noticed my fan has been running a lot more frequently lately. Hmm. Definitely worth looking into. Thanks for all of the great information. :KS

If you don't mind I might PM you with some specs once I get everything set back up. I know my CPU (Celeron D) temp is okay, it averages about 30, but didn't think about the hard drive being a heat source. Yes, unfortunately, I have one of those bargain basement systems. :\

---

