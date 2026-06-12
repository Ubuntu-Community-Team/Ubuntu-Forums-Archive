---
title: "No sound on fiesty.."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by christianj on 2007-05-08
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 ES [SB0160]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 ES [SB0160]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 ES [SB0160]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

As far as I can tell, it recognizes my card but it just will not play.
I run a dual boot system and the sound is fine on the other operating system but not on Fiesty.

I have un-installed and re-installed as per instruction on sound issues but all to no avail.

Originally I had sound when I first installed fiesty but not now...

Any ideas ?

Cheers...

---

### Post by ctsdownloads on 2007-05-08
Not making any promises, but assuming the card is truly supported, this may give you some options to get things working.

[http://ubuntuforums.org/showpost.php?p=1954446&postcount=10](http://ubuntuforums.org/showpost.php?p=1954446&postcount=10)

Again, assuming this newer Creative card jives (and some of the [newer ones]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix") do not), you can locate the card and even create executables to switch between your sound card and a USB headset should you need to.

But for now, do a asoundconf list and then follow the rest of the command line directions in the link. :)

---

### Post by Ianman on 2007-05-08
This is the solution I found for myself. I also have an audigy card:

" I opened the Alsa mixer and umuted everything as mentioned here:
[https://help.ubuntu.com/community/De...gSoundProblems](https://help.ubuntu.com/community/De...gSoundProblems)

I then switched to the Switches tab and noticed an option:
Audigy Analog/Digital Output Jack

In my case it was enabled. As soon as I disabled this option sound started to work! "

Hope it helps!

---

### Post by christianj on 2007-05-08
No luck...

-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:09.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)
christianj@christianj-desktop:~$ asoundconf list
Names of available sound cards:
Audigy
christianj@christianj-desktop:~$ ! /bin/sh -f
$ sudo asoundconf set-default-card audigy

No icon either ! or he is a bit vague on where to find it..

---

### Post by christianj on 2007-05-08
Excellent guys, fixed..

It was THAT jack switch all along..

---

