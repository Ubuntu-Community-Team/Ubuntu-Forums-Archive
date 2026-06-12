---
title: "External HD mounting in OSX+Kubuntu"
date: 2007-12-23
forum: Apple Intel Users
---

### Post by slyn on 2007-12-23
So I was given a friends sisters laptop to fix, as her Kubuntu install was broken. I think somewhere an upgrade got interupted and that broke her HAL, as her usb ports, wired and wireless internet isn't working. 

All I figured I would do is put her data on an external I use for my Macbook Pro, do a clean Kubuntu install with / and /home on seperate partitions, and reload her data back onto the laptop. Thats when I realized her USB wasn't working, so I burned a Kubuntu live cd, learned how to mount her HD, got the external to be recognized. Unfortunately, due to my inexperience, I decided to resize my external's HFS+ partition to half its size, and then give the rest to ext3 so that I could copy her data over (what I shouldve done is just mount the drive as HFS+ and copy the data over). I can still access the data on the external with the Kubuntu live-cd laptop, but when I plug it into my MBP it gives me a message: "The disk you inserted is not readable by this computer". 

Seeing as how the disk is still readable with the kubuntu live-cd using "sudo mount -t hfsplus /dev/sdb1 /mnt", what/is there a comparable command in OS X to force a mount?

Also, the main applications she uses are firefox, Pidgen, OO.org, and Amarok, and seeing as how 3/4 of those applications are gnome based, I was thinking of setting here up with Ubuntu instead of Kubuntu. Is there a Amarok Gnome replacement in terms of functionality and ease of use?

---

### Post by willmcgree on 2007-12-24
Anxious to help, since something similar happened to me before after trashing my bootloader during a cack-handed install of Debian (thinking it was a LiveCD when it wasn't).

As far as apps go, yeah, they are GNOME-based for the main, but that doesn't mean they're the only options in Ubuntu. I use OO.o for Writer, Calc and that's about it. This is primarily because I'm too lazy to try anything else. However, if you want something more lightweight, try splitting the suite. AbiWord and Gnumeric are brilliant apps (if I remember rightly) and load a bit quicker. You can also then shed the bits like OO.o Base that few people outside enterprise need on a regular basis, and if she's not big into the presentations, she won't miss Impress either.

Short answer: never use cannonball to kill mosquito. Try lightweight options for zippiness.

To replace Amarok (not that there's a great need - my very very quick tests showed it to be "all right"), just give Rhythmbox a stab, and if that's not your cup of tea (and for some people it isn't), try Exaile which is essentially a GNOME port of Amarok (i.e. less fiddly).

As for the data recovery issue, this is not my strong point, if I'm being honest, and I think it's only fair that I am.

A sensible guiding principle for data recovery is to clone the original and only ever work with the clone. From what I understand, the problem lies in getting the original files off the external disk.

Try ISO Master (available from the repositories) and, if your external disk space allows, make a .iso file of the *entire* hard drive. As far as I know, and I may not be entirely correct here, but .iso files ought to mount on any system since they are independent of filesystem (which might be the issue you're describing). Personally, my external 80GB drive is in FAT16 format and has never let me down.

Once you can mount that .iso of the drive on another system, you know you're safe to trash the original and do a clean install.

A .iso file will appear as a drive within a drive in the Finder, but once it's mounted, it should be trivial to get the stuff over.

Good luck, but please don't act too hastily on the information given here. I'd love to help, but don't want to be too enthusiastic as to wreck a system (especially when it's someone else's).

Might be a good idea to leave this post until someone agrees with me or points out my mistakes.

Hope it works.
Will

---

