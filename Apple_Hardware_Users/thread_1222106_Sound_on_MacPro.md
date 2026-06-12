---
title: "Sound on MacPro"
date: 2009-07-24
forum: Apple Hardware Users
---

### Post by dschoerl on 2009-07-24
Hi there, 

I have installed Ubuntu on my new Mac Pro (dual-boot). We got everything working except the sound.

We tried all common approaches, installing new drivers, etc. but all of them failed. It seems that the set-up of the card is fine.
Everything seems to work fine, but unfortunately no sound is played...

The hardware is according to the alsa script:
[FONT=Courier New]
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC889A Analog [ALC889A Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1[/FONT]

And [FONT=Courier New]lspci -v | less[/FONT] gives:

[FONT=Courier New]00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 8b420000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel[/FONT]


Would be great if anyone has an idea, how to solve the problem!

Thanks!

---

### Post by LowSky on 2009-07-24
go to sound icon, right click and pick  preferences, now go to options and add FRONT, make sure its on and all the way up and not muted. That should do the trick.

---

### Post by dschoerl on 2009-07-28
Sorry but this did not solve the problem! There is still no sound.

Thanks!

---

### Post by dschoerl on 2009-07-30
Just some further information: ```
hwinfo --sound
``` gives:

```
30: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3a3e
  Unique ID: u1Nb.tbGLr+gVGM8
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel ICH10 HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3a3e "ICH10 HD Audio Controller"
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x8b420000-0x8b423fff (rw,non-prefetchable)
  IRQ: 22 (1951 events)
  Module Alias: "pci:v00008086d00003A3Esv00000000sd00000000bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```It is really strange but there is no way to get some sound out of my Mac under Ubuntu, although it seems all configured allright.

Does anyone has any idea? Would be great!!!

Thanks so much!

---

### Post by bluecitabria on 2009-08-05
> **dschoerl said:**
> Hi there, 

I have installed Ubuntu on my new Mac Pro (dual-boot). We got everything working except the sound.

We tried all common approaches, installing new drivers, etc. but all of them failed. It seems that the set-up of the card is fine.
Everything seems to work fine, but unfortunately no sound is played...

The hardware is according to the alsa script:
[FONT=Courier New]
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC889A Analog [ALC889A Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1[/FONT]

And [FONT=Courier New]lspci -v | less[/FONT] gives:

[FONT=Courier New]00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 8b420000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel[/FONT]


Would be great if anyone has an idea, how to solve the problem!

Thanks!

assuming that this is a 2009 dual nehalem based mac-pro,
adding "options snd-hda-intel model=imac24" as a seperate line to /etc/modprobe.d/alsa-base.conf
will get the sound working through the rear analog output, but not the front.

---

### Post by Visgodred on 2009-09-22
Hello,

I am having the same problem. This is my first real shot at Linux as a total newb. I am in need of a little guidance on the CLI.

I found this link

[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

and it looks like it would solve this problem except that I am not familiar enough with command line to understand where the instructions want me to fill in blanks and whether I should or should not type in all the characters. 

If this is not the place to ask for this kind basic breakdown please point me in the right direction and accept my apologies. But if it is the right place I would be really grateful for a closer breakdown of the instructions.

Visgodred

---

### Post by Signal64 on 2009-10-04
dschoerl - don't know if you ever got an answer to your problem.

Can you confirm the mac pro model and attach the codec dump?

Codec dump file is usually found at: /proc/asound/card0/codec#0

---

