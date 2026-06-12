---
title: "No sound in Fiesty on newly built computer"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by nixy_jones on 2007-10-13
I can't get any sound to come out of my new install. 
[LIST]
[*]Gigabyte 965p-ds3 motherboard
[/LIST]
[LIST]
[*]ubuntu 7.04
[/LIST]
I have followed every instruction found in [this tutorial]("http://ubuntuforums.org/showthread.php?t=205449"). And have done everything found in the readme file in the [realtek driver download (version 4.06a)]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false").

By running aplay -l I can see that my onboard sound is detected, as well as my cheap old pci sound card I threw in to see if maybe the mobo was defective. Neither works.

[INDENT]card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AV710 [Chaintech AV-710], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/INDENT]

All channels in my alsamixer are unmuted.

Thanks to anyone that can help.

---

### Post by Girya on 2007-10-13
I had the same problem when I installed 7.04. here is the adress of the guide that i used to get the sound going. [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

Note that I installed 7.10 and the sound worked without any problems. Good luck, Kevin

---

### Post by nixy_jones on 2007-10-13
Did it. Twice. Received no errors and everything came out just as guide described (with the exception that ALSA-Configuration.txt is in a different location - /usr/src/modules/alsa-driver/alsa-kernel/Documentation/)

Still no sound. Downloading 7.10 to see if that works.

---

### Post by nixy_jones on 2007-10-13
Update. I installed 7.10. WOW. Everything looks and feels fantastic. A significant improvement over 7.04. 

However, I still have sound issues. Everything *appears* to be installed and running; my Volume control gives me the option of switching between HDA Intel (ALSA mixer) Chaintech (ALSA mixer) and ALC888 Realtek (OSS mixer). 

I have on the mobo 1 digital coax, 1 optical, and six 1/8" stereo jacks (center out / surround out / side out / line in / line out / mic in). 
The coax and optical have no signal with any device enabled. Headphones plugged into the main line out produce the faintest whisper of a signal *regardless* of what channel is enabled.

This has to be something simple that I'm missing, but I'm at wit's end after having stared at this thing all day. I would be ever so happy if someone could suggest something new to try.

---

### Post by nixy_jones on 2007-10-13
Solved

IEC958 was muted in AlsaMixer.

System > Preferences > Sound > Music and movies ALC883 Digital. Sound events, meanwhile, only work in ALC883 analog.

?

---

