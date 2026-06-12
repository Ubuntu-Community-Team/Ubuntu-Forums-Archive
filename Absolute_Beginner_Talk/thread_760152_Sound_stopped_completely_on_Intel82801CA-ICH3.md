---
title: "Sound stopped completely on Intel82801CA-ICH3"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by PinkFloyd102489 on 2008-04-19
The sound was working just fine yesterday. I had to play around a bit with Xine plugins in order to get Totem, Mplayer, and XMMS to correctly play everything and it was sounding great. Now today, sound doesnt work at all. I dont recall changing anything, only restarting the laptop.


Any ideas?


Here's the output of the also-info debugging script:

```

name=tabitha&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.41
!!################################

!!Script ran on: Sat Apr 19 23:02:41 EDT 2008


!!Linux Distribution
!!------------------

Ubuntu 7.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.10"


!!Kernel Information
!!------------------

Kernel release:    2.6.22-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.14
Library version:    
Utilities version:  1.0.14


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with AD1886 at irq 5


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:2485 (rev 01)
	Subsystem: 0e11:007b


!!Modprobe options (Sound related)
!!--------------------------------

snd-bt87x: index=-2
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=1
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
ac97_clock : 0
ac97_quirk : <NULL>
buggy_irq : N
buggy_semaphore : N
enable : N
id : <NULL>
index : -1
joystick : 0
spdif_aclink : 0
xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1886

PCI Subsys Vendor: 0x0e11
PCI Subsys Device: 0x007b

Capabilities     : -headphone out-
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : Analog Devices Phat Stereo

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=0 DSA=0 SPDIF VRA
Extended status  : SPCV SPDIF=3/4 SPDIF VRA
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0410
0:02 = 0a0a
0:04 = 0606
0:06 = 0006
0:08 = 0000
0:0a = 0002
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 0606
0:14 = 9f1f
0:16 = 9f1f
0:18 = 0303
0:1a = 0505
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 000c
0:24 = 0000
0:26 = 800f
0:28 = 0005
0:2a = 0405
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0010
0:74 = 1000
0:76 = 0404
0:78 = bb80
0:7a = bb80
0:7c = 4144
0:7e = 5361
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116, 7 2008-04-19 22:51 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 6 2008-04-19 22:51 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 5 2008-04-19 22:51 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 4 2008-04-19 22:51 /dev/snd/pcmC0D1c
crw-rw---- 1 root audio 116, 3 2008-04-19 22:51 /dev/snd/seq
crw-rw---- 1 root audio 116, 2 2008-04-19 22:51 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 1: Intel ICH - MIC ADC [Intel 82801CA-ICH3 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [I82801CAICH3]

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 53 [84%] [-15.00dB] [on]
  Front Right: Playback 53 [84%] [-15.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 57 [90%] [-3.00dB] [on]
  Front Right: Playback 57 [90%] [-3.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 12 [80%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 12 [80%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [7.50dB] [on]
  Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
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
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 14 [93%] [-3.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.I82801CAICH3 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		iface MIXER
		name 'Master Playback Volume'
		value.0 53
		value.1 53
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 57
		value.1 57
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Master Mono Playback Volume'
		value 25
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 14
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value false
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Video Playback Switch'
		value false
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Video Playback Volume'
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'PCM Playback Volume'
		value.0 28
		value.1 28
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mix
		value.1 Mix
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.27 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'pre 3D'
		comment.item.1 'post 3D'
		iface MIXER
		name 'PCM Out Path & Mute'
		value 'pre 3D'
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name '3D Control - Switch'
		value false
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Center'
		value 12
	}
	control.32 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Depth'
		value 12
	}
	control.33 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.35 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.37 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 0
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value false
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
radeon
drm
af_packet
ppdev
ipv6
speedstep_ich
speedstep_lib
cpufreq_conservative
cpufreq_ondemand
cpufreq_stats
freq_table
cpufreq_userspace
cpufreq_powersave
sbs
button
ac
container
bay
dock
video
battery
sbp2
lp
snd_intel8x0
snd_ac97_codec
joydev
ac97_bus
snd_pcm_oss
snd_pcm
snd_mixer_oss
snd_seq_dummy
snd_seq_oss
pcmcia
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
parport_pc
parport
pcspkr
snd_timer
snd_seq_device
psmouse
serio_raw
iTCO_wdt
iTCO_vendor_support
snd
soundcore
snd_page_alloc
yenta_socket
rsrc_nonstatic
pcmcia_core
shpchp
pci_hotplug
intel_agp
agpgart
evdev
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
floppy
e100
mii
ohci1394
ieee1394
ata_piix
ata_generic
libata
scsi_mod
uhci_hcd
usbcore
thermal
processor
fan
fuse
apparmor
commoncap


```

---

### Post by spiderbatdad on 2008-04-20
```
asoundconf set-default-card I82801CAICH3

```
Reboot.

---

