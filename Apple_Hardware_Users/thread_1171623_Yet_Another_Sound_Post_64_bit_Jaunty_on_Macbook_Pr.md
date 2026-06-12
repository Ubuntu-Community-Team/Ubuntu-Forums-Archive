---
title: "Yet Another Sound Post: 64 bit Jaunty on Macbook Pro Penryn 4,1"
date: 2009-05-27
forum: Apple Hardware Users
---

### Post by MaddMatt on 2009-05-27
Hi All, 

So to join into the clutter of sound posts, I have to see if I can find something that works. 

So far I have tried everything outlined here:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
and here:
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")
As well as several other forums and posts.

I recompiled the ALSA drivers from scratch, modified my modprobe.d, uninstalled drivers, reinstalled drivers, installed pulse audio server, so on and so forth. All of my levels have been checked and rechecked and are not muted, and as far as I can tell, the drivers are all tip top- just no sound! For two weeks!

Also weird: The digital seems to be on all the time, as my headphone port is putting out a red light the whole time its on. 

Some stats:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Device 00a4
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


```

This is really annoying, so hopefully someone else has gone though this. The Penryn wiki right now declares that everything usually works tip-top on an install... Any ideas? 

Cheers, 
m

---

### Post by _mario_ on 2009-05-28
> **MaddMatt said:**
> 
This is really annoying, so hopefully someone else has gone though this. The Penryn wiki right now declares that everything usually works tip-top on an install... Any ideas? 


i'm running the same ubuntu version on the same machine and didn't have any sound problems since intrepid. (besides a crashing/buggy pulseaudio of course ;-)). to tackle your problem i'd like to ask a few questions:
[LIST=1]
[*]do the speakers work? using another OS?
[*]did you add the required module option for snd_hda_intel?
[*]if you suspect the pulseaudio sound server, you might also deinstall the package to test plain ALSA audio output. does it work then?
[/LIST]

in order to to turn off the digital output, you can run:
```

amixer set IEC958 off

```
either manually or add this line to /etc/rc.local and change its permissions to executable.

ciao,
Mario

---

### Post by MaddMatt on 2009-05-29
Hi Mario, 

Thanks for the tips. Since you said the original drivers worked for you, I decided to try them again (even though they didn't work for me on fresh install...) so I ran 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

and it remedied the sound as well as the digital audio. The sound levels are quite low, though, but I used pulse audio to boost them by 400% and that brought them back to normal. I've never used pulse audio in the past- I just installed it because it was recommeneded by some of the forums I was relying on. it's possible I fubar'd my system with all of the extra packages I installed trying to fix my sound... hmmm. Thanks for the help!
m

---

### Post by pmaciver on 2009-05-31
Could you explain how you used Pulse to boost your audio.
I am in real need of this, although I am running 32 bit.

> **MaddMatt said:**
> Hi Mario, 

Thanks for the tips. Since you said the original drivers worked for you, I decided to try them again (even though they didn't work for me on fresh install...) so I ran 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

and it remedied the sound as well as the digital audio. The sound levels are quite low, though, but I used pulse audio to boost them by 400% and that brought them back to normal. I've never used pulse audio in the past- I just installed it because it was recommeneded by some of the forums I was relying on. it's possible I fubar'd my system with all of the extra packages I installed trying to fix my sound... hmmm. Thanks for the help!
m

---

### Post by MaddMatt on 2009-05-31
Hi pmciver, 

I used this command:
```

$ sudo apt-get install padevchooser vlc-plugin-pulse pulseaudio-module-lirc libsdl1.2debian-all libao2 asoundconf-gtk gnome-alsamixer alsa-oss ubuntu-restricted-extras

```
to get pulse audio everything, and then up in the right, after you reboot is a pulse-audio applet of sorts. In there you can click "manage", select your card, and hit "properties" to pump up audio. 

However, when I uninstalled pulse and everything else I had added to get sound, it seemed to have worked... so maybe try that. Good luck!
m

---

### Post by _mario_ on 2009-06-02
> **MaddMatt said:**
> 
..., but I used pulse audio to boost them by 400% and that brought them back to normal.


sound volume shouldn't be lower as usual if you added 
```

options snd_hda_intel model=mbp3

```
to some file in /etc/modprobe.d and updated your ramdisk as indicated by the mactel documentation. however, if it works for you using pulseaudio (is the quality and/or performance impact acceptable?), it's fine.

ciao,
Mario

---

