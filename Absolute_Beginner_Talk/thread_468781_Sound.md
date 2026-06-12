---
title: "Sound"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by reecedeg on 2007-06-09
I have a new Lenovo 3000 N100. I have installed Feisty w/o running windows. I cannot get any sound. I am a newbie and would appreciate any help I can get. Thanks 

 List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

        Subsystem: Lenovo Unknown device 2066

        Flags: bus master, fast devsel, latency 0, IRQ 21

        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>

---

### Post by ggaaron on 2007-06-09
IntelHD should work - are you sure that mixer isn't muted? Run alsamixer from console and see if it works. Are you trying to play some music? What player are you using?

---

### Post by mills on 2007-06-09
this usually sorts sound problems out

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by reecedeg on 2007-06-10
> **ggaaron said:**
> IntelHD should work - are you sure that mixer isn't muted? Run alsamixer from console and see if it works. Are you trying to play some music? What player are you using?

I have opened and checked all in both mixers some say auto, and increased volume. I am trying to play music on the Rhythmbox music player, a cd and from utube and such no sound of any kind.  I don't see how downloading another driver would help since my system is brand new do you? I sure appreciate your help.Thanks--Reece

---

### Post by Harpoon on 2007-08-04
Just a guess, but you have to have the modem enabled for sound to work.  Some resources are shared between soundcard and modem.

---

