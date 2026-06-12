---
title: "Sudo modprobe snd-hda-intel?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-16
I am having alot of problems compiling a driver for my sound to work...SO I did modprobe and I got this error

harry@harry-desktop:~/alsa-driver-1.0.4$ sudo modprobe snd-hda-intel
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
harry@harry-desktop:~/alsa-driver-1.0.4$

I just reinstalled Dapper..BTW

thanks to anybody that can help

---

### Post by ovimunt on 2006-07-16
Didi you actually ***make*** and ***make install*** the package? :-k It looks like the ***kernel*** can't find some of the components.

---

