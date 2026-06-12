---
title: "Macbook second screen resolution"
date: 2009-12-03
forum: Apple Hardware Users
---

### Post by kjhermans on 2009-12-03
Hi.  This is probably familiar, because I've seen similar (but unfortunately, never identical) issues posted in other places, but I was wondering if there was an obvious fix.

I have ubuntu karmic koala installed as a second partition on an aluminium simple macbook from may 2009.  5,1 in other words.  I mean to move away from Mac OS altogether, but not if I can't fix two issues.  The first issue is not so much of a show-stopper: the audio won't come out of the earphone plug, even if you run alsamixer and turn it all the way up to eleven.  I don't even see two output devices in gnome-volume-control.  It's just not there.

The second one is a bit more grave: I also have a second screen, a Dell 2007FT that Mac OS supports at 1600x1200, however, the ubuntu Nvidia 177- and 185-drivers will give me very colourful vertical stripes on it, and the newest, hottest downloaded-from-nvidia-itself driver will only give me 1280x1024, max.  I tried forcing the issue by editing the xorg.conf file, but that just gave me a black screen.  I tried the mactel-xorg.confs but they don't work (X even 'panics' during boot when you do that).  Twin-view or seperate X-screen doesn't make a difference.  Changing screens for other screens (also DELLs, but different types) doesn't make a difference.  I've scoured the Xorg.log files and they don't provide /any/ clue.  I feel like I've tried everything.  The only thing I can think of that could be a problem still is the mini-DVI to VGA-adapter that I ordered with this Mac (someone said I should try a mini-DVI to proper DVI instead).  But then - that's the same adapter I use under Mac OS and it works just fine.  I don't see how this could help.  Especially if the issue can't be forced.  O, and before anyone thinks of it: yes, I've also (in one of my attempts) set the horizontal and vertical sync rates to the exact spec of the monitor.

So, is there anyone that could provide me with some info regarding solutions or ways to find out what's wrong ?  Cheers.

---

### Post by ercoppa on 2009-12-03
> ottest downloaded-from-nvidia-itself driver will only give me 1280x1024
Newer nvidia binary driver introduces a check on external display, disable with:
```
Option         "ModeValidation" "NoExtendedGPUCapabilitiesCheck"
```
In device section.

Greets.

---

### Post by kjhermans on 2009-12-06
Tried it.  With and without forcing the resolution.  It doesn't work, sorry.

---

