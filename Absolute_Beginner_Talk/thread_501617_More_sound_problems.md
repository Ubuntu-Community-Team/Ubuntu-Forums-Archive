---
title: "More sound problems"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by fedira on 2007-07-15
Hi, 

When I first installed Feisty (about 3 weeks ago), my sound worked fine from the get-go. I installed the codecs I wanted, and still no problems. Then one day, about a week ago, it stopped working. When I went into alsamixer, it turned out the master volume had been muted (somehow); I unmuted and all was well.

Now, after coming back from a hibernate, all sound is gone. I rebooted and nothing, not even a login sound. 

Here's what I've tried so far:

> aplay -l
returns:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Even though sound card seemed to fine, I tried a purge/reinstall anyway:

> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
> sudo apt-get install linux-sound-base alsa-base alsa-utils

I rebooted and still nothing. I went into alsamixer, turned everything way up, made sure nothing was muted, and still nothing.

I tried
> grep 'audio' /etc/group
and my username was found.

I'm only a newbie, all of these steps came from the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449"), and now I don't know what else to try. I can't stand not having sound, since I listen to music constantly. Any ideas? What can I try next? I'd be infinitely grateful for any help. Thank you!

---

### Post by Happy_Man on 2007-07-15
Hmm.... I don't know what to say, except that maybe your sound card's on the fritz? Can you test this in Windows, perhaps?

---

### Post by fedira on 2007-07-15
Oh no... now I have no sound in Windows either now. I've never had a problem there, and my computer (a Thinkpad X60s) is nearly brand new. I don't know if this is possible, but could Ubuntu have somehow messed up my physical sound card? Why else would it not work in Windows either?

I also just tried:

> sudo apt-get update && sudo aptitude dist-upgrade
reboot

with no luck. Any other suggestions?

---

### Post by fedira on 2007-07-15
Also,

```
cat /proc/asound/modules
```
says:
```
 0 snd_hda_intel

```

Is there anything I can check that might help diagnose this problem? I've followed this whole thread: [http://ubuntuforums.org/showthread.php?t=457373&page=3](http://ubuntuforums.org/showthread.php?t=457373&page=3) and nothing seems to work for me.

---

### Post by fedira on 2007-07-15
I also just remembered I recently installed MPlayer & the MPlayer plugin... could this be at all related?

Any help, anyone?

---

### Post by BobLand on 2007-07-16
fedira,
Judging by the output of aplay -l it appears you are using the sound chip on the motherboard.  If that is the case I'm not sure any of the procedures you've read so far will help.  The few posts I've seen regarding sound chips involved a different set of procedures.

Have you verified that your driver is indexed in /etc/modprobe.d/alsa-base?

I'm not an expert, just someone who found a way to keep sound going when it gets lost, so take my words with a grain of salt. 

oops!  I reread your post and you're using a laptop.  Is it possible the chip went bad?  Are you still under warranty?

bobland

---

