---
title: "Input Not Supported"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by The Grand Falloon on 2007-01-20
Yar... I don't know what I'm doin'.

OK, bear in mind I have absolutely no experience with Linux.  The only time I've used Linux was playing Doom on a friend's computer and I managed to crash the whole damn thing.  Anyway, I figured I would give the Live CD thing a shot.  The CD starts to run, and I select "Run or Install Ubuntu."  I get a little splash screen, then the computer starts thinking, while displaying "Input not Supported."  Basically my LCD monitor doesn't know what the hell's going on.  I'm pretty sure I could go dig out my old CRT, but I really don't want to.  Is there any other way around this?  I don't see how I can change any sort of options since I'm just trying to boot from a  read-only CD.

Uh, and my son wants me to put this on here...  :mad: 
There you have it.  I guess I'm angry.

---

### Post by je1117 on 2007-01-20
How about trying the alternate install iso?

[i386]("http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso")
[AMD64]("http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-amd64.iso")

---

### Post by taurus on 2007-01-20
Why not use the alternate CD to install Ubuntu on your machine.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by The Grand Falloon on 2007-01-21
er... hm.
See,  was thinking of the Live CD so that i wouldn't have to make any changes to the ol' box just yet.  Trial runs and whatnot.  I'm not quite ready to ditch Windows or reformat or anything, or do a partition...

What does an Ubuntu installation do to one's PC?

---

### Post by taurus on 2007-01-21
Which version of LiveCD, Dapper or Edgy, did you try?  And what's the spec of your machine?

---

### Post by freebeer on 2007-01-21
Are you sure that it's the LCD that's giving it fits?  The LCD monitor is an output device, and the error message seems to imply that it's calving on an input device - the touchpad, perhaps?  I'm certainly no expert here - I just wanted to point out that you might be chasing the wrong path to diagnose the problem.

---

### Post by MasterOfDisaster on 2007-01-21
Well, the installation cd means that you will either be able to boot Ubuntu and Windows, or just Ubuntu.

Do you know the specs for your monitor?  I have this problem with my LCD monitor, and have to manually edit the xorg.conf.  If you post back with the specs it would be appreciated.

---

### Post by freebeer on 2007-01-21
> **The Grand Falloon said:**
> er... hm.
What does an Ubuntu installation do to one's PC?

Just running the live CD doesn't do anything to your machine.  It will create an Install Icon on your Ubuntu Desktop, but that's all held in memory.  It's not until you go through the Install procedure that it will do anything to your machine.  It's well behaved that way.  :D

---

### Post by The Grand Falloon on 2007-01-21
I'm running the Edgy EFT (6.10).

My system: 1.5 GHz AMD Athlon XP
1.5 Gigs of RAM
nVidia GeForce 6600
Cheap Rosewill LCD monitor.

I suppose I should be suspecting a video card issue rather than a monitor issue.  It's just that the only time I've gotten the Input Not Supported message was when I only had the digital video cable hooked up and tried to run Battlefield 2.  Apparently BF2 has to run on the analog cable or something, I don't know.

So I reckon I should just try the 6.06 release?

---

### Post by freebeer on 2007-01-21
I haven't tried 6.10 and I really don't know much about it.  You could try 6.06 - it certainly won't hurt and it may work just fine for you.

---

### Post by The Grand Falloon on 2007-01-21
Sweet.  It's working.  Now to explore this... Leen-ox...

thanks everyone :)

---

### Post by freebeer on 2007-01-21
Great!  Happy 'pooting!

---

