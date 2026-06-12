---
title: "[SOLVED] duel boot, no sound"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mangurt on 2008-01-03
Greetings all,
I have a rather odd problem.  I got my system up and running via duel boot, and now I do not have any sound in ubuntu.  I had sound during the installation (off of the live disk), and I also had sound when my system was ubuntu.  I did a clean install of windows XP, and then ubuntu 7.10.
Any help would be greatly appreciated.
Thanks

---

### Post by RomeReactor on 2008-01-03
Hi. What sound card do you have in the system? please open a terminal (Applications->Accessories->Terminal) and run the following:
```
aplay -l
```
```
sudo lshw -C multimedia
```
and
```
lspci | grep Multimedia
```
if you can't see your soundcard there, run lspci without any parameters:
```
lspci
```
and please post the output.

---

### Post by mangurt on 2008-01-04
Here's the information from all the codes.

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [SBLive! Value [SB0101]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
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
card 2: Live [SBLive! Value [SB0101]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SBLive! Value [SB0101]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

  *-multimedia:0          
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:1
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
  *-multimedia:2
       description: Multimedia controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
       vendor: Conexant
       physical id: c.1
       bus info: pci@0000:00:0c.1
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=cx88_audio latency=32 maxlatency=255 mingnt=4 module=cx88_alsa
  *-multimedia:3 UNCLAIMED
       description: Multimedia controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
       vendor: Conexant
       physical id: c.2
       bus info: pci@0000:00:0c.2
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=88 mingnt=6
  *-multimedia:4
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx

00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0c.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0c.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
ed@ed-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0c.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0c.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

Thanks again.

---

### Post by RomeReactor on 2008-01-04
If you're currently using the SoundBlaster card, try disabling the onboard in your PC's BIOS. Also, right-click on the volume applet in the top panel, select "Preferences" and from the dropdown list see if **SB0101** is selected. Now right-click the volume again and select "Open Volume Control", go to "Edit->Preferences" and check all the channels there. Now start to play an audio file, and play with the levels of the channels and see if one of those lets you control the volume.

EDIT: From the output it looks like the soundblaster *is not* the default soundcard.

---

### Post by mangurt on 2008-01-04
Ok, I did like you suggested, and I still don't have any sound.  I tried to go into the CMOS and disable the onboard sound card, but that did not work.

---

### Post by RomeReactor on 2008-01-04
Try running:
```
asoundconf list
```
and post the output. Most likely the **SB0101** won't be the first one; if this is the case, to make it the default card run:
```
sudo asoundconf set-default-card SB0101
```
and reboot.

From what I've seen, SB Live cards are tricky to get going...

---

### Post by kpkeerthi on 2008-01-04
Open a terminal and type **alsamixer**. Make sure the channels are not muted. Press 'm' key to unmute.

---

### Post by mangurt on 2008-01-04
Ok, I will look into this when I get home (currently at work).  I will post the results when I get home.

---

### Post by mangurt on 2008-01-04
Here's the results from asoundconf list

ed@ed-desktop:~$ asoundconf list
Names of available sound cards:
V8237
CX8801
Live


I guess I need to make live default?

---

### Post by RomeReactor on 2008-01-04
Yes, run the command like this:
```
sudo asoundconf set-default-card Live
```

Also, you need to blacklist the other two cards; for that, open the **/etc/modprobe.d/blacklist** file in gedit with administrator privileges:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and add at the end of the file:
```
blacklist V8237
blacklist CX8801
```

Then reboot.

---

### Post by mangurt on 2008-01-04
Ding Ding Ding....we have a winner!

Thanks for the help....I have sound!

---

