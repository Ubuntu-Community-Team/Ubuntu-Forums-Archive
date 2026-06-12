---
title: "My sound has gone - no connection to sound server?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Kouki on 2006-08-30
Hi, I installed Ubuntu on both my PC and my Dads PC, at first, both worked absolutely perfectly.  I've learnt how to install programs and change the grub boot order which I'm quite proud about!

Unfortunately, the other day, the sound on my PC stopped working and I have no idea how.  Basically, now, if I try to play music from a CD rhythm box music player gives me the following error: 

"Error playing CD.

Reason: Could not establish connection to sound server"

:confused: 

Very strange I thought considering I'd not touched sound settings.  Right I thought, it could be the update I downloaded, so I thought, its only been on my pc for a day, I'll reformat the disk and install it again, then my sound should come back.  I was wrong, exactly the same message is displayed after the install.

I thought initially it might be that Ubuntu doesn't recognise my onboard soundcard, but then I thought no, it can't be that because it used to work.  All the same, my motherboard/soundcard set up is this:

Abit AV8-3RD Eye Skt 939 K8t800pro 8xAGP ATX Gigabit LAN, SATA150 RAID, IEEE1394, 6ch Audio, ìGuru USB2.0

Really need some pointers, I could fix it easily in Windows as I've grown up with it, but have only been using linux for about 4 days now so I'm completely stuck.

I should add that its not just sound when trying to play CD's thats affected, it's any sound, I don't even get the startup noise anymore.

---

### Post by Kouki on 2006-08-30
:mrgreen: Fixed it!

It turned out Ubunto had changed my soundcard to something random.  I went into system/preferences/sound and noticed that Default sound card was set to SAA7134 :confused:   I knew my soundcard was a VIA so clicked to change it and the other option was VIA 8237, that looked more like it, so I set that as my default card and the sound worked.

Very strange, considering I'd never been in that window before.

Ah well, I'm happy now :)

---

### Post by danielph on 2006-09-01
This can happen when plug in a USB device such as a webcam. I happened to me, I plugged a webcam in and it defaulted to that as it's sound output. I am not sure how Linux was going to get sound to come out of my webcam, I would have been impressed. Your fix worked for me too, thanks

---

### Post by total wormage on 2006-10-20
ubuntu seems to like doing things randomly with VIA soundcards :o

my kubuntu edgy chose a primary soundcard at random while booting, so i had to unplug and plug my cables everytime i rebooted :p

[fixed now though]("http://ubuntuforums.org/showthread.php?t=274063&")

---

