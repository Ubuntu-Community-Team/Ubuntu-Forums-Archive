---
title: "How to get headphones sound working on iMac 7,1"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by oneiric on 2009-04-20
I installed Ubuntu 8.10 on an iMac 7,1, aluminum 20" computer, but sound isn't working through the headphones.  Over the past few days, I have been googling for my codec: ALC889A, and my audio device:  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03), and my sound module: snd-hda-intel, but nothing has fixed the problem so far.  

There is a [known issue with snd-hda-intel on Macs]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), but when I did that ( added "rmmod snd-hda-intel" and "modprobe snd-hda-intel" to the end of /etc/rc.local file ), it shifted my screen to the left and didn't fix sound through headphones.  Also I have tried various options adding to the last line of the /etc/modprobe.d/alsa-base file (but none of these was successful)

options snd-hda-intel model=imac24
options snd-hda-intel model=laptop
options snd-hda-intel model=macpro
options snd-hda-intel model=auto

Typing in to the terminal:
```
aplay -l
```

returns:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


When i type
```
alsamixer
```

All channels ("Master", "PCM", "IEC958" and IEC958 D") are unmuted.


Typing
```
cat /proc/asound/version
```

returns
Advanced Linux Sound Architecture Driver Version 1.0.19.
Compiled on Apr 15 2009 for kernel 2.6.27-11-generic (SMP).



 Sound IS working partially because it comes out of the computer speakers, but I really need the headphones to work.  When I plug in the headphones, sound continues to play out of the computer, and the sound quality is very poor.

Can someone point me in the right direction?  I'm sure its just a simple thing that I'm missing.

---

### Post by oneiric on 2009-04-20
Problem solved !!  I just got sound through the headphones after I restarted the computer, with no options added to the end of "/etc/modprobe.d/alsa-base"

---

