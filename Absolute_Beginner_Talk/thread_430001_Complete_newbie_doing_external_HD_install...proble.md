---
title: "Complete newbie doing external HD install...problems..."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by TuxBobble on 2007-05-01
Hey everyone, let me preface this by saying that I've barely scratched the surface of Linux.  I've run a Knoppix live CD, and as of a couple of days ago decided to try the Ubuntu live CD.  Now that I have an external hard drive, I want to try booting 7.04 from it.

I first used the Live CD to install, but couldn't get GRUB to install properly, so I tried the alternate CD since I was told it worked better with external drives.  This worked better, as now the GRUB prompt loads when the external drive is plugged in and turned on.

However, now I'm faced with another problem.  Regardless of what I select at the GRUB prompt, nothing will load.  It shows three Ubuntu choices--regular, recovery mode, and memtest.  And it shows Windows XP, which is on my internal drive.  But none of them load properly.  

When I choose regular Ubuntu, it begins to load, but as soon as the Ubuntu logo screen appears, the computer stops.  There is no further loading from the external drive, (where it is installed) according to its status LED.  The orange bar doesn't even start to move after the first piece of it appears.

Choosing recovery mode Ubuntu, I get the message:

"Alert! /dev/hda1 does not exist.  Dropping to a shell."
and then 
"/bin/sh: can't access tty; job control turned off
(initramfs)"

If I choose the Windows installation, it just recycles the grub prompt.

I've tried pressing 'e' on the grub loader prompt to edit lines of script, but nothing seems to do the trick.
By default the first line of both the Ubuntu boot options is set to (hd0,0) and if I try (hd1,0) it won't even pass the grub loader when I attempt to boot.

And on the Windows one it says the same thing, I think.  I tried changing it, I think to (hd1,0), but when I boot it says "Starting up..." but never actually leaves this screen...

If I unplug the hard drive or turn it off before turning the computer on, it boots directly to Windows XP, just like I wanted.  However, I can't figure out how to make GRUB boot the system properly.  If anyone knows anything that could help me, out, I'd greatly appreciate it.  I only have a few weeks left with this computer, and I'd prefer not doing this again at home but having it capable of running off the hard drive when I get there, ideally.

Thank you very much, and I apologize for the very lengthy post.  I just wanted to be as clear as possible about the issue so that someone might be able to help.

---

### Post by zvacet on 2007-05-02
I don´t if this will help you 

[http://ubuntuforums.org/showthread.php?t=308027&highlight=external+drive]("http://ubuntuforums.org/showthread.php?t=308027&highlight=external+drive")

---

### Post by TuxBobble on 2008-07-07
Unfortunately that's not quite what I'm looking for.  If anyone has any ideas to help me out with this one, please fill me in.

---

