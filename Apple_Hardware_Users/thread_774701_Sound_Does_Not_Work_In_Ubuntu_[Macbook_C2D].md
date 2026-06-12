---
title: "Sound Does Not Work In Ubuntu [Macbook C2D]"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by jatoskep on 2008-04-29
My sound does not work at all in Ubuntu 8.04.

It is a C2D Black Macbook. I tried the fix shown in the Macbook Santa Rosa guide, but it did not work:

To resolve, add the following to /etc/modprobe.d/options:

```
options snd_hda_intel model=mbp3 
```

Any suggestions?

---

### Post by Cannaregio on 2008-04-29
This worked for me:

Check if you yourself (and other users) are part of the pulse groups. If not, add yourself to all pulse groups.
```
System --> Admin --> Users and groups
```
Restart or reboot.
Make sure to turn your volume on and up after reboot.

Good luck.

---

### Post by jatoskep on 2008-04-29
> **Cannaregio said:**
> This worked for me:

Check if you yourself (and other users) are part of the pulse groups. If not, add yourself to all pulse groups.
```
System --> Admin --> Users and groups
```
Restart or reboot.
Make sure to turn your volume on and up after reboot.

Good luck.
I checked, I'm part of the pulse group. D:

---

### Post by cyberdork33 on 2008-04-29
there are some other parameters you can try setting:
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Sound](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Sound)

---

### Post by sands on 2008-04-30
> **jatoskep said:**
> My sound does not work at all in Ubuntu 8.04.

It is a C2D Black Macbook. I tried the fix shown in the Macbook Santa Rosa guide, but it did not work:

To resolve, add the following to /etc/modprobe.d/options:

```
options snd_hda_intel model=mbp3 
```Any suggestions?


Try this.. That is what I did..

[http://ubuntuforums.org/showthread.php?p=4807645#post4807645](http://ubuntuforums.org/showthread.php?p=4807645#post4807645)

---

### Post by mabovo on 2008-04-30
> **jatoskep said:**
> My sound does not work at all in Ubuntu 8.04.

It is a C2D Black Macbook. I tried the fix shown in the Macbook Santa Rosa guide, but it did not work:

To resolve, add the following to /etc/modprobe.d/options:

```
options snd_hda_intel model=mbp3 
```

Any suggestions?

Try this for MacBook 2nd gen:
options snd-hda-intel model=[intel-mac-v5] position_fix=1 probe_mask=1

If you want surround try this on /etc/pulse/default.pa
load-module module-alsa-sink device=pulseaudio rate=48000 channels=6 sink_name=alsa_surround mmap=0 fragments=6
set-default-sink alsa_surround

---

