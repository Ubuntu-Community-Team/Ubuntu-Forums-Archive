---
title: "strange audio problems on ppc powerbookG4"
date: 2008-10-21
forum: Apple Hardware Users
---

### Post by ieuph7 on 2008-10-21
So I've spent a good many hours pouring through the very helpful forums here, trying to get my audio to work properly.  I only ended up making things worse, and have now just reinstalled Ubuntu entirely.  This has emboldened me to actually ask for help.  I figured that folks who know ppc would be best equiped to help; if not feel free to move this thread to wherever it should go (multimedia, I would suppose)  Here's what's up:

I'm trying to run 8.04 Hardy on an old ppc PowerBookG4.  Perhaps this wasn't the wisest choice, but I previously had Ubuntu on a different computer and loved it.  If I fail to get this sound issue figured out, I may opt to switch over to Fedora, or possibly dual-boot.

The problem is that a few seconds into any audio or video, regardless of player (vlc, amarok, rhythmbox, movie player at least) the sound will simply cut out.  Depending on the player and type of media I'll get somewhere between 3 and 11 seconds of audio and then nothing.

If I test the audio, everything works fine.  The soundcard comes up, the ALSA drivers are ok (I think, at least I did whatever the big "sound problems" sticky said to do, and they seem to be ok), and I've tried everything recommended in the various "sound problems" stickies and faqs, both on this forum and a couple others. I'm willing to try things again, since I assume that I bungled something the first time.

Oh, and I've verified my iso, so that's not the problem.  System sounds work just fine.  Any suggestions would be appreciated.

---

### Post by tiresia on 2008-10-21
Do you think that your issue is related to this bug?
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

May be:
[http://forums.gentoo.org/viewtopic-t-548091-highlight-powerbook.html](http://forums.gentoo.org/viewtopic-t-548091-highlight-powerbook.html)

---

### Post by Concorde105 on 2008-10-21
> **ieuph7 said:**
> 
I'm trying to run 8.04 Hardy on an old ppc PowerBookG4


Maybe you could tell us the year, al or ti, screen size, ram, etc...
Those can make a difference. My 2005 12" dual-boot PowerBook works fine, with audio, but volume control only works in KDE/Kubuntu. The specs could be very helpful, or they might not matter, I don't know. But they might, so please post them.

Concorde105

---

### Post by ieuph7 on 2008-10-21
Apologies for not including that earlier.  It's a 15" 32-bit 2002 Titanium PowerBook G4 1GHz processor (Either Antimony or Ivory; I thought ivory at first since it doesn't seem to want to recognize blank dvds (just ejects them) though the "lshw" tool clued me in to the fact that it does actually have dvd-writing capability)   

I'll try those suggestions you folks helpfully suggested and let you know.

---

### Post by ieuph7 on 2008-10-21
Audio problem solved thanks to this post [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/comments/72]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/comments/72")

All I had to do was switch to the smp kernel/image.  Thanks so much for pointing me towards the solution...

---

### Post by ieuph7 on 2008-10-24
Ok, so now I have a new, but related problem.  Everything worked fine for two days, and then my headphones suddenly died.  All the rest of the sound works great.  I tried the workaround here ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957)) but didn't seem to have a "surround sound" option.  At least things are moving in a positive direction...

---

