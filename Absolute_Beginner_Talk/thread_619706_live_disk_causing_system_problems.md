---
title: "live disk causing system problems?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jory88 on 2007-11-21
I ran the latest live disk on my Dell a couple of days ago.  

Now when I start my system it hangs miserably on boot, and prompts for CD.  

Can only boot with live cd in tray, and choose run off first HD option...

Any advice for a confused newbie.  I thought the live CD runs from the CD only?  It wouldnt have installed anything or changed any settings would it?

cheers!

Jory

---

### Post by victorgreen on 2007-11-21
Live cd shouldnt have installed any anything on the harddirve, it loads all its programs to ram. 

It sounds like your bios has been set to boot from cd first and wastes extra time on boot looking for a cd. Change it to boot from HD first and some of the lag time should be eliminated.

---

### Post by Sef on 2007-11-21
Have an old Dell laptop, and I have option of doing a one time boot if I push F12.   If you do set the BIOS to run off the hard drive first, then that would be a good option when you run the live cd.

---

### Post by rmemm on 2007-11-21
I hope that it didn't cause issues -- but as with any software it's possible.  Meaning - it's not intended to cause problems -- but it can.  The old statement that your system is only as good as it's last backup is really true.

There are several things that can happen.  One -- if you access the disk read/write from the live CD then sure -- you are modifying it.  If you use various Linux commands like fdisk or programs like Gparted -- both partician tools -- you can modify the disk.

Another thing I don't actually like (though I use them) is that Live CDs often use the swap partician on your hard drive.  If it for example mis-recognized such a partitian I suppose that something bad could have happened.

And I'll close with a little personal story.  I was using my wifes computer once to boot a Live CD (not a Ubuntu CD -- but one that shall remain nameless), and it basically erased her disk.  This was not intended -- but there was a bug which I hope was later resolved which caused the problem.

My only point -- things can happen and one should always backup their system.

That said -- probably the best thing you can do is to figure out where you are and what's recoverable.  It may be simple or hard depending.  

In my wifes case we had a backup -- but one that was older than one would like and I had to do a block by block recovery of a few specific files to supplement the old backup.  I still have the disk image around thinking I might some day do a better recovery.

Rob

---

