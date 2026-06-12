---
title: "another different trouble with sound on Feisty"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by thinkren on 2007-10-08
I've been using a brand new install of feisty for a few days with great satisfaction.  There was no problem with sound until I created a second user account with:

[FONT="Tahoma"]sudo adduser sen[/FONT]

The account seemed to have been created with no problems but the sound icon on the top menu bar is crossed out.  When I right click and try to access volume control, the following message is displayed:

[FONT="Tahoma"]No volume control GStreamer plugins and/or devices found.[/FONT]

This is very strange as the original account created during installation played sound just fine.

I tried a few thing in the sound troubleshooting guide but can't identify any obvious problems.  Below is the terminal output.  can anyone suggest anything else I might try to narrow down the problem?  Thanks for any suggestions.

-ren

[FONT="Tahoma"]sen@ren-desktop:~$ aplay -l
aplay: device_list:222: no soundcards found...
sen@ren-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        Memory behind bridge: fca00000-feafffff
        Prefetchable memory behind bridge: f0700000-f47fffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fc900000-fc9fffff
        Prefetchable memory behind bridge: f0600000-f06fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 01) (prog-if 80 [Master])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at ef80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 01)
        Subsystem: Intel Corporation Unknown device 4541
        Flags: medium devsel, IRQ 9
        I/O ports at efa0 [size=16]

01:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: 3Com Corporation 3C905C-TX Fast Etherlink for PC Management NIC
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dc00 [size=128]
        Memory at fc9ff800 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at f0600000 [disabled] [size=128K]
        Capabilities: <access denied>

01:0b.0 Communication controller: Agere Systems 56k WinModem (rev 01)
        Subsystem: Unknown device 141c:9300
        Flags: bus master, medium devsel, latency 0, IRQ 3
        Memory at fc9ffc00 (32-bit, non-prefetchable) [size=256]
        I/O ports at dff0 [size=8]
        I/O ports at d800 [size=256]
        Capabilities: <access denied>

01:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 64, IRQ 9
        I/O ports at df00 [size=64]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0001
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f2000000 (32-bit, prefetchable) [size=32M]
        Expansion ROM at feaf0000 [disabled] [size=64K]
        Capabilities: <access denied>

sen@ren-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
sen@ren-desktop:~$ lsmod | grep snd
snd_ens1371            27552  0 
gameport               16520  1 snd_ens1371
snd_ac97_codec         98464  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  1 snd_pcm
sen@ren-desktop:~$[/FONT]

---

### Post by thinkren on 2007-10-08
I should add that before logging on, I can hear the bongo drums.  But once I enter the newly created account, the jungle fanfare that usually accompanies the logon process does not sound.  It seems the failure of audio is strongly associated with the additional user account, but I have no idea how and what to do to fix it.

---

