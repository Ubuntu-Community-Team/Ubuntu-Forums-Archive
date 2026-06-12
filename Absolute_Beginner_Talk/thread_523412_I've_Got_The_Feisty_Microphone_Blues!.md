---
title: "I've Got The Feisty Microphone Blues!"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by ebediel on 2007-08-11
Well I'm trying to use Ekiga but Ubuntu won't recognize my microphone.  I've read through several of the forums to try to figure it out but so far no luck.  I don't really know where to start but here it goes.
scott@scott-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

scott@scott-desktop:~$ lsmod | grep snd
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mpu401              9256  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm


Any help would be greatly appreciated as I'm at a loss.
Thanks

---

### Post by ugm6hr on 2007-08-12
See this: [http://ubuntuforums.org/showpost.php?p=3178090&postcount=8](http://ubuntuforums.org/showpost.php?p=3178090&postcount=8)

Then post the results here.  That *might* be enough info to get it working.

---

### Post by ebediel on 2007-08-12
here's the amixer:
scott@scott-desktop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


and the screenshot from alsamixer:

[IMG]http://i208.photobucket.com/albums/bb219/ebediel/alsamixer.png[/IMG]

---

### Post by ebediel on 2007-08-12
Thanks, BTW.

---

### Post by ugm6hr on 2007-08-12
Hmmmm.... Not 100% certain - but this might be the problem:

> Simple mixer control 'Mic Select',0
Capabilities: enum
Items: 'Mic1' 'Mic2'
Item0: 'Mic1'
So your mic options are Mic1 or Mic2 (you have selected Mic1) - perhaps try Mic2????

But there is no option to edit Mic1 or Mic2 - only Mic0:
> Simple mixer control 'Mic',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Mono
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono: Playback 31 [100%] [12.00dB] [on]
Front Left: Capture [on]
Front Right: Capture [on]

Nevertheless - Mic0 has capture ON, so should work (if it actually refers to your mic)....

So perhaps Mic0 is not the correct mic?

> Simple mixer control 'Phone',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Mono
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono: Playback 31 [100%] [12.00dB] [on]
Front Left: Capture [off]
Front Right: Capture [off]
Perhaps Phone0 refers to the mic?  This certainly looks like some kind of sound input - and the capture is OFF at the moment - maybe worth turning capture ON here, and test again.

Sorry if this just sounds like rambling - but your sound card is different than mine, and I think a bit of trial and error is necessary to try out different combinations until something works.

If Phone0 doesn't appear in *alsamixer* - you can edit it directly with *amixer* - for commands:
```
amixer -h
```

Have a look here for my example:
[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

---

### Post by ebediel on 2007-08-14
Sorry it takes me so long to get back but I can only look at this at night.

I tried changing some things around and nothing worked.  I even tried plugging the microphone into the jack on the front of my machine and that did nothing.  I did test the mic on my laptop and it records fine on there.

I did make an observation though.  On my volume control window I have only one thing listed under recording: capture.     These: Microphone, CD input, Phone, and several other things are listed under playback.  That doesn't seem to be right since a mic is for recording and not playback.  Is there anyway to change this? 

Let me also say I went through the posts you recommended to me and everything is a little over my head.  I was able to muttle through but I'm not really sure I understand what I'm doing.  Simplicity is appreciated, although I was able to make some sense of things and it did stretch me a little which is not necessarily a bad thing.

Thanks again for your help.

---

### Post by ugm6hr on 2007-08-15
I'm not really sure about the playback / recording issue.  But my Mic is listed in Playback too - and it works OK.

Just to give me a handle on exactly what your settings are - can you post screenshots of all the alsamixer settings (the original is cut off at the right)?

And press Tab in alsamixer to bring up capture options - and post that screenshot too.

Hopefully something will click.

---

