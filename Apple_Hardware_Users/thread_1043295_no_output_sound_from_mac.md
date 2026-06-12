---
title: "no output sound from mac"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by nitemon on 2009-01-18
Having checked my sound card, I have input but no output. When I turn on the pc it has the normal sound. Put that is all. Is there a simple remedy.

---

### Post by Chrisj303 on 2009-01-18
What sort of Mac are you using?

---

### Post by McFrostey on 2009-01-18
sound card and what type of computer do you have doesnt matter...
its just a bug in the PPC go to Applications>Accesories>Terminal

type "sudo modprobe snd-powermac"
then right click the volume button on the top tool bar and click "open volume control"
and control it from there =D

---

### Post by cyberdork33 on 2009-01-18
> **McFrostey said:**
> sound card and what type of computer do you have doesnt matter...
its just a bug in the PPC go to Applications>Accesories>Terminal

type "sudo modprobe snd-powermac"
then right click the volume button on the top tool bar and click "open volume control"
and control it from there =D
The type of computer does matter if her is not using a powerpc mac!

---

### Post by McFrostey on 2009-01-19
Most of the sound problems from sound not outputting is POWERPC so I assumed... PowerPC
...

---

### Post by cyberdork33 on 2009-01-19
> **McFrostey said:**
> Most of the sound problems from sound not outputting is POWERPC so I assumed... PowerPC
...
The Intel Macs have sound issues quite often.

---

### Post by Dunkintori on 2009-01-19
So I have the same problem (no sound). I have the new Macbook aluminum(the one with the trackpad) apple.com/macbook
I have tried to type in sudo modprobe snd-powermac and the console replies: Module powermac not found.
What else can I try?

---

### Post by Dunkintori on 2009-01-20
And I've gone to this page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
I've gone through all the steps, everything is fine. My audio card is: 


00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
        Subsystem: nVidia Corporation Device cb79
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at 93380000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

Is it not supported? Is it going to be supported any time soon?

---

### Post by cyberdork33 on 2009-01-20
Please make sure to identify your Macbook properly in the future, you have a Macbook5,1

The documentation for your Machine is here:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

---

### Post by Dunkintori on 2009-01-20
Thank you! And sorry for not being specific (i'm an idiot).

---

### Post by cyberdork33 on 2009-01-20
> **Dunkintori said:**
> Thank you! And sorry for not being specific (i'm an idiot).
No problem. It is just that there are a lot of Macbooks all with different hardware. Saying you version number let's us know exactly what you are dealing with.

---

### Post by Dunkintori on 2009-01-22
Well, ironically enough that link fixed all of my mac-related problems except sound:-). Right now I am trying to get my headphones to work, and this is what happens:

Gnome: I hear noise instead of sound. The noise gets louder when I turn the volume up and v.v. When I start alsamixer, there's only two items I can edit: Master and capture. There's supposed to be more, right?

KDE: I hear the nice music when I log in/out(hurray!), but nothing otherwise (mp3, video etc.)

Could you please point me in the direction where the problem might be?

---

### Post by cyberdork33 on 2009-01-22
Unfortunately, it is likely just a bug in the ALSA driver. You might try filing a bug report.

---

### Post by Dunkintori on 2009-01-22
Well, it turns out (as usually) that the problem was just me being stupid. I right-clicked on the volume control, chose preferences, then set the "device to control" to PCM, - and now I have sound!
So now the link that you gave me has fixed all of my problems! Thank you so much.

---

### Post by cyberdork33 on 2009-01-22
> **Dunkintori said:**
> Well, it turns out (as usually) that the problem was just me being stupid. I right-clicked on the volume control, chose preferences, then set the "device to control" to PCM, - and now I have sound!
So now the link that you gave me has fixed all of my problems! Thank you so much.
This worked for headphones as well as for speakers?

---

### Post by Dunkintori on 2009-01-22
Yeah.

---

### Post by jamesey on 2009-03-15
I'm having an issue on the new iMac, 9,1. Just bought it yesterday, 3-14-09. It's 20 inch. 

I went through the troubleshooting guide, here are my results

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

find /lib/modules/`uname -r` | grep snd
```
i wont paste them, but a load of *.ko files were found
```

lspci -v
```
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at d3580000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I went here [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

I think that is my video card
In terminal i typed
modinfo soundcore
and got

```
filename:       /lib/modules/2.6.27-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 

```

in terminal i did
gksudo gedit /etc/modprobe.d/options
and added "options snd_hda_intel model=mac24" 
I restarted and still no sound

---

