---
title: "Help with SB Audigy installation"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by siltin on 2006-09-03
Hi All,

First post here and completely new to Ubuntu and Linux. 
My issue is that I can't get my SB Audigy to work. 
Ubuntu was able to detect my onboard VIA soundcard and it works fine but I'd like to use my SB Audigy if possible. I've tried looking online for various solutions mainly from 

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1)

and the Comprehensive Sound Problem Solutions Guide at [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

I've tried to follow the instructions but I still can't choose to use my SB audigy card. I don't know if its because i've followed the instructions incorrectly or if theres something i'm totally missing.

I have a PCI Sound Blaster Audigy Platinum card which works under Windows (dual boot system now). So from the docs I mentioned above i tried using the emu10k1 driver. I could not see my SB under alsamixer. When following the Comprehensive Sound Problem Solutions Guide I've also tried to follow the sections "Getting the ALSA drivers from a *fresh* kernel" and once I tried "aplay -l" my SB wasnt listed. Then I proceeded to follow the "ALSA driver Compilation" section... when I performed the "sudo module-assistant a-i   alsa-source" command it completed with 100% success. No error messages. Anyways, after all that I still can't get it working. Any advice would be great! Tks!

Anyways, heres more details:
*******************************************************************

gcmyu@gcmyu-linux-home:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gcmyu@gcmyu-linux-home:~$

*******************************************************************

gcmyu@gcmyu-linux-home:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M266 Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e4000000-e6ffffff
        Prefetchable memory behind bridge: c0000000-dfffffff
        Capabilities: <available only to root>

0000:00:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Linksys: Unknown device 0013
        Flags: bus master, fast devsel, latency 32, IRQ 193
        Memory at e7004000 (32-bit, non-prefetchable) [size=8K]

0000:00:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: medium devsel, IRQ 209
        I/O ports at c000 [size=32]
        Capabilities: <available only to root>

0000:00:07.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at c400 [size=8]
        Capabilities: <available only to root>

0000:00:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at e7006000 (32-bit, non-prefetchable) [size=2K]
        Memory at e7000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 185
        I/O ports at c800 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 185
        I/O ports at cc00 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 185
        I/O ports at d000 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at e7007000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at d400 [size=16]
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7870
        Flags: medium devsel, IRQ 225
        I/O ports at d800 [size=256]
        Capabilities: <available only to root>

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device c01c
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at e000 [size=256]
        Memory at e7008000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81ea
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 201
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=512M]
        Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at e6000000 [disabled] [size=128K]
        Capabilities: <available only to root>
*******************************************************************

gcmyu@gcmyu-linux-home:~$ lsmod | grep emu10k1
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_emu10k1           117284  1 snd_emu10k1_synth
snd_rawmidi            25504  5 snd_usb_lib,snd_mpu401_uart,snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         93088  2 snd_via82xx,snd_emu10k1
snd_pcm                89864  5 snd_usb_audio,snd_via82xx,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  3 snd_via82xx,snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  3 snd_usb_audio,snd_emux_synth,snd_emu10k1
emu10k1_gp              3840  0
snd                    55268  18 snd_usb_audio,snd_via82xx,snd_mpu401_uart,snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
gameport               15496  3 snd_via82xx,emu10k1_gp
gcmyu@gcmyu-linux-home:~$


*******************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
snd-emu10k1
*******************************************************************
gcmyu@gcmyu-linux-home:~$ sudo gedit /etc/esound/esd.conf

File looks like below

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
*******************************************************************
sudo gedit /etc/asound.conf

File looks like below:

pcm.emu10k1 {
           type hw
           card 0
        }

        ctl.emu10k1 {
           type hw
           card 0
        }

*******************************************************************

---

### Post by macdo on 2006-09-03
What happens if you run ```
alsamixer -c 1
```

Just guessing here, you understand...

---

### Post by bodhi.zazen on 2006-09-03
I have this card and it is working for me.

You have the corect driver.

What happens whne in a terminal you type:

alsamixer -c 1 ?

In you mixer there are a few choices -> there is a tab to select devices.

also (sounds funny) check that the device is not muted.

---

### Post by siltin on 2006-09-03
Thx for the quick reply guys! Anyways I tried alsamixer -c 1
and basically I get the following:

Card: USB Device 0x46d:0x8b4
Chip: USB Mixer
View Playback Capture All

Under the Playback i theres not option to change. I tried the Capture and All Views then increased the settings. Anyways, I still dont this is the correct card I need or chip setting.

Bodhi.Zazen if its not too much trouble are you able to recall what you did? Or possibily send me any config files you set? 

Anyways If anyone else has any suggestions please let me know. Tks guys really hope I can get this working so that I not too turned off with the Linux experience.

---

### Post by bodhi.zazen on 2006-09-03
What program are you using?

It looks like the hardware is working, under the mixer there are some options, again make sure you are not muted.

In xmms, audacity, etc you need to set your card as the output.

---

