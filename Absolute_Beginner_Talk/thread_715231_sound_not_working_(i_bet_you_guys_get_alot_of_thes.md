---
title: "sound not working (i bet you guys get alot of these)"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by xecure on 2008-03-04
well out of the blue my sound just stopped working. When I start up Ubuntu the sound plays after I login nothing plays (from rythmbox to youtube), on the other hand I have vista running under VirtualBox, and the sound works fine there.

Any ideas?

---

### Post by Crooksey on 2008-03-04
```

$ sudo alsamixer
```

Try turning the volume up in the alsa mixer

---

### Post by kebes on 2008-03-04
Does the sound stop working only when VirtualBox is running?

I've found that with sound enabled in VirtualBox, it always takes complete control of the sound device, preventing other programs from using it until I close the VirtualBox session.

---

### Post by xecure on 2008-03-12
I have another problem now, now my sound doesn't work period. Not even when i start up ubuntu, it does not even play the staring up sound.

---

### Post by erginemr on 2008-03-12
What is your sound card (on board, pci, what brand)?

The output of the following commands from the terminal:
```
aplay -l
```
```
lspci | grep -i audio
```
```
cat /proc/asound/cards
```
and the (error) message from:
```
alsamixer
```

---

### Post by xecure on 2008-03-13
The out put for
```
aplay -l
```gives me ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```the output for 
```
lspci | grep -i audio
```gives me```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```the output for 
```
cat /proc/asound/cards
``` gives me ```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 19

```
and when i type in 
```
alsamixer
``` I don't get an error just a little image of my volume bars.

---

### Post by Junglizer on 2008-03-13
Try running 
```
alsaconf
```
in the console, and make sure nothing is muted (m key) in ```
alsamixer
```

---

### Post by Oldsoldier2003 on 2008-03-13
[Comprehensive Sound Problems Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by erginemr on 2008-03-13
Your problem seems to match this one:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

Please enable backports, install the "linux-backports-modules-generic" package as suggested therein and reboot to see if it helps.

---

### Post by billgoldberg on 2008-03-13
Try download the gui for alsamixer called "gnome alsa mixer" it's alot easier if something gets mixed up.

---

