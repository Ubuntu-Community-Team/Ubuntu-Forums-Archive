---
title: "No sound Mac Mini intel based"
date: 2011-03-24
forum: Apple Hardware Users
---

### Post by mowermanjp on 2011-03-24
here is my alsa info. can somebody help me get sound? works fine in osx but not ubuntu.


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Thu Mar 24 11:45:03 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Apple Inc.
Product Name:      Macmini3,1
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd3480000 irq 23


!!PCI Soundcards installed in the system
!!--------------------------------------

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:08.0 0403: 10de:0ac0 (rev b1)
	Subsystem: 10de:cb79


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=mbp55


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : mbp55,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC889A
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b4100
Revision Id: 0x100103
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC889A Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC889A Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC889A Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC889A Analog", type="Audio", device=2
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC889A Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=7, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=7, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3b 0x3b]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x012b4040: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Line Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x018b3010: [Jack] Line In at Ext Rear
    Conn = Comb, Color = Blue
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x90100130: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x41: OUT VREF_50
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x41: OUT VREF_50
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014be050: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x01cbe020: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = White
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=63
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=2, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Mar 22 08:09 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Mar 22 08:09 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Mar 22 08:10 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  7 Mar 23 21:36 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  6 Mar 22 08:10 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  5 Mar 22 08:10 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  4 Mar 22 08:09 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  3 Mar 22 08:09 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Mar 22 08:09 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar 22 08:09 .
drwxr-xr-x 3 root root 240 Mar 22 08:09 ..
lrwxrwxrwx 1 root root  12 Mar 22 08:09 pci-0000:00:08.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC889A Analog [ALC889A Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xd3480000 irq 23'
  Mixer name	: 'Realtek ALC889A'
  Components	: 'HDA:10ec0885,106b4100,00100103'
  Controls      : 33
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 59 [92%] [-5.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Line' 'CD'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Line' 'CD'
  Item0: 'Line'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Line' 'CD'
  Item0: 'Line'


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 0
		value.1 0
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 false
		value.1 false
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'LFE Playback Switch'
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 23
		value.1 23
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Line Boost'
		value.0 0
		value.1 0
	}
	control.12 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '6ch'
		iface MIXER
		name 'Channel Mode'
		value '2ch'
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 2
		value.0 false
		value.1 false
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 16
		value.1 16
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 16
		value.1 16
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 2
		value.0 16
		value.1 16
	}
	control.19 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Line
		comment.item.1 CD
		iface MIXER
		name 'Input Source'
		value Line
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Line
		comment.item.1 CD
		iface MIXER
		name 'Input Source'
		index 1
		value Line
	}
	control.21 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Line
		comment.item.1 CD
		iface MIXER
		name 'Input Source'
		index 2
		value Line
	}
	control.22 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.23 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.24 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.28 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Beep Playback Volume'
		value.0 23
		value.1 23
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 false
		value.1 false
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 59
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.33 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
hidp
binfmt_misc
rfcomm
sco
bnep
l2cap
parport_pc
ppdev
nvidia
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
lib80211_crypt_tkip
snd_pcm
wl
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
i2c_nforce2
snd_page_alloc
agpgart
lib80211
shpchp
applesmc
lp
led_class
parport
input_polldev
btusb
bluetooth
hid_a4tech
hid_apple
usbhid
hid
ahci
firewire_ohci
forcedeth
libahci
firewire_core
crc_itu_t


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x012b4040
0x15 0x018b3010
0x16 0x400000f0
0x17 0x400000f0
0x18 0x90100130
0x19 0x400000f0
0x1a 0x400000f0
0x1b 0x400000f0
0x1c 0x400000f0
0x1d 0x400000f0
0x1e 0x014be050
0x1f 0x01cbe020

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   10.181173] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
[   11.330001] ALSA: hda_intel.c: You're running a customized HDA driver, installed by DKMS. The packaging was made by [email]david.henningsson@canonical.com[/email].
[   11.330752] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   11.330759] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   11.330762] hda_intel: Disable MSI for Nvidia chipset
[   11.330790] HDA Intel 0000:00:08.0: setting latency timer to 64
[   11.330794] ALSA-HDA hda_intel.c:2515: chipset global capabilities = 0x4401
[   11.360025] ALSA-HDA hda_intel.c:908: codec_mask = 0x1
[   11.369046] ALSA-HDA hda_intel.c:1343: codec #0 probed OK
[   13.225407] hda_codec: ALC889A: SKU not ready 0x400000f0
[   13.525052] ALSA-HDA hda_codec.c:2145: Cannot find slave Center Playback Volume, skipped
[   13.525060] ALSA-HDA hda_codec.c:2145: Cannot find slave Side Playback Volume, skipped
[   13.525066] ALSA-HDA hda_codec.c:2145: Cannot find slave Speaker Playback Volume, skipped
[   13.525070] ALSA-HDA hda_codec.c:2145: Cannot find slave Mono Playback Volume, skipped
[   13.525075] ALSA-HDA hda_codec.c:2145: Cannot find slave Line-Out Playback Volume, skipped
[   13.525079] ALSA-HDA hda_codec.c:2145: Cannot find slave PCM Playback Volume, skipped
[   13.525089] ALSA-HDA hda_codec.c:2145: Cannot find slave Center Playback Switch, skipped
[   13.525095] ALSA-HDA hda_codec.c:2145: Cannot find slave Side Playback Switch, skipped
[   13.525101] ALSA-HDA hda_codec.c:2145: Cannot find slave Speaker Playback Switch, skipped
[   13.525105] ALSA-HDA hda_codec.c:2145: Cannot find slave Mono Playback Switch, skipped
[   13.525112] ALSA-HDA hda_codec.c:2145: Cannot find slave Line-Out Playback Switch, skipped
[   13.525117] ALSA-HDA hda_codec.c:2145: Cannot find slave PCM Playback Switch, skipped
[   14.661507] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 22
--
[   35.531865] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   36.724847] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.724852] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.724855] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.724859] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.725041] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.725045] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.725048] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.725051] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.725972] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.725976] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.725979] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.725982] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.726352] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.726356] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.726359] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.726362] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.726541] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.726545] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.726549] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.726552] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.726725] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.726729] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.726732] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.726735] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.726976] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.726980] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.726983] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.726986] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.727351] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.727355] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.727358] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.727361] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.727537] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.727541] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.727544] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.727547] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.727719] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.727722] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.727725] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.727728] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.727969] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.727973] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.727976] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.727979] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.728369] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.728373] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.728376] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.728379] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.728559] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.728563] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.728566] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.728569] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.728742] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.728746] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.728749] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.728752] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.728994] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.728998] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.729004] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.729007] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.729375] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.729379] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.729383] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.729386] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.729564] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.729568] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.729571] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.729574] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.729747] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.729750] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.729754] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.729757] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.729998] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.730002] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.730005] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.730008] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.730375] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.730379] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.730382] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.730386] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.768965] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.768977] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   36.792098] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   36.817036] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   36.841038] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[   36.864025] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[   36.889092] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.889108] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   36.889113] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   36.889117] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   36.889121] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[   36.889125] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[   36.889436] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.889616] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.889867] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.890237] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.890761] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.890770] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   36.913135] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.913144] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   36.913178] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.913195] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.922164] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.922173] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0xa, stream=0x4, channel=0, format=0x4011
[   36.945054] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.945062] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0xa, stream=0x4, channel=0, format=0x4011
[   36.945082] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.945130] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.945705] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.946185] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.946735] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.947407] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.947424] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.947428] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.947431] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.947434] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.947437] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   36.947455] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.947458] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.947461] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.947464] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.947868] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.947872] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.947876] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.947879] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.948266] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.948270] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.948274] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.948277] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.948781] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.948785] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.948788] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.948791] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.949455] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.949460] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.949463] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.949466] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.949862] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.949866] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.949869] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.949872] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.950261] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.950265] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.950268] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.950271] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.950775] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.950779] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.950782] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.950786] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.951429] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.951433] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.951436] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.951439] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.951832] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.951836] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.951839] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.951842] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.952228] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.952232] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.952236] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.952239] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.952743] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.952747] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.952751] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.952754] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.953412] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.953416] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.953419] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.953422] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.953819] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.953823] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.953826] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.953829] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.954219] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.954223] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.954226] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.954229] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.954735] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.954739] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.954742] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.954746] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.955386] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.955390] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.955393] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.955396] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.955788] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.955792] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.955795] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.955798] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.956184] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.956188] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.956191] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.956194] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.956699] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.956703] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.956707] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.956710] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.957382] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.957386] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.957389] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.957392] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.957766] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.957770] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.957774] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.957777] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.958126] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.958130] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.958133] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.958136] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.958504] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.958508] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.958511] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.958514] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.958887] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.958891] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.958894] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.958897] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.959250] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.959254] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.959257] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.959260] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.959610] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.959614] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.959618] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.959621] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.959987] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.959991] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.959995] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.959998] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.960367] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.960371] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.960374] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.960377] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.960727] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.960732] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.960735] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.960738] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.961103] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.961109] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.961113] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.961118] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.961485] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.961489] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.961492] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.961495] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.961869] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.961874] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.961879] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.961884] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.962239] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.962243] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.962246] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.962249] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.962597] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.962601] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.962604] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.962608] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.962971] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.962975] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.962979] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.962982] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.963352] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.963356] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.963360] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.963363] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.963714] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.963718] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.963722] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.963725] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.964072] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.964076] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.964079] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.964082] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.964447] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.964451] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.964454] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.964457] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.964830] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.964834] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.964837] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.964840] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.965209] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.965213] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.965216] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.965219] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.965565] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.965569] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.965572] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.965575] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.965941] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.965945] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.965948] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.965951] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.966324] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.966328] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.966331] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.966334] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.966685] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.966689] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.966692] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.966695] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.967043] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.967047] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.967050] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.967053] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.967423] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.967427] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.967430] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.967433] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.967802] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.967806] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.967809] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.967812] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.968164] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.968168] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.968171] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.968174] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.968520] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.968524] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.968527] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.968530] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.968896] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.968900] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.968903] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.968906] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.969324] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.969328] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.969332] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.969335] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.969685] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.969689] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.969693] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.969696] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.970043] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.970047] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.970051] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.970054] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.970418] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.970422] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.970426] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.970429] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.970799] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.970803] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.970806] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.970809] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.971160] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.971164] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.971167] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.971170] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.971517] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.971521] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.971525] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.971528] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.971892] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.971896] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.971899] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.971902] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.972272] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.972276] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.972280] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.972283] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.972674] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.972678] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.972682] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.972685] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.973088] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.973093] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.973098] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.973102] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.973605] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.973609] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.973612] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.973615] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.974261] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.974265] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.974268] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.974272] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.974664] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.974668] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.974672] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.974675] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.975060] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.975064] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.975067] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.975070] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.975575] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.975579] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.975582] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.975585] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.976226] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.976230] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.976234] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.976237] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.976629] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.976633] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.976636] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.976639] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.977084] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.977089] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.977094] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.977098] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.977603] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.977607] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.977610] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.977613] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.978259] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.978263] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.978266] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.978269] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.978661] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.978665] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.978668] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.978671] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.979058] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.979062] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.979065] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.979068] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.979570] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.979574] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.979578] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.979581] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.980222] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.980226] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.980229] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.980232] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.980625] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.980629] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.980632] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.980635] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.981039] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.981044] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.981049] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.981053] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.981560] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.981564] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.981567] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.981570] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.982215] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.982219] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.982222] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.982225] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.982619] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.982623] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.982626] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.982629] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.983016] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.983020] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.983024] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.983027] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.983530] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.983534] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.983537] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.983540] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.984183] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.984187] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.984191] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.984193] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.984584] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.984588] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.984591] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.984594] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.984980] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.984984] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.984987] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.984990] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.985540] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.985544] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.985548] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.985551] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.986195] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.986199] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.986202] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.986205] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.986597] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.986601] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.986604] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.986607] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.986995] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.986999] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.987002] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.987005] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.987509] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.987513] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.987516] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.987519] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.988161] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.988165] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.988168] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.988171] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.988563] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.988567] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.988571] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.988574] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.988962] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.988966] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.988969] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.988972] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.989493] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.989496] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.989500] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.989503] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.990151] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.990155] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.990159] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.990162] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.990554] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.990558] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.990562] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.990565] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.990951] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.990955] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.990958] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.990961] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.991465] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.991469] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.991472] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.991475] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.992117] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   36.992121] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   36.992124] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   36.992128] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   36.992710] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.992725] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   36.997068] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.997077] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   36.997291] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.997465] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.997706] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.998071] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.998564] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.998572] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   36.998586] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.998592] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   36.998606] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.998618] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   36.999127] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.999135] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0xa, stream=0x4, channel=0, format=0x4011
[   36.999149] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   36.999155] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0xa, stream=0x4, channel=0, format=0x4011
[   36.999165] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.999192] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   36.999670] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.000144] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.000685] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.001399] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.001412] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.001435] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.001937] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.002425] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.002980] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.003661] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.004153] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.004640] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.005213] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.005895] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.006389] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.006879] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.007443] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.008128] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.008628] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.009147] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.009705] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.010387] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.010882] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.011371] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.011925] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.012607] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   37.014841] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   37.015013] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   37.015252] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   37.015616] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   37.016118] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   37.016127] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   37.016141] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   37.016147] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   37.016160] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   37.016178] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x7
[   37.016689] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   37.016697] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0xa, stream=0x4, channel=0, format=0x4011
[   37.016711] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   37.016717] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0xa, stream=0x4, channel=0, format=0x4011
[   37.016727] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.016756] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.017274] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.017750] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.018290] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.018955] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0xa
[   37.152070] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   37.152083] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   37.160036] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   37.160042] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   37.160047] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[   37.160052] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[   37.160088] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   37.160097] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   37.160103] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   37.160108] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   37.160112] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[   37.160117] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[   40.071960] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   52.407988] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   52.407993] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   52.407996] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   52.407999] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   52.408002] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[   52.408026] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   52.408029] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   52.408032] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[   52.408035] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[   79.408667] lo: Disabled Privacy Extensions
[  122.955111] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  122.955125] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  122.955132] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  122.955136] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  122.955141] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[  122.955145] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[  122.955374] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  122.955382] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  122.955387] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  122.955391] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  122.955395] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[  122.955399] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[  148.246554] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[  148.246561] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[  148.246565] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[  148.246568] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[  148.246572] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[  148.246599] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[  148.246602] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[  148.246606] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[  148.246610] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[  206.638012] lo: Disabled Privacy Extensions
--
[ 8246.253017] ehci_hcd 0000:00:06.1: PCI INT B disabled
[ 8246.416023] HDA Intel 0000:00:08.0: PCI INT A disabled
[ 8246.432017] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 220.964 msecs
[ 8247.220775] PM: suspend of drv:sd dev:0:0:0:0 complete after 1014.810 msecs
--
[ 8247.872685] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[ 8247.872708] HDA Intel 0000:00:08.0: restoring config space at offset 0xf (was 0x5020100, writing 0x502010f)
[ 8247.872719] HDA Intel 0000:00:08.0: restoring config space at offset 0x4 (was 0x0, writing 0xd3480000)
[ 8247.872725] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[ 8247.872742] pci 0000:00:09.0: restoring config space at offset 0xf (was 0x2000000, writing 0x20000ff)
--
[ 8247.874299] ehci_hcd 0000:00:06.1: setting latency timer to 64
[ 8247.874318] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[ 8247.874323] HDA Intel 0000:00:08.0: setting latency timer to 64
[ 8247.874346] pci 0000:00:09.0: setting latency timer to 64
--
[16788.976026] ehci_hcd 0000:00:06.1: PCI INT B disabled
[16789.136022] HDA Intel 0000:00:08.0: PCI INT A disabled
[16789.143645] sd 0:0:0:0: [sda] Stopping disk
[16789.152016] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 219.628 msecs
[16790.301706] PM: suspend of drv:sd dev:0:0:0:0 complete after 1371.749 msecs
--
[16790.944686] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[16790.944709] HDA Intel 0000:00:08.0: restoring config space at offset 0xf (was 0x5020100, writing 0x502010f)
[16790.944721] HDA Intel 0000:00:08.0: restoring config space at offset 0x4 (was 0x0, writing 0xd3480000)
[16790.944726] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[16790.944743] pci 0000:00:09.0: restoring config space at offset 0xf (was 0x2000000, writing 0x20000ff)
--
[16790.946309] ehci_hcd 0000:00:06.1: setting latency timer to 64
[16790.946318] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[16790.946323] HDA Intel 0000:00:08.0: setting latency timer to 64
[16790.946352] pci 0000:00:09.0: setting latency timer to 64
--
[16827.127993] lo: Disabled Privacy Extensions
[16905.628624] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[16905.628637] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[16905.653083] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[16905.677033] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[16905.701034] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[16905.724108] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[16905.749123] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[16905.749139] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[16905.749336] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[16905.749340] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[16905.749345] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[16905.749348] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[16976.698175] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[16976.698182] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[16976.698186] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[16976.698190] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[16976.698194] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[16976.698221] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[16976.698225] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[16976.698229] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[16976.698233] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[17084.259625] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[17084.259641] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[17084.259648] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[17084.259653] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[17084.259659] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[17084.259664] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[17084.259884] ALSA-HDA hda_intel.c:1667: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[17084.259893] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[17084.259899] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[17084.259904] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[17084.259909] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[17084.259914] ALSA-HDA hda_codec.c:1226: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x4011
[17090.357526] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[17090.357533] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[17090.357537] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[17090.357541] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[17090.357545] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x6
[17090.357576] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[17090.357580] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[17090.357584] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x4
[17090.357588] ALSA-HDA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x5
[37717.765325] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
--
[37719.347170] sd 0:0:0:0: [sda] Stopping disk
[37719.464023] HDA Intel 0000:00:08.0: PCI INT A disabled
[37719.480017] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 221.136 msecs
[37720.316933] PM: suspend of drv:sd dev:0:0:0:0 complete after 1063.022 msecs
--
[37720.976687] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[37720.976710] HDA Intel 0000:00:08.0: restoring config space at offset 0xf (was 0x5020100, writing 0x502010f)
[37720.976722] HDA Intel 0000:00:08.0: restoring config space at offset 0x4 (was 0x0, writing 0xd3480000)
[37720.976727] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[37720.976744] pci 0000:00:09.0: restoring config space at offset 0xf (was 0x2000000, writing 0x20000ff)
--
[37720.978306] ehci_hcd 0000:00:06.1: setting latency timer to 64
[37720.978314] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[37720.978320] HDA Intel 0000:00:08.0: setting latency timer to 64
[37720.978343] pci 0000:00:09.0: setting latency timer to 64

---

