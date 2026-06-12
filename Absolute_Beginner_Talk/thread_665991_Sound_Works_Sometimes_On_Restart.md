---
title: "Sound Works Sometimes On Restart"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-01-12
I installed Gusty Gibbon Recently on my brothers machine, I had that audio working the first time, but now when he restarts, either proper restart or forced, the sound sometimes work  and sometimes it doesn't is this common, and what can i do to diagnose, the sound card works in xp. I have Ubuntu as my main machine and everything runs smoothly on it. 

Here Is my Setup

> austin@austin-desktop:~$ aplay -l
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
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
austin@austin-desktop:~$ 

00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

---

### Post by RomeReactor on 2008-01-12
Hi. Try disabling the integrated card in the PC's BIOS.

---

### Post by szymon_g on 2008-01-12
did you installed alsa-firmware-loader and alsa-utils on it? it helped me with similar problem on laptop with intel card

---

### Post by anderskitson on 2008-01-12
Yep I disabled the sound card in the bios and no luck, i will try the alsa commands next

---

### Post by RomeReactor on 2008-01-12
Go to 'System->Preferences->Sound', and on the first tab (Devices), from the **Default Mixer Tracks** dropdown menu select **CA0106** and below that, select "Analog Front" as the channel. Then right-click on the volume applet in the top panel, select "Preferences" and do the same.

---

### Post by anderskitson on 2008-01-12
Ok well there seems to be a weird trait as of late, when i restart and the audio works the keyboard doesn't now i have tried the keyboard in different usb ports, and different keyboards with ps/2 connections. So when the keyboard works no audio and vice a versa, except the odd time that both work. They both work in xp, im stumped.

---

### Post by anderskitson on 2008-01-12
ok well i just noticed you replied, right now CA0106 is selected but > iec958 unknown is selected and the audio is working

---

### Post by RomeReactor on 2008-01-12
Do you have an AMD processor? you may need to add some parameters to your **/boot/grub/menu.lst** file.

EDIT: Posted late. If both sound and keyboard work now, disregard this post.

---

### Post by anderskitson on 2008-01-12
Amd Athalon 3000+,
well keyboard and sound have worked together but only sometimes

---

### Post by RomeReactor on 2008-01-14
If the problem isn't solved yet, try blacklisting the other card: from the terminal run:
```
asoundconf list
```
And please post the result. You should get **CA0106** (the SB card) and the Via card. Now run:
```
gksudo gedit /etc/modprobe.d/blacklist
```
And add this to the bottom:
```
blacklist snd_via82xx
```
Save the file, reboot, and see if the problem is still there.

---

### Post by anderskitson on 2008-01-14
All right I'm going to try this tomorrow morning my brothers asleep and the computers  is in his room. So is it possible that sometimes this card I am blacklisting is taking priority and sometimes not, explaining the booting problem. the one that is working is the ca0106

---

