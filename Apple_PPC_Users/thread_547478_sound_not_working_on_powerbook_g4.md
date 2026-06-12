---
title: "sound not working on powerbook g4"
date: 2007-09-10
forum: Apple PPC Users
---

### Post by wickstopher on 2007-09-10
I recently installed Kubuntu 7.04 on a G4 PowerBook, and have not been able to figure out how to get sound working.  The KMix applet in the notification area (or whatever it may be called in KDE) has a red circle with a white x through it on top, and when the mouse hover over it, it says "Mixer cannot be found."  Also of note is that, when attempting to start Amarok, I get the window for Amarok, but It never really gets into the software.  It just hangs, and I end up having to terminate the process.  This didn't happen on the LiveCD (although I also wasn't getting sound on the LiveCD), and this happened both before and after I upgraded the Kernel to 2.6.20-16.

The following is from KInfoCenter > Sound:

> 
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux ubuntu 2.6.20-16-powerpc #3 Thu Aug 30 23:43:24 UTC 2007 ppc
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG


I'm hoping that this is enough information...I'm at a bit of a loss as to how to get sound working.  Thanks very much!

---

### Post by lisati on 2007-09-10
Sometimes installing "updates" to your system and then restarting can help after a "fresh" install. 

Look for a little notification triangle down the bottom right of your screen.

---

### Post by wickstopher on 2007-09-10
I did install all of the available updates (see new kernel).  Still no sound.

---

### Post by stmiller on 2007-09-10
Is this a Tibook? Or a newer Powerbook G4? Check out this info for a fix:

[https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e](https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e)

You may just have to add

snd-powermac

to /etc/modules

---

### Post by wickstopher on 2007-09-12
Thanks for the info.  It is indeed a TIBook, so I downloaded and installed an older kernel from edgy (2.6.17-11) and sound seems to be working fairly well.  I had to delete my newer kernels via adept, as I couldn't figure out how to make yaboot boot into the kernel of my choosing, but after that it seems to be working fine.  Currently listening to some mp3s in Amarok via my headphones.

---

### Post by wickstopher on 2007-09-14
update:

sound still cuts out a bit.  I haven't quite figured out why.  I don't use sound much on my laptop, but the only way I can seem to get it working again is by rebooting the system and it works again.

---

