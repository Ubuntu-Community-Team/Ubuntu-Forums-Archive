---
title: "What options do I have for installing Linux on a Macbook Pro 1,1 (Early 2006)"
date: 2016-04-19
forum: Apple Hardware Users
---

### Post by aceman67 on 2016-04-19
I picked up an old Macbook Pro from a friend on the cheap, and I was disappointed at just how little the thing is supported. The only modern browser that still works is Firefox (yuck, Chrome or nothing). The only thing I'll be using the OSX partition for is running Herolab (I play Pathfinder a lot)

I know that putting Linux on it will at least improve its performance, but I was wondering, what options do I have in terms of Linux (like Ubuntu), do I have? I would like the most recent I can install.

Are there any guides on how to get it going (I'm new to Macs in general, haven't used one since college over 12 years ago)?

I have the Macbook Pro 1,1 (Early 2006) currently running 10.6.8

---

### Post by Frogs Hair on 2016-04-19
Do you have any specs ? The ones I find indicate 1gb of ram and an Intel core Duo, so I be looking at Lubuntu unless the computer has more memory.

---

### Post by aceman67 on 2016-04-19
It has 2gb, Core Duo 2.16ghz, sorry about not putting it in the OP, It was in another room (I'm on my PC).

---

### Post by aceman67 on 2016-04-19
I managed to install Lubuntu and the only thing that doesn't work is the audio, I can't remember where, and my google-fu is failing me, but I read that the audio drivers are proprietary. Where would i find them?

---

### Post by mörgæs on 2016-04-20
Try installing Pulse Audio Volume Control with the command
```
sudo apt-get install pavucontrol

```
After that simply play around with the settings. Often the problem is that some level is by default set to 0.

---

### Post by aceman67 on 2016-04-20
A lot has happened since last night. I managed to get the sound working by adding to the following to the alsa-base.conf file

```

# My Mods
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=intel-mac-v1
```

While trying to get the mic to work, I screwed something up and my install became unbootable, so I wiped and installed Ubuntu 15.10 (32-bit), and that is working perfectly.

I got the iSight Camera working, but now for the life of me I can't figure out how to get the microphone to work. Every 'fix' I find on google tells me to edit the alsa-base.conf file or check if its muted under the alsamixer.

My issue is that the microphone just doesn't show up under any of it. 

This really sucks, because I use my laptop to communicate with my GF, and not having a working mic is bummer.

Thank you to those that helped or will help.

---

### Post by mörgæs on 2016-04-21
Have you tried this?
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

---

### Post by aceman67 on 2016-04-21
that page assumes that the device itself is selectable. For me, all I get is "Digital Input (S/PDIF)" as the default device, which is not the built-in microphone, which I assume is part of the isight camera (of which I have the video capture working).

---

