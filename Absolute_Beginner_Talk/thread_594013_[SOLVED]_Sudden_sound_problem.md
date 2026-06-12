---
title: "[SOLVED] Sudden sound problem"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Utimer on 2007-10-27
Hello all,

Yesterday my sound suddenly stopped working. During a session I was watching some movies, and as I started a new one it had no sound. 

I figured something weird had happened to the sound server, so I rebooted. Still no sound. 

Trying to test the sound from the sound preferences panel results in this:

Using ALSA:
No error, but no sound either

Using OSS:
Every time I click test, the bar comes up (no errors), but there is only a very short (~0.1 sec) "burst" coming out of the speakers.

Output of 
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Using the alsamixer shows nothing is muted.

A 'grep 'audio' /etc/group' will reveal I am in the audio group.

I already tried:

*Re-install of most of the stuff:*
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
sudo apt-get install hibernate
sudo apt-get install gdm-themes xserver-xephyr xnest

*Attempt to reset back to defaults*
sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils
sudo dpkg-reconfigure libasound2
asoundconf list
asoundconf set-default-card CK804
sudo dpkg-reconfigure libesd-alsa0
sudo dpkg-reconfigure libao2
sudo dpkg-reconfigure linux-sound-base
asoundconf unset-pulseaudio

I am using 
Ubuntu 7.10:Ubunty (uname -a: Linux utimer-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux)

The hardware does work perfectly well, as does audio on the live cd. Untill yesterday, the sound on this system worked perfectly well as well. 

I already tried various guides on this forum, but none have improved the situation I'm in.

I would much appreciate it if anyone could give me a pointer a new direction to look for the cause of this problem, since I wouldn't know how to fix it, short of a re-install (which I consider an overkill-solution)


Edit:
Solved
In IEC958 playback source, the box was set to PCM. Setting it to Analog In, resolved the problem.

---

