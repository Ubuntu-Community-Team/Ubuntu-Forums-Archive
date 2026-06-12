---
title: "Speaker / Headphone switching"
date: 2011-03-29
forum: Apple Hardware Users
---

### Post by sopranojam85 on 2011-03-29
Hi all,

I'm using Ubuntu 8.04.10 on an old PowerBook 3400c 240 MHz, 40 GB hard drive, 80 MB ram.

I did a bare-bones install with the PPC-Alternate disc, and am using FluxBox as my Window manager.

I used these steps to set up mocp for internet radio listening via the shell:
[http://www.doknowevil.net/2009/07/15/the-easy-way-to-listen-to-internt-radio-in-ubuntu/](http://www.doknowevil.net/2009/07/15/the-easy-way-to-listen-to-internt-radio-in-ubuntu/)

SO I then found that audio playback happened at max volume on both the built-in speakers and headphones. Connecting headphones does not switch off the audio to the headphones.

I know the headphone jack is fine, as it switches the audio fine when I boot to the native Mac OS 9.

Which pieces of Ubuntu do I work on to control audio volume, audio switching, etc etc?

P.S. I added blacklist pcspkr to /etc/modprobe.d/blacklist, but it still beeps twice when shutting down. WHat the hell do I have to do to disable this?

---

### Post by pauljwells on 2011-03-29
I found the headphones and speakers act a bit 'funny' too on a Powermac G5. I fixed it by running alsamixer and systematically muting and unmuting the various channels until it worked - I haven't found an 'automatic' fix yet, I have to use this manually anytime I plug in the headphones

---

### Post by sopranojam85 on 2011-03-29
Now I find that "Headphone Detection" is off, and highlighting it, pressing "m" to un-mute headphone detection is not working.

It's almost like I've got the wrong drivers for my sound hardware or something.

I'm attempting a solution documented here: [http://ubuntuforums.org/showthread.php?t=738275](http://ubuntuforums.org/showthread.php?t=738275)

---

### Post by linuxopjemac on 2011-03-29
This is also a helpful place:
[http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html](http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html)

---

### Post by sopranojam85 on 2011-03-30
No such luck.

Tried both these sites' workarounds/solutions. 

typing lsmod | grep snd

```
snd_powermac            50336     0
snd_pcm                                    87812     1  snd_powermac
snd_timer                                  26820     1  snd_pcm
snd                                             70548     3  snd_powermac,snd_pcm,snd_timer
soundcore                                   9028      1  snd
snd_page_alloc                         12040     1  snd_pcm

```

Any clues where I should head?

This guy's got something listed out, but instructions are vague: [http://www.rockhopper.dk/old/linux/hardware/powerbook-3400.html#chap3_sect2](http://www.rockhopper.dk/old/linux/hardware/powerbook-3400.html#chap3_sect2)

---

### Post by sopranojam85 on 2011-04-12
For what it's worth, I've run 

/dev/sndstat

Here's the output:

> Sound Driver: 3.8.1a-980706 (ALSA v1.0.15 emulation code)
Kernel: Linux 3400c 2.6.24-19-powerpc #1 Wed Jun 18 14:14:12 UTC 2008 ppc
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
PowerMac AWACS [PB3400] Rev 0

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG

---

