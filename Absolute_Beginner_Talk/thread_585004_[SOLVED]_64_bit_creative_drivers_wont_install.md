---
title: "[SOLVED] 64 bit creative drivers wont install"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2007-10-21
I just installed 7.10 64 bit today. The only thing that doesn't work so far is my sound card. Its a creative x-fi extreme music. I got the 64 bit driver from a website i found in another thread. When i try to run it it says "this is for 64 bit os only"....Can anyone help me? Thanks...

---

### Post by Maestro23 on 2007-10-21
Got a link to the download site?

---

### Post by Daveth on 2007-10-21
I guess he means this

[http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)

---

### Post by e1ektrob0y on 2007-10-21
> **Daveth said:**
> I guess he means this

[http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)
Yep, thats the one.

---

### Post by Daveth on 2007-10-21
you have read this bit of that page I guess?

"This download**_ is a beta driver _**providing Linux® 64-bit OS support for Creative Sound Blaster® X-Fi&#8482; series audio devices. For more details, read the rest of this web release note.

Take note of the following:
THIS IS AN UNSUPPORTED BETA DRIVER. There is no technical support for this driver.
We recommend that only experienced users install this driver. Do not install this driver on a system used to perform critical tasks.
Your feedback is a valuable part of our development process. To submit feedback on this driver, visit the Sound Blaster X-Fi Linux Beta Driver Feedback Program.

This download is intended for the following audio devices only:
Creative Sound Blaster X-Fi Elite Pro 
Creative Sound Blaster X-Fi Platinum
Creative Sound Blaster X-Fi Fatal1ty®
Creative Sound Blaster X-Fi XtremeGamer
Creative Sound Blaster X-Fi XtremeMusic

Current release features:
ALSA PCM Playback
ALSA MIDI Playback
ALSA Synth
ALSA Record
ALSA Mixer

Known issues:
This driver source will not compile with GCC version 4 and above.
S/PDIF passthrough is not supported in this driver release.
External I/O modules are not supported in this driver release.
Applications from the original Sound Blaster X-Fi Installation CD will not work with this driver.

Requirements:
Linux x86_64 OS
Creative Sound Blaster X-Fi audio devices listed above.

Notes:
To install the driver, do the following: 
Download the XFiDrv_Linux_US-1.04.tar.gz package onto your local hard disk.
Double-click the downloaded package to unpack its contents.
Read the README file and follow the instructions."

---

### Post by Maestro23 on 2007-10-21
Getting ready to ask/ post the same thing Daveth.  Just got done reading that.

---

### Post by jhpope on 2007-10-21
pretty sure i got the 64bit gusty and i get the same message...how do you check if you're running the 32 or 64 bit version?

---

### Post by Maestro23 on 2007-10-21
> **jhpope said:**
> pretty sure i got the 64bit gusty and i get the same message...how do you check if you're running the 32 or 64 bit version?

In terminal:

> uname -a

Should see something like the following:

> Linux xxxx 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 **x86_64** GNU/Linux

---

### Post by e1ektrob0y on 2007-10-21
Well, i guess the problem is the drivers is just not ready...[http://ubuntuforums.org/showthread.php?t=571656&highlight=creative]("http://ubuntuforums.org/showthread.php?t=571656&highlight=creative")
so, i'm gonna switch to on-board sound and see if that works...

---

### Post by e1ektrob0y on 2007-10-21
Onboard audio works woot! Guess that will have to do for now:D

---

### Post by Maestro23 on 2007-10-21
> **e1ektrob0y said:**
> Onboard audio works woot! Guess that will have to do for now:D

Good deal man.  Just keep you eye on that driver when it becomes more stable.

Don't forget to mark this thread SOLVED using the the Thread Tools.

---

