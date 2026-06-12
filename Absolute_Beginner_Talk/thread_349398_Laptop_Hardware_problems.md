---
title: "Laptop Hardware problems"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by eilu on 2007-01-30
Just installed Dapper on my new laptop (whitebox) but I have a bunch of problems:
1. No sounds. No nothing, not even a system beep. I tried the [comprehensive sound problems solutions guide]("http://ubuntuforums.org/showthread.php?t=205449") but got nothing.
Like it said, I did $aplay -l, to which Dapper returned:
```
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subservices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device10: AD198x Digital [AD198x Digital]
  Subservices: 1/1
  Subdevice #0: subdevice #0
```
Then I did $alsamixer and unmuted everything (headphone, PCM, Front, Surround, Center, LFE, Line CD, IEC958, PC Speak, Aux, Mono, Stereo D), and I still can't here anything.

2. As for the modem, it can't autodetect the internal one. eth0 and eth1 (wireless and ethernet, respectively) worked, but the modem cannot be detected. There are 5 ports listed at /dev/ (/modem, /ttyS0, /ttyS1, /ttyS2 and /ttyS3) but it says it can't detect the modem

3. weird thing with ejecting a CD- if I push the eject button on the drive and there's no CD, the tray comes out BUT if there's a mounted CD inside, pushing eject does nothing; I have to eject it from Nautilus. How odd.

4. hardware buttons don't work. Not *really* important, but I'd love to be able to turn the touchpad on & off

---

### Post by mikewhatever on 2007-01-31
In case you haven't tried reinstalling the sound driver, check this [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)
The instructions are for 6.06, but I've done the same to get the mic to work.

---

### Post by JulioCruz on 2007-01-31
>  4. hardware buttons don't work. Not *really* important, but I'd love to be able to turn the touchpad on & off

I turned my touchpad off by installing and using Qsynaptics, you have to edit  the Input Device section in your xorg.conf like below:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"   
EndSection

I added a button in the toolbar so i can easily acces it and turn touchpad on and off

---

