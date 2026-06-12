---
title: "SBlive 4"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Drathas on 2008-02-01
Maybe someone here can explain the process related to sound in Ubuntu, I seem to either be a moron or unable to decipher how ALSA works.

I have an SBlive it's supported by ALSA - the sound system is using ALSA mixer for everything.  No channels are muted and yet there's still no sound being produced and the "test" button produces no errors [other than no sound of course].

> 
/etc/modules

alias char-major-116 snd
alias snd-card-0 snd-ca0106
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss


> 
**output of 'aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> 
**output of lspci -v**

02:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0790 X-Fi XA
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at ac00 [size=32]
        Capabilities: <access denied>


As you can see, I have fairly good understanding of what needs to happen and what IS happening.  I searched the forum for almost an hour and tried every suggestion for other peoples problems and I feel maybe I've overlooked something incredibly small.  I also have these weird IEC958 hardware channels (I think that's what they are) showing up in the mixer/sound properties, no idea what they are or what they do.

---

### Post by r4ik on 2008-02-01
Think you did this but anyway,
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by Drathas on 2008-02-01
> **r4ik said:**
> Think you did this but anyway,
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

The only thing present in the switches tab is that IE958 business.  Which is weird to me like I said because it apparently doesn't even exist.

---

### Post by r4ik on 2008-02-01
I am almost afraid to ask :) but you did try Edit=> Preferences in the volume control ?

---

### Post by Drathas on 2008-02-01
> **r4ik said:**
> I am almost afraid to ask :) but you did try Edit=> Preferences in the volume control ?

Yuppers.  Any idea what that IEC958 stuff is in the audio panels?  It's kind of weird.

---

### Post by r4ik on 2008-02-01
Not really i have IEC958 and IEC958 Capture so it from this world i suppose.


A standard for digital audio transfer published by the IEC (International Electrotechnical Commission). The IEC958 standard describes (specifically in IEC958 Part 3 and IEC958 Part 4) the protocol used by what we commonly refer to as AES/EBU (now called AES3) and S/PDIF for transferring digital audio data between hardware platforms.

Doesn't tell me a lot.

---

### Post by Drathas on 2008-02-01
Would it be worth my while to yank out the SBlive and try the onboard soundcard?  it's a c-major their chipset hasn't changed in probably ten years - if it's a support issue c-major should definitely work IMO.

---

### Post by r4ik on 2008-02-01
Give it a go why not ?

---

### Post by r4ik on 2008-02-01
By the way did you try,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

---

### Post by Drathas on 2008-02-01
praise zombie jesus the onboard soundcard works!

As for the guide - yes and no result.  Sound Blaster cards are junk anyway I've been meaning to ditch mine for a long time now anyway, looks like I have a good excuse.  Thanks for the help it was appreciated.

---

### Post by r4ik on 2008-02-01
Glad it works see you around :)

---

