---
title: "Foxconn Nettop - can't mute internal speaker in Natty"
date: 2011-06-10
forum: Any Other OS
---

### Post by imperfect10 on 2011-06-10
Hi,
I have a Foxconn nT-330i nettop and just installed Linux Mint 11 (based on Ubuntu Natty), over a previous installation of Element OS (based on Ubuntu Karmic).

Everything worked just fine, except for the sound.
The machine is connected through the analog output to external speakers, but it also has an inner speaker.

In Karmic, connecting the external analog audio cable muted the internal speaker.
In Natty, the internal speaker is on, and there seems to be no way to turn it off without turning off the external analog audio.

The internal speaker is very scratchy and annoying at higher volumes, so I'd like to turn it off just like in Karmic.

I first suspected this was due to the upgrade, however I found this bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/637520](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/637520)

And also this discussion here:

[http://forums.whirlpool.net.au/archive/1551455](http://forums.whirlpool.net.au/archive/1551455)

So this seems to be some problem with the ALSA driver(s), as far as I understand that last thread.

Has anyone else managed to solve this?

I guess not too many people ran into it since everyone is using HDMI output these days...

There is a workaround mentioned in those links: connecting earphones to the jack in the front panel seems to mute the inner speaker and all is good.  However, this is annoying - why did the ability to mute the inner speaker suddenly disappear?

I uploaded the result of Alsa-Info here:
[http://www.alsa-project.org/db/?f=1d88f566263407c6397295a2b8ca4cb0ef45eb80](http://www.alsa-project.org/db/?f=1d88f566263407c6397295a2b8ca4cb0ef45eb80)

Also, should I open a bug for the alsa people?  Or is that bug I found in Ubuntu launchpad enough?

---

### Post by wolfen69 on 2011-06-10
Check your BIOS settings to turn off internal speaker. Also, did you know Karmic is no longer officially supported?

---

### Post by imperfect10 on 2011-06-11
> **wolfen69 said:**
> Check your BIOS settings to turn off internal speaker. Also, did you know Karmic is no longer officially supported?

I checked, there isn't any BIOS option to turn off the internal speaker.

Also, I know Karmic is no longer supported -that's the reason I upgraded to Natty in the firs place (well, to Mint 11 actually).  Like I said, everything was cool except for this one bug.

---

### Post by kerry_s on 2011-06-11
run "alsamixer" in terminal & mute the 1 you don't want.

---

### Post by Perfect Storm on 2011-06-11
Moved to Other OS/Distro Talk.

---

### Post by imperfect10 on 2011-06-14
I've tried muting all the inputs in alsamixer, one by one, but it didn't work - either both the external audio and the internal speaker are muted, or both work.

I've read a bit more about pulseaudio and saw that it's known as problematic.  Perhaps uninstalling it will help?   I saw this suggested by some people.

I've also posted this question in the Linux Mint board.

---

### Post by kerry_s on 2011-06-14
my bag, looks like something changed while i was away.

so now mute, mutes all sound. which is stupid.
now you have to lower the volume all the way down on the 1 you want. so on my foxconn nettop, to turn off the desktop speakers, i have to lower pcm all the way down, so sound only comes out my headphones instead of both.

i use gnome-alsamixer, if you want something better than term.

---

### Post by jackashe on 2011-08-14
I had this same problem with natty on my system76 Koala box.  prior to natty I could see the different channels by going into sound settings.  Thanks so much for enlightening me to alsamixer and gnome-alsamixer!

---

