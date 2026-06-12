---
title: "PPC mac problems"
date: 2009-01-13
forum: Apple Hardware Users
---

### Post by deamon_knight on 2009-01-13
I'm installing 8.10 on two Macs. One is an iBook G4, i succeeded in installing with the alternate installer by using **modprobe ide-scsi**

However, while I can get to the desktop, colors are all fouled up and the display is nearly unreadable. The system reports an error along the lines that the display system cannot start, and prompts with a window and 3 radio buttons. Its very hard to read but the options appear to be "to restart the display system", "reboot the system", or "proceed to the desktop". Proceed to the desktop worked once but after a reboot I'm stuck at that windows with the same 3 options.

The Second machine is an iMac G4, and the alternate installer worked again, after **modprobe ide-scsi**. Everything looks good but I have no audio. The icon looks muted but reports it cannot start the sound system, it may be disabled or misconfigured.

Any advice on how I can fix these problems?

The oddest thing is that, on both systems, the 8.04 live Cds work normally,display and sound, etc., although no 8.10 live cds will load. So I have to ask, what are we getting in 8.10? This isn't a dig at anyone (I can't code myself), but support seems to be moving backwards in this case. Apple is no longer developing PPC systems, so there is no new hardware to be supported, am I missing out on any new features by going with 8.04? instead of 8.10? Later version of software in the repos perhaps?

All help is appreciated.

---

### Post by stream303 on 2009-01-14
> **deamon_knight said:**
> Any advice on how I can fix these problems?

I've seen this audio problem in 8.10 - fire up *alsamixer* in a terminal.  Use the left-right arrow keys to navigate through the channels, and make sure that the master or speakers arent muted (use M to toggle muting on and off).  Also be sure that your PCM is around 75 percent or so.  Use B to balance the channels if they are different.  Hit ESC when done.  Now see if the gui components work ok.  You may have to remove PulseAudio, but usually alsamixer can unwedge things.

> The oddest thing is that, on both systems, the 8.04 live Cds work normally,display and sound, etc., although no 8.10 live cds will load.
.
So I have to ask, what are we getting in 8.10? This isn't a dig at anyone (I can't code myself), but support seems to be moving backwards in this case.

Check the release notes about 8.10 and see if anything new is absolutely vital.  At this stage, unless you want to fool around with getting it all working, I'd say stick to Hardy 8.04.

If you still want to use 8.10, install 8.04 anyway as a diagnostic, and grab the /etc/X11/xorg.conf from that install and see if it will work in 8.10.  

A big problem is that xorg is trying to make it easier by being smarter about detecting video card capabilities, and the resulting xorg.conf files are getting shorter - even *nothing* in Intrepid's xorg.conf.  This is generally seen as a good thing for most users (aside from ppc) as they want to move away from the 90's style of end-user configuration with manual editing.

Unfortunately, in some cases that's exactly what we have to do since the Apple hardware wasn't designed to be linux-friendly, so the normal probing techniques during installation sometimes fail or result in bad values.  At least with the older releases, xorg.conf would be populated with data, even if wrong, but that allowed those not experienced with xorg to kind of wing-it by changing values around.  Now with a nearly empty, or absolutely empty xorg.conf, it makes that chore nearly impossible for those not prepared to dig into it.

> Apple is no longer developing PPC systems, so there is no new hardware to be supported, am I missing out on any new features by going with 8.04? instead of 8.10? Later version of software in the repos perhaps?

For now, I'd stick with what is working - yes, there are later releases of software with 8.10, but is it vital to your operations?  Consider that 8.04 is less than a year old, but my old Tiger install is *years* old now, but entirely usable.  8.04 should be no problem, especially because it is going to get security updates for a long time.  (although there are no guarantees for community-supported versions like ours, so LTS is not to be relied upon absolutely.)

There's no shame in running 8.04 !

---

### Post by mkvnmtr on 2009-01-14
On my G4 Ibook I am still running 8.04 and I like it. I read about the problems that ppc people were having and just decided to wait. I really don't find that I am missing anything that I need.

---

### Post by deamon_knight on 2009-01-14
Yea, I ran alsamixer and it reported no mixer elms found.

I think I may just go back to 8.04. I'm using 8.10 on my non PCC units and was looking for uniformity. Anyone know if OpenOffice 3.0 is available for 8.04 on PPC?

---

### Post by wnagourney on 2009-01-14
I very recently installed 8.10 on an 800 MHz iBook G4 (12") and had no video problems of any sort. I used the alternate install DVD (it didn't fit on any of the CDs I had) and did the "modprobe" thing to get the installer to work. To get any video at all, I needed to type "Linux "video=ofonly"" at the second Yaboot prompt, but I assume you have done that. 

I was even pleased (and surprised) to get some 2D video acceleration, which I wasn't expecting. Scrolling, however, is painfully sluggish.

Hope this helps.

Warren Nagourney

---

### Post by roym4 on 2009-01-14
[QUOTE=deamon_knight;6548352]Yea, I ran alsamixer and it reported no mixer elms found.[QUOTE]


Try adding snd-powermac to the /etc/modules file and see if that doesn't help with your sound problem.

If addiing snd=powermac doesn't fix the sound, you may also need to add these lines to your /etc/rc.local file:
amixer sset 'PC Speaker' on
amixer sset 'Auto Mute' off

---

### Post by deamon_knight on 2009-01-15
Thanks for the replies but I've decided to go back to 8.04. Typing from the machine in question right now.

---

### Post by deamon_knight on 2009-01-15
Darn, its been a while since I installed on PPC system and I have forgotten how to get Flash to work, e.g. Youtube. I've installed Ubuntu restricted extras, Gnash & VLC. I though that was all I had to do last time, but no luck.

---

