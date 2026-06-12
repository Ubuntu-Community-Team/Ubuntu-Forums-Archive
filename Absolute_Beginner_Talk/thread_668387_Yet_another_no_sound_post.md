---
title: "Yet another no sound post"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by jonathanpiper on 2008-01-15
I'm sure some people are getting tired of these, but I still haven't been able to solve my issue.

aplay -l gives
aplay: device_list:204: no soundcards found...

lspci -v gives
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: fast devsel, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

alsamixer gives
alsamixer: function snd_ctl_open failed for default: No such device

I put snd-hda-intel in my /etc/modules, and my /etc/modprobe.d/alsa-base contains the options snd-hda-intel line.

I've recompiled my alsa driver, I've used the alsa-source package and done module-assistant, I've purged the alsa packages and reinstalled them.  I've even tried this on 3 fresh installations of Gutsy.  I've used Edgy and Feisty, and sound worked fine in both of those.  Now with Gutsy, nothing.  What more can I do?  Any suggestions are GREATLY appreciated!

---

### Post by balaknair on 2008-01-15
Whenever I've come up against the no sound cards found result, the only thing that's worked 100% for me is to remake the entire Linux Kernel(either complete Reinstall of Ubuntu, or roll back the kernel to the Generic kernel) It could have something to do with some incompatability with ALSA snd-hda-intel modules in modified kernels.

Though you could try entering this in a terminal
sudo modprobe snd-hda-intel

and checking for sound again.

---

### Post by balaknair on 2008-01-15
I hope it doesn't come to that, but if you do have to do a reinstall, just try *aplay -l* before changing anything else on the system.
If it detects your card now move straight on to the modprobe.d/alsa-base step and add the options line with your model and then reboot.

---

### Post by Therion on 2008-01-15
See if this [Sound Problems Thread/Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide") helps.  It covers just about everything.

---

### Post by mali2297 on 2008-01-15
Have you searched Launchpad for bugs?

A quick search gave me this [reported bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/75818"), can it be related to your problem? (Perhaps you can find some others.)

---

### Post by jonathanpiper on 2008-01-15
> **balaknair said:**
> Whenever I've come up against the no sound cards found result, the only thing that's worked 100% for me is to remake the entire Linux Kernel(either complete Reinstall of Ubuntu, or roll back the kernel to the Generic kernel) It could have something to do with some incompatability with ALSA snd-hda-intel modules in modified kernels.

Though you could try entering this in a terminal
sudo modprobe snd-hda-intel

and checking for sound again.

How do I remake the kernel?  I've already tried reinstalling Ubuntu 3 times, all with the same result.

---

### Post by jonathanpiper on 2008-01-15
> **Therion said:**
> See if this [Sound Problems Thread/Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide") helps.  It covers just about everything.

I followed that guide to the letter, and nothing worked.

---

### Post by jonathanpiper on 2008-01-15
> **mali2297 said:**
> Have you searched Launchpad for bugs?

A quick search gave me this [reported bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/75818"), can it be related to your problem? (Perhaps you can find some others.)

I haven't checked that yet, but I'll take a look.

---

