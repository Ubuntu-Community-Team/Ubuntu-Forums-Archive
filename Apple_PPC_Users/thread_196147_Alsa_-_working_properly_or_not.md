---
title: "Alsa - working properly or not?"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by Ububurns on 2006-06-13
Does ALSA work **properly** on PPC or not?

I can run jackd, and it will work, on a PC.
Using the same sound card, I receive "Cannot load driver module ALSA" - failure.

I can run Hydrogen and get sound through ALSA, on a PC.
Using the same sound card, I get static, on my Mac.

This has been tested with both Breezy and Dapper.  In both cases no modification was made to configuration files.

Why should one architecture work, and the other not?

---

### Post by BoneKracker on 2006-06-20
Different bus architectures?

---

### Post by Ububurns on 2006-06-27
I thought that at first - but have been informed that only video cards are incompatible switched between Mac and PC.

Also, if it was a purely architectural reason - why would the sound card be able to play music, and audio from movies?

Thus I concluded it might be a problem with ALSA.  Any other ideas?

---

### Post by BoneKracker on 2006-06-27
Well, ALSA does work on ppc.  As configured in Dapper, it works great on my G4.  I've had some challenges with it in the past, though (it took me several days to work through issues with it in in a self-configured Gentoo/Gnome build).  My only experience with it has revolved around issues with kernel configuration/modules that are required for the bus and cards used.  

So, if I understand your situation, you are using a standard Ubuntu kernel for mac/ppc, but you are using a card that isn't commonly found in a Mac.  If that's the case, it could very well be that the kernel does not have support for the device.  

You may need to add a kernel module (driver) or configure and compile the kernel yourself.  I suspect the latter would be required, because the mac's I'm familiar with had built-in sound, so you may have to disable that to avoid conflicts.

---

### Post by Ububurns on 2006-06-28
Yes, ALSA is working (partly) - I can play and record sound through aplay and arecord, and use various applications that use ALSA.

The sound card I use, taken from a PC, is an SBLive (emu10k1 - well supported, I believe).  The G4 has no input for recording - so the sound card was necessary.

However ALSA support seems to run out there, and there are several applications that are unable to use it, find it etc.  These same applications work fine on a PC, using the same setup.

BoneKracker - would you please be able to try running jackd on your Mac?  In over a year, I haven't heard one person say that they have been able to run it.  It would help clear up a few queries I have!

---

### Post by BoneKracker on 2006-06-29
You want me install unsupported, experimental software that I have no need for and which is unlikely to run on my computer?

Let me think it over.  Okay, I've thought it over... I think I'll pass.

---

### Post by Ububurns on 2006-07-04
The package "jackd" has been "officially supported" by Warty, Hoary and Breezy, with its package found in the ir respective main distribution repositories.  There should be little fear that this is an "experimental" program.

I can fully understand that you may have no need for the software.  However, with the installation process only consisting of half a dozen clicks, and a measly 100kb download, I thought it may not have been such a big deal.

And yes, it is possible that jackd will not run on your computer.  Coincidentally, that was the purpose of my request.

:)

Nevertheless, if that is your final decision, I am able to cope.

Is anyone else able to help out by trying to run jackd on a Mac?

---

### Post by onehotcutey on 2006-07-05
I have jackd running on my TiBook, 1ghz.  Well at least it starts and sees connections.  I have not worked with to change outputs and inputs.

jackd -d alsa -d hw:0

---

### Post by Ububurns on 2006-07-05
Thankyou so much for that, onehotcutey! :)

---

