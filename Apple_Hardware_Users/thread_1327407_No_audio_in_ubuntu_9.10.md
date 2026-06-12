---
title: "No audio in ubuntu 9.10"
date: 2009-11-15
forum: Apple Hardware Users
---

### Post by Paperfish on 2009-11-15
Hi there! 

I've just installed ubuntu 9.10 on my macbook pro, and the audio doesn't seem to be working. 

Really not sure how to got about fixing this. Can anyone offer any advice?

---

### Post by tom4everitt on 2009-11-15
Did you try this guide:

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by Bunnybugs on 2009-11-15
> **tom4everitt said:**
> Did you try this guide:

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)


The solution is to remove the driver of the software modem...

Go to: System>Administration>Hardware Drivers, Remove the 'Software Modem' Driver, reboot your computer, and sound should work fine!

---

### Post by Paperfish on 2009-11-15
Hiya! Yup, I managed to find that guide. I've got a '3.1' model laptop, and the karmic page states that the sound should work fine! :(

---

### Post by Paperfish on 2009-11-15
Hi Bunnybugs!

I just had a look at the Hardware Drivers window, and there's nothing in there that mentions the 'Software Modem' driver. :( It's just stuff to do with my nvidia card.

---

### Post by Bunnybugs on 2009-11-15
check this out... it should work... worked for everybody that asked me the same question!

[http://ubuntuforums.org/showthread.php?p=8322450](http://ubuntuforums.org/showthread.php?p=8322450)

---

### Post by Bunnybugs on 2009-11-15
Ah, okay... that's a little weird... try [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Rich_Roast on 2009-11-15
All I can think of is to check the device is working:

```
aplay -l
```

and then check volume control for the device that should be working and make sure that all the mixer levels are not muted and at an audible level. If Linux distros received a penny for all the times these levels get mysteriously set to 0 there would be no need for donations.

---

### Post by Bunnybugs on 2009-11-15
> **Rich_Roast said:**
> All I can think of is to check the device is working:

```
aplay -l
```and then check volume control for the device that should be working and make sure that all the mixer levels are not muted and at an audible level. If Linux distros received a penny for all the times these levels get mysteriously set to 0 there would be no need for donations.

Yeah, sounds nice... but you can check that out by using the command ```
alsamixer
```

First check if your device is listed, then check alsa

---

### Post by Paperfish on 2009-11-15
Yup! aplay -l listed audio things:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer shows the levels to all be at 100. Very odd. 

Currently looking at that comprehensive sound problems guide that bunnybugs posted. 

Will report back.... !

---

### Post by Bunnybugs on 2009-11-15
Well. wish you luck with that guide... it's long, and boring... but it could work

---

### Post by Paperfish on 2009-11-15
Sifted through parts of that guide.
It basically led me to double/triple-checking my alsamixer. 

Figured I might throw this line in a terminal and see what happens...
sudo apt-get dpkg-reconfigure alsa-source

---

### Post by Paperfish on 2009-11-15
After a little more detective work, I've found that alsa doesn't actually support my sound card.... at all.

Found my card detail with a lspci -v:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Device 00a0
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


and on the elsa site, i've found that the ICH8 family isn't supported:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)


Out of curiousity, i tried adding the hda intel driver to the kernel anyway, with 'sudo modprobe snd-hda-intel'. No change.

Is that the bottom line you think? It's just not supported?

---

### Post by Bunnybugs on 2009-11-16
> **Paperfish said:**
> After a little more detective work, I've found that alsa doesn't actually support my sound card.... at all.

Found my card detail with a lspci -v:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Apple Computer Inc. Device 00a0
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


and on the elsa site, i've found that the ICH8 family isn't supported:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)


Out of curiousity, i tried adding the hda intel driver to the kernel anyway, with 'sudo modprobe snd-hda-intel'. No change.

Is that the bottom line you think? It's just not supported?

I find that rather impossible... I have an ICH8-family soundcard, and it is really supported by the alsa-kernels:s

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1339
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```And yeah, it really works here!

---

