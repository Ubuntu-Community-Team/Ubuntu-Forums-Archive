---
title: "Install problems"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by onimike on 2007-06-24
Okay, heres the story.

About a month ago, I installed Ubuntu 7.04 (DVD, i386) onto a hard disk that was natively windows xp.

I created a seperate partition for Ubuntu, 40gigs, while windows kept 120 gigs.  Everything was fine and all that.

About two weeks ago I upgraded my system, heres the new stuff:
Gigabyte 965p-ds3 mobo
Intel e4300 C2Duo 1.8ghz
2x 1gb G.Skill DDR2
Geforce 7900 GS 256mb ddr3
Wireless card: D-link air plus dwl-g520 rev.B

When starting up with this new hardware, neither Ubuntu nor Windows would load up.  SO instead of troubleshooting with no internet connection, I put in the WinXP Home disc, did a format and install.

The thing is, it only touched the windows partition, so the Ubuntu partition for 40 gigs is still there, but I can't seem to touch it.  Inserting my Ubuntu DVD (i386, 7.04) will load up the install menu.  Selecting install will load up a linux kernel, but on the Ubutnu logo progress bar is hardlocks the system and forces a restart.

It will not load the text installer either.

So what can I do to either go back to my old version of Ubuntu, or wipe it and install a new one?

Thanks in advance.


edit:  this probably should be posted in install&upgrades, so ill post it there too

---

### Post by Scunizi on 2007-06-24
All that has really happened is "Grub" has been overwritten by the fresh windows install. Insert the Live CD and get to the desktop then open a terminal window.

Now type grub ... you'll get a new prompt and be in grub

next type "find /boot/grub/stage1"

the response you get will have something similar to (hd0,1) in the line.  What ever the first item is (in this case it's hd0) insert into the next step.

which is... type " setup (hd0) " it'll buz and wirr for a few secs and may produce some output. 

now type "quit" to get out of grub

REBOOT.. and you should have your grub menu back...

---

