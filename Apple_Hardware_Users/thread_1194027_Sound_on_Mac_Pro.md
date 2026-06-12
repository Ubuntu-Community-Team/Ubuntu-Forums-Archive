---
title: "Sound on Mac Pro"
date: 2009-06-22
forum: Apple Hardware Users
---

### Post by fatum on 2009-06-22
On my early 2008 Mac Pro dual quad core I can get sound through VLC if I change the audio to A/52 over S/PDIF in the audio dropdown menu. This is getting sound through the toslink digital output to my stereo. Normal sound for the OS does not work and the sound through web does not work. What am I missing? I updated the alsa driver to the latest 1.0.20

lspci -v gives this output for audio 

00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 90b04000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

alsa driver was compiled and installed with hda-intel flags. Sound is not muted through the volume control.

---

### Post by Kver on 2009-07-27
> **fatum said:**
> On my early 2008 Mac Pro dual quad core I can get sound through VLC if I change the audio to A/52 over S/PDIF in the audio dropdown menu. This is getting sound through the toslink digital output to my stereo. Normal sound for the OS does not work and the sound through web does not work. What am I missing? I updated the alsa driver to the latest 1.0.20

lspci -v gives this output for audio 

00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 90b04000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

alsa driver was compiled and installed with hda-intel flags. Sound is not muted through the volume control.

I'm also having the exact same problem.

---

