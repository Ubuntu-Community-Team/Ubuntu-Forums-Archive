---
title: "the Brag"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by jaggedaloc on 2005-10-09
At 3:30 am last night I for the first time installed Linux on something besides my iPod.  I chose to keep winnieXP for now (or, rather, my beautiful wife so chose), so now I have Ubuntu on a tee-tiny partition on a 20 gig hard drive.  With the exception of one glitch (that is, no sound?!?), EVERYTHING seems so much tighter, faster than XP.

I couldn't be happier (unless I had sound, I suppose.  Anyone direct me on fixing this, hmm?).  I think I might cry.

---

### Post by XDevHald on 2005-10-09
[QUOTE=jaggedaloc]At 3:30 am last night I for the first time installed Linux on something besides my iPod.  I chose to keep winnieXP for now (or, rather, my beautiful wife so chose), so now I have Ubuntu on a tee-tiny partition on a 20 gig hard drive.  With the exception of one glitch (that is, no sound?!?), EVERYTHING seems so much tighter, faster than XP.

I couldn't be happier (unless I had sound, I suppose.  Anyone direct me on fixing this, hmm?).  I think I might cry.[/QUOTE]
How to Hear Multiple Sounds At One: 
[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)

Getting Alsa, OSD, ESD to work and other sound settings as well:
[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=Sounds](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=Sounds)

---

### Post by Lord Illidan on 2005-10-09
We can't help if we don't know the make and model of your sound card...

---

### Post by Wolki on 2005-10-09
[QUOTE=jaggedaloc]I couldn't be happier (unless I had sound, I suppose.  Anyone direct me on fixing this, hmm?).  I think I might cry.[/QUOTE]

One thing that sometimes happens is that the sound is muted. Run "alsamixer" and make sure "master" and "pcm" have values > 0.

---

### Post by jaggedaloc on 2005-10-09
[QUOTE=Lord Illidan]We can't help if we don't know the make and model of your sound card...[/QUOTE]
Sorry.  Don't know why I solicited help so soon...  am still plugging away at understanding ALL THIS.
I evidently, according to windows, have a Conexant Riptide Audio Device, which, unless I miss my guess, was origional equipment on the HP Pavillion Intel Pentium III.  But I am loathe to crack the box and read serial numbers, which almost assures that I shall have to do so.

Am also having simlar problems reading cd's and dvd's off of an HP CD-Writer = 8100 and  an Hitachi DVD-ROM GD-2500.

But, hey, Windows never could give me the screen resolution I'm running with now, so, there's that.

---

### Post by dcraven on 2005-10-09
No need to crack the box and read serial numbers. The "lspci" command will list the actual chipset used for playing audio.

Cheers,
~djc

---

### Post by erikpiper on 2005-10-10
When I had no sound in games, I did the following: 
(At the top left menu in Gnome) Go to system- Preferences- Sound
Then deselect "Enable sound server at startup" 

If that doesn't help, reselect it!

---

### Post by jaggedaloc on 2005-10-10
[QUOTE=dcraven]No need to crack the box and read serial numbers. The "lspci" command will list the actual chipset used for playing audio.[/QUOTE]

I have, evidently, a Rockwell International PCI Audio Controller.

I notice during my boot that there is a claim that area four (or something) of the pci cannot be initialized.  I think, initialized.  Maybe addressed.  It's all so fast.

Curiouser and curiouser.

---

### Post by UbuWu on 2005-10-10
Upgrading to breezy next week will solve a lot of sound problems (no garantees though ;) )

---

### Post by Wolki on 2005-10-10
[QUOTE=jaggedaloc]I have, evidently, a Rockwell International PCI Audio Controller.

I notice during my boot that there is a claim that area four (or something) of the pci cannot be initialized.  I think, initialized.  Maybe addressed.  It's all so fast.

Curiouser and curiouser.[/QUOTE]

So I did some looking around....

Generally, Rockwell/Conexant is not a linux-friendly vendor. OSS did support your card. I do not know, however, whether this is in the free implementation of OSS or in the one you have to buy. Anyway, OSS is today (since Kernel 2.6) being replaced by a new System called ALSA. Today there is no support for you card in ALSA. It looks like there are people working on it and something related to your card was checked into the source code recently, but this is likely not in Ubuntu yet. You could try Breezy regardless, maybe I'm wrong. You have a chance that it will be supported in Dapper, which will be released April next year.
If you can't replace the sound card, you seem to be out of luck. SuSE's Professional Editions - the non-free ones - used to include the full OSS package, maybe the card will work with one of these; I do not know whether they still include it.

---

### Post by jaggedaloc on 2005-10-11
[QUOTE=Wolki]If you can't replace the sound card, you seem to be out of luck.[/QUOTE]

So a trip to the flea market might help me convince my beautiful wife to switch to Linux?

Sign me up!

What should I best (or second best, or whatever) look for in bargin bins?

---

### Post by Wolki on 2005-10-11
[QUOTE=jaggedaloc]So a trip to the flea market might help me convince my beautiful wife to switch to Linux?

Sign me up!

What should I best (or second best, or whatever) look for in bargin bins?[/QUOTE]

[http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix) has a list of all cards supported by alsa. Each one that is not marked should work without problms out of the box.

When I switched to linux, I tried very hard to get my soundcard to work without success... then while visiting my parents grabbed a leftover one (lucky there was one that claimed linux support^^; ), plugged it in, and didn't have any problems since.

---

### Post by jaggedaloc on 2005-10-12
[QUOTE=Wolki][http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix) has a list of all cards supported by alsa. Each one that is not marked should work without problms out of the box.[/QUOTE]

You're so cool...  Tanx.

---

