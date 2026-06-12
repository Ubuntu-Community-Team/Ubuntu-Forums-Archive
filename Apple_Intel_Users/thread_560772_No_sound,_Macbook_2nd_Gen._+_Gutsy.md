---
title: "No sound, Macbook 2nd Gen. + Gutsy"
date: 2007-09-26
forum: Apple Intel Users
---

### Post by anujseth on 2007-09-26
Just installed Gutsy Tribe 5 and then about 400 MB of updates on a 2nd Gen. 2GHz macbook. There is no sound. Tried various different options, alsa mixer settings etc. nothing. There is no sound from the speaker and also the headphones. Just for the record there were no such problems on feisty. 

also read last few posts here ->
[http://ubuntuforums.org/showthread.php?t=555730](http://ubuntuforums.org/showthread.php?t=555730)

---

### Post by myk on 2007-09-26
I also have this problem :( Hopefully it gets resolved soon!

---

### Post by nicfagn on 2007-09-28
Can you post the output of :
```
cat /proc/asound/version
cat /proc/asound/card0/codec#0
amixer

```
This could help understand why sound is not working for your Macbook 2nd Gen.

Bye

Nicola

---

### Post by myk on 2007-09-29
Hey, 
I reinstalled Ubuntu 7.04 so I could have working sound. I'll post the output of those commands for ubuntu 7.04 if it helps.

```

mn@macbook:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
mn@macbook:~$ cat /proc/asound/card0/codec#0
Codec: SigmaTel STAC9221 A1
Address: 0
Vendor Id: 0x83847680
Subsystem Id: 0x106b2200
Revision Id: 0x103401
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x66 0x66]
  Power: 0x0
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Power: 0x0
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x17
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x18
Node 0x08 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
Node 0x09 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x11
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect
  Pin Default 0x0321e230: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = White
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect
  Pin Default 0x03a1e020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = White
  Pin-ctls: 0x24: IN
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect
  Pin Default 0x9017e110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = White
  Pin-ctls: 0x00:
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0x00:
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x0824: IN Detect
  Pin Default 0x01a19021: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect
  Pin Default 0x0381e021: [Jack] Line In at Ext Left
    Conn = 1/8, Color = White
  Pin-ctls: 0x20: IN
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x1345e240: [Jack] SPDIF Out at Int Left
    Conn = Optical, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 3
     0x08* 0x17 0x19
Node 0x11 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN EAPD Detect
  Pin Default 0x13c5e22e: [Jack] SPDIF In at Int Left
    Conn = Optical, Color = White
  Pin-ctls: 0x20: IN
  Power: 0x0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e* 0x15 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e 0x15* 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x02a19320: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x00:
Node 0x16 [Volume Knob Widget] wcaps 0x600000: Mono
Node 0x17 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x12
Node 0x18 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x13
Node 0x19 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
Node 0x1a [Audio Output] wcaps 0x30201: Stereo Digital
Node 0x1b [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x400000fb: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x1a
mn@macbook:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 102 [80%] [-18.75dB] [on]
  Front Right: Playback 102 [80%] [-18.75dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Line In as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

```

---

### Post by nicfagn on 2007-09-30
I looked at the alsa driver code at version 1.0.14, the one used in Gutsy, and from what I can understand your model, with the SigmaTel STAC9221 A1 codec, should be explicitly supported.
The strange thing is that in alsa 1.0.14rc1, the Feisty one,  it shouldn't be supported at all :confused:

Bye

---

### Post by myk on 2007-09-30
That's very strange lol, well I know that 7.04 and sound do work! Thanks for looking though!

---

### Post by xIke on 2007-10-16
I'm running gutsy and also have no sound.  If anyone's still watching this thread, I'd love to give you whatever information you need to diagnose and fix this.

Cheers.

---

### Post by quannum on 2007-10-16
I'm running Gutsy RC on my MacBook Pro and have sound though headphones only. Same sound card as the MacBook, so not sure what the difference would be...

---

### Post by cyberdork33 on 2007-10-16
For those requesting help or a fix, please post the output of these commands for your machine. This will help people understand exactly what hardware you have and any issues there may be with it.
```
cat /proc/asound/version
cat /proc/asound/card0/codec#0
amixer
```

---

### Post by xIke on 2007-10-16
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

/proc/asound/card0/codec#0
```
Codec: SigmaTel STAC9221 A1
Address: 0
Vendor Id: 0x83847680
Subsystem Id: 0x106b1e00
Revision Id: 0x103401
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Power: 0x0
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x17
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x18
Node 0x08 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
Node 0x09 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x11
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect
  Pin Default 0x90a70120: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x24: IN
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect
  Pin Default 0x01813024: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x0824: IN Detect
  Pin Default 0x400000fd: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x1345e240: [Jack] SPDIF Out at Int Left
    Conn = Optical, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 3
     0x08* 0x17 0x19
Node 0x11 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN EAPD Detect
  Pin Default 0x13c5e22e: [Jack] SPDIF In at Int Left
    Conn = Optical, Color = White
  Pin-ctls: 0x20: IN
  Power: 0x0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e 0x15 0x0f 0x0b* 0x0c 0x0d 0x0a
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e 0x15 0x0f 0x0b* 0x0c 0x0d 0x0a
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400000fc: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
Node 0x16 [Volume Knob Widget] wcaps 0x600000: Mono
Node 0x17 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x12
Node 0x18 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x13
Node 0x19 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
Node 0x1a [Audio Output] wcaps 0x30201: Stereo Digital
Node 0x1b [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x400000fb: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x1a
```

amixer:
```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Line In as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
```

---

### Post by nicfagn on 2007-10-17
Just remembered that, since the inclusion of the linux-ubuntu-modules package into Gutsy, the alsa kernel modules are blacklisted.
In other words, the snd_hda_intel module in the kernel is disabled in favor of the one contained in the linux_ubuntu-modules package, so compiling an installing from alsa sources isn't sufficient.
To use the compiled module, you have to kill the mixer applet and issue the following commands:

```

sudo rmmod $(lsmod | awk '/snd/{print $1}')
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,_orig}.ko
sudo cp -v /lib/modules/$(uname -r)/{kernel/sound/pci/hda,ubuntu/media/snd-hda-intel}/snd-hda-intel.ko
sudo depmod -a
sudo modprobe snd_hda_intel

```

Just for reference, this snippet of code shows the choice of sound configuration for sigmatel systems, in alsa-driver-1.0.14 sources:
```

		switch (codec->subsystem_id) {

		case 0x106b0800:
			spec->board_config = STAC_INTEL_MAC_V1;
			break;
		case 0x106b0600:
		case 0x106b0700:
			spec->board_config = STAC_INTEL_MAC_V2;
			break;
		case 0x106b0e00:
		case 0x106b0f00:
		case 0x106b1600:
		case 0x106b1700:
		case 0x106b0200:
		case **0x106b1e00**:
			spec->board_config = STAC_INTEL_MAC_V3;
			break;
		case 0x106b1a00:
		case 0x00000100:
			spec->board_config = STAC_INTEL_MAC_V4;
			break;
		case 0x106b0a00:
		case **0x106b2200**:
			spec->board_config = STAC_INTEL_MAC_V5;
			break;
		}
```
and both systems in this thread (myk = 0x106b2200, xIke = 0x106b1e00) are valid entries in it.

---

### Post by nicfagn on 2007-10-17
Same snippet of code in linux-ubuntu-modules:
```

		switch (codec->subsystem_id) {
		case 0x106b0a00: /* MacBook First generatoin */
			spec->board_config = STAC_MACBOOK;
			break;
		case 0x106b0200: /* MacBook Pro first generation */
			spec->board_config = STAC_MACBOOK_PRO_V1;
			break;
		case 0x106b1e00: /* MacBook Pro second generation */
			spec->board_config = STAC_MACBOOK_PRO_V2;
			break;
		case 0x106b0700: /* Intel-based iMac */
			spec->board_config = STAC_IMAC_INTEL;
			break;
		}

```

This explains why the 0x106b2200 system is not working, is missing here.
The 0x106b1e00 is present but it seems to have a different config...

---

### Post by cyberdork33 on 2007-10-17
> **nicfagn said:**
> Just remembered that, since the inclusion of the linux-ubuntu-modules package into Gutsy, the alsa kernel modules are blacklisted.
In other words, the snd_hda_intel module in the kernel is disabled in favor of the one contained in the linux_ubuntu-modules package, so compiling an installing from alsa sources isn't sufficient.

Can you not just add the modules to the blacklist file the same way we do for custom fglrx modules, madwifi, etc?

---

### Post by nicfagn on 2007-10-17
> **cyberdork33 said:**
> Can you not just add the modules to the blacklist file the same way we do for custom fglrx modules, madwifi, etc?

Quite likely yes, If I knew how to do. ;-)
I didn't dig into this and the simpler way I found to use my compiled module was the one in the post above, but If there are better ways they're welcome.

I think that now I'm going to look into this...

---

### Post by xIke on 2007-10-17
Should I wait or try 

```
sudo rmmod $(lsmod | awk '/snd/{print $1}')
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,_orig}.ko
sudo cp -v /lib/modules/$(uname -r)/{kernel/sound/pci/hda,ubuntu/media/snd-hda-intel}/snd-hda-intel.ko
sudo depmod -a
sudo modprobe snd_hda_intel
```

It looks somewhat permanent...

---

### Post by nicfagn on 2007-10-17
Ok, I think this is the situation.
The snd_hda_intel module is part of the linux kernel and so it was shipped with the linux-image-generic package until the kernel development team decided to create the linux-ubuntu-modules package to manage some modules independently from the rest of the kernel.
Since then, the module is not included in kernel compilation and in this sense blacklisted and not installed by the linux-image-generic package in it's usual location /lib/modules/$(uname -r)/kernel/sound/pci/hda. 
I read the term "blacklisted" in a commit log and so I used it here but it is a completely different thing from the module blacklisting mentioned by cyberdork33.
The module is instead installed by the linux-ubuntu-modules into /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel.

What I didn't get was why a module compiled from source and installed in the usual location was ignored in favor of the linux-ubuntu-modules one.
After some tries the explanation is quite simple: the depmod commands generates module dependencies looking for them in the /lib/modules/$(uname -r) directory in alphabetical order; if it finds more than one module with the same name, only the last one is kept.
In the end the dependencies for the module under /lib/modules/$(uname -r)/ubuntu are kept and the ones for the module under /lib/modules/$(uname -r)/kernel are discarded, and the l-u-m snd-hda-intel module is loaded by the modprobe command.

All this implies that to use the compiled version under the kernel directory, one can simply rename the l-u-m module:
```

kill $(fuser /dev/snd/*)
sudo rmmod $(lsmod | awk '/snd/{print $1}')
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
sudo depmod -a
sudo modprobe snd_hda_intel
```
and to undo that:
```

kill $(fuser /dev/snd/*)
sudo rmmod $(lsmod | awk '/snd/{print $1}')
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{-ubuntu,}.ko
sudo depmod -a
sudo modprobe snd_hda_intel
```
So it's not permanent ;-)

---

### Post by xIke on 2007-10-17
Great, trying it now...  How can I get around this?

```
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_pcm,snd_timer
ERROR: Module soundcore is in use by snd
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
```

Thanks.

---

### Post by cyberdork33 on 2007-10-17
Weird that they do not have a file similar to [SIZE=-1]/etc/default/linux-restricted-modules-common for modules of other than the 'restricted' variety. That would make things a bit easier.
[/SIZE]

---

### Post by nicfagn on 2007-10-18
> **xIke said:**
> Great, trying it now...  How can I get around this?

```
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_pcm,snd_timer
ERROR: Module soundcore is in use by snd
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
```

Thanks.

You have to quit all programs using sound, that is at least kill the mixer applet process, or use  a command like:

kill $(fuser /dev/snd/*)

---

### Post by xIke on 2007-10-19
I'm sorry it took me so long to respond...the forum didn't notify me that there was a response.

I'm not having any luck killing sound.  I tried those commands from a pure terminal login and they didn't work.  The kill command didn't work, the shell complained about usage of kill.  Any ideas?

---

### Post by nicfagn on 2007-10-19
> **xIke said:**
> 
I'm not having any luck killing sound.  I tried those commands from a pure terminal login and they didn't work.  The kill command didn't work, the shell complained about usage of kill.  Any ideas?

I copied the kill command from the post and pasted into gnome-terminal and it killed the volume applet. I can't figure out why it doesn't work for you :confused:
To make things simple you can just do:
```

sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
sudo depmod -a

```
and then reboot.

---

### Post by xIke on 2007-10-19
Okay, I'm on the last step so I think there's hope...

```
$ sudo modprobe snd_hda_intel
FATAL: Module snd_hda_intel not found.
```

---

### Post by nicfagn on 2007-10-19
What is the ouput of:
```
ls -l /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
```
?

---

### Post by xIke on 2007-10-19
```
ls: /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko: No such file or directory
```

---

### Post by nicfagn on 2007-10-19
Oh **_my fault_**, I confused this thread with others I'm following.:(
I thought you had compiled and installed from alsa sources while in fact you where using only the Ubuntu version of the snd_hda_intel module.

My proposed solution needs that you compile and install from alsa-driver-1.0.14 sources.
If you want try this, do the following:

Download alsa sources from:
 [INDENT][ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")[/INDENT] 

Expand the sources with:
```
tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2
```

Install the libc6 developer libraries if missing:

```
sudo apt-get install libc6-dev
```

Cd into **alsa-driver-1.0.14** dir in a terminal and do a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

Compile with the command:

```
make
```

Install the compiled modules:

```
sudo make install-modules
```

Reboot or load the module with:

```
sudo modprobe snd_hda_intel
```

---

### Post by nicfagn on 2007-10-19
Oh **_my fault_**, I confused this thread with others I'm following.:(
I thought you had compiled and installed from alsa sources while in fact you where using only the Ubuntu version of the snd_hda_intel module.

My proposed solution needs that you compile and install from alsa-driver-1.0.14 sources.
If you want to try this, do the following:

Download alsa sources from:
 [INDENT][ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")[/INDENT] 

Expand the sources with:
```
tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2
```

Install the libc6 developer libraries if missing:

```
sudo apt-get install libc6-dev
```

Cd into **alsa-driver-1.0.14** dir in a terminal and do a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

Compile with the command:

```
make
```

Install the compiled modules:

```
sudo make install-modules
```

Reboot or load the module with:

```
sudo modprobe snd_hda_intel
```

---

### Post by xIke on 2007-10-19
Sweet, thank you so much.  It's working perfectly now.  I don't see how you people (smart people) can know all this stuff....

---

### Post by nicfagn on 2007-10-19
Great! :popcorn:

---

### Post by phonky on 2007-10-19
Sorry, can't join in the hurray....

My audio first didn't work at all.
Downloaded **alsa-driver-1.0.15** first, didn't work at all.
Then installed **alsa-driver-1.0.14**, as in your post.

Now I have audio, but I can't regulate the volume!
I turn down the volume in the volume applet in the panel,
but there's NO EFFECT!

When I plug in headphones, I don't hear anything at all.
I bet the mic doesn't work either, but I'm not going to try as I will
wake up the rest of my fellow students...

any ideas?

---

### Post by xIke on 2007-10-19
As for the applet. you can right click on it, go to prefs, and tell it what to control.  For me, I have it set to HDA Intel (Alsa Mixer) and then Master.

Headphones just work for me though, not sure what your problem there is.

---

### Post by phonky on 2007-10-19
I gave it again a try with 1.0.15.
> /configure --with-cards=hda-intel, make, and sudo make install.
without reboot (what configuration do I have now?:confused:).
Did it load the new audio or the old?

If I lower the volume in the volume applet, nothing happens.
But if I change the volume in Rhythmbox, the volume responds...:confused::confused::confused:

Headphones still do not work

---

### Post by xIke on 2007-10-19
Well, changing it in rhythmbox isn't actually changing your system volume, just how loud the music will be. (if you have any other apps making sound, they won't be any quieter by changing rhythmbox).

Did you try setting the applet to control a different device?  That really sounds like your problem to me, but your post doesn't make it clear if you tried that or not.

---

### Post by phonky on 2007-10-20
It seems 1.0.15 doesn't work.

with 1.0.14 the sound is working again. =D> the problem was indeed the applet,
but for another reason: Moving the master sliders wasn't doing anything.
Only the PCM and the Front sliders were affecting the volume!

Headphones are working now as well....

No idea why. Perhaps I had some old modules from my 1.0.15 make install floating????

Scared of reboot though...:redface:

---

### Post by xIke on 2007-10-20
Yeah, reboots can be terrifying.  Right now I'm scared of suspend the most though.  Everything else is rescuable.

---

### Post by hackersmovie on 2008-04-02
**BUMP**

Same issue here! I can do without the iSight and a quirky trackpad but, I gotta have some sound! This is the deal breaker for me! 

[SIZE="5"][COLOR="Red"]PLEASE HELP[/COLOR][/SIZE]

[B][COLOR="Lime"]EDIT: I GOT IT WORKING, I'm not even sure what it was. I found a thread relating to the fact the the Alsa mixer has trouble detecting the audio chip or something and forced it to look again, it worked! The sound is now working, sounds like crap, but working. I use headphones, they sound much better. . . 
[/COLOR][/B]

---

### Post by Aurora on 2008-05-29
[Moved to new thread]

---

