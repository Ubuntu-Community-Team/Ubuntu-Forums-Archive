---
title: "No sound on Macbook Pro 3,1"
date: 2009-10-23
forum: Apple Hardware Users
---

### Post by suffah on 2009-10-23
Running a late 2007 model MBP (3,1) and can't get sound to work.  Wiki says sound should be working out of the box.

I've loaded different kernels with the same result.

I've checked alsamixer and made sure nothing was on mute.

I've tried reinstalling alsa but it created a big mess of things so I reformatted and reloaded ubuntu.

I've also tried both headphones and the built in speakers.

Attached are screenshots of the sound screens and alsamixer.

**Any advice would be appreciated!**

```
charlie@charlie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
charlie@charlie-laptop:~$ lspci -v | less
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controll
er (rev 03)
        Subsystem: Apple Computer Inc. Device 00a0
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at db500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

```
charlie@charlie-laptop:~$ asoundconf list
Names of available sound cards:
Intel
```

---

### Post by suffah on 2009-10-25
Solved it!!!!!!!!!!!!!

I added **options snd-hda-intel model=mbp3 **to the end of my /etc/modprobe.d/alsa-base.conf file. 

Sound works great now.  Hope this helps someone.

---

### Post by hardaur on 2009-11-14
It did, thanks!

H

---

### Post by linuxopjemac on 2009-11-14
Someone should document this all and make a sticky out of all this useful information. Now that I write this I realize that I could also do that, but I'm not part of the Mactel Ubuntu group...

---

### Post by Odin Overland on 2009-11-14
> **suffah said:**
> Solved it!!!!!!!!!!!!!

I added **options snd-hda-intel model=mbp3 **to the end of my /etc/modprobe.d/alsa-base.conf file. 

Sound works great now.  Hope this helps someone.

I'm not following what you did to solve this exactly.  My MacBook has the sound playing perfectly, but my home iMac doesn't have any sound.  I tried some of your commands without any success, but I don't understand what you did for you final fix.

---

### Post by linuxopjemac on 2009-11-14
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
then add that line at the end then CTRL-O and then CTRL-X, then restart.

---

### Post by Forgott3n on 2009-11-29
I found I needed to do this myself to get my MacBook Pro 3,1 sound too.

Running 9.10...

Methinks this may need to be documented on the Wiki install somewhere.

---

### Post by struppi on 2009-12-04
> **suffah said:**
> Solved it!!!!!!!!!!!!!

I added **options snd-hda-intel model=mbp3 **to the end of my /etc/modprobe.d/alsa-base.conf file. 

Sound works great now.  Hope this helps someone.

model=mbp3 works for my MacBookPro4,1 too, thanks!

---

### Post by almahtar on 2009-12-08
Worked like a charm - thanks. 17" Macbook pro 3,1. Ubuntu 9.10.

---

