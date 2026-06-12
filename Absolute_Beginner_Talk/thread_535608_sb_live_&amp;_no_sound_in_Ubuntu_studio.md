---
title: "sb live &amp; no sound in Ubuntu studio"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-26
I posted this in Multimedia but didn't get any answers so far so I figured I try here.


I'm dual booting with XP & Ubuntu Studio with an SB Live Card.
The card works fine in XP but I can't get any sound out of it in Linux.
I checked its on IRQ 10 by itself .
It shows up in /proc/asound/cards & in the alsa mixer.
I've unmuted things in the mixer to no avail.
I'm running a Dell with no onboard sound.
Anyone have any ideas?

---

### Post by alienexplorers on 2007-08-26
Can you type in terminal:
> lspci
and print the results here.
I am running the same card in a dual boot setup with Ubuntu and XP and sound works fine in both.

---

### Post by garyed on 2007-08-26
> **alienexplorers said:**
> Can you type in terminal:

and print the results here.
I am running the same card in a dual boot setup with Ubuntu and XP and sound works fine in both.

~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:09.0 Modem: Smart Link Ltd. Unknown device 8800 (rev 02)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

---

### Post by Hobo Joe on 2007-08-26
I have the same card, and i also had the same issue. Here's what I did to fix it:

First, run this command:
```

sudo asoundconf list

```
That will give you your list of sound cards. You will probalbly have two, and the SB Live! card will probably be called just Live.

If it is called Live, run this command:
```

sudo asoundconf set-default-card Live

```
If the name is something besides Live, change accordingly.

---

### Post by garyed on 2007-08-26
> **Hobo Joe said:**
> I have the same card, and i also had the same issue. Here's what I did to fix it:

First, run this command:
```

sudo asoundconf list

```
That will give you your list of sound cards. You will probalbly have two, and the SB Live! card will probably be called just Live.

If it is called Live, run this command:
```

sudo asoundconf set-default-card Live

```
If the name is something besides Live, change accordingly.

Thanks for the help but it didn't work.
It was called Live but it was the only one in the list.
Maybe I'm supposed to have something else in the list & that''s my problem.
If you wouldn't mind post your results of " asoundconf list " .
I'd like to see what yours says.

---

### Post by garyed on 2007-08-27
Once again I feel like an idiot.
It was in the alsa mixer, I had the wave & wave surround turned all the way down.
I never knew those settings existed because they were off the screen. 
I turned up everything on the screen, surround, synth, bass treble, PCM, Master etc. but I didn't know there was more. like "WAVE... etc.."
I thought it must be something very technical, at least for me.<g>
This link was what made me think there wasn't anything wrong with the card or drivers.

[http://www.alsa-project.org/main/index.php/SoundcardTesting](http://www.alsa-project.org/main/index.php/SoundcardTesting)

The surround test works even with the mixer turned down.

---

