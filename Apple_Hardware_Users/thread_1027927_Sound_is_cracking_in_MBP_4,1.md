---
title: "Sound is cracking in MBP 4,1"
date: 2009-01-01
forum: Apple Hardware Users
---

### Post by lat2005 on 2009-01-01
Hello,

I got most everything running on my MBP 4,1 with Ubuntu 8.10 (Intrepid) and triple boot of Win XP and OS X.

However, the sound is a problem.
Right now when I first log in, the ubuntu startup sound sounds as a high frequency crackling noise.

When I go to the sound settings in ubuntu and I test 
HDA Intel ALC885 Analog (OSS) I get the correct nice tone. 
MP3s sound fine in Totem , but youtube has all the crackling noise.
In youtube I use the adobe supplied player as Gnash used up a lot of CPU power and really caused heating.

I also have the    options snd_hda_intel model=mbp3
in  /etc/modprobe.d/options

Is there any solution to this? 

Thank you

---

### Post by hyperboloid on 2009-01-02
I had some problems with sound also at one point, and I managed to solve it by tuning in to an internet radio station (so that something was constantly playing) and then opening up the Volume Control tool (right click on the volume icon at the top of your desktop) and playing with the settings until things sounded decent. This took a while, but worked in the end. It turned out that I needed to put one of the controls at 70% or so to avoid some sort of awful feedback that caused a squealing noise.

---

### Post by cyberdork33 on 2009-01-02
> **lat2005 said:**
> When I go to the sound settings in ubuntu and I test 
HDA Intel ALC885 Analog (OSS) I get the correct nice tone.

Though it is working, you should not use the OSS interface, it is just there for legacy purposes. You want to get the ALSA interface working properly.

---

