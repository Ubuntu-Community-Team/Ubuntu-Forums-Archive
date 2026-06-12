---
title: "[SOLVED] Skype is speechless"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Robert Ashley on 2007-07-02
I am new to Linux, and have a Gateway 838GM computer with Ubuntu 7.04 installed (dual boot with Win-XP). The audio system is on the mother board.
The Linux System Information - Hardware, says it is;
82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller,
with 3 ALC880 Analog ALSA selections, 3 ALC880 Analog OSS selections, and 1 Intel ALSA Control Device.
I have installed the Linux version of Skype.
Skype boots up OK and I hear the test voice just fine, but I cannot get the microphone audio to transmit.
Under System -> Preferences -> Sound, I have tried all of the possible microphone selections. None of them allow transmitted sound.
(Skype with Win XP works OK).
Has anyone found this same problem, and a fix for it?

---

### Post by yagood on 2007-07-02
I had the same problem. Try this - open Volume Control - right-click on a speaker icon in tray and select Open Volume Control or launch "gnome-volume-control" from the terminal. In Options tab try switching Input Source to Mic or Front Mic.

---

### Post by Robert Ashley on 2007-07-03
Many thanks for your suggestions. I tried them all.
Unfortunately, I still don't have microphone sound.
Maybe I need to install a sound card.

---

### Post by pjbgravely on 2007-07-05
Right click on volume, click open volume control. Make sure mic is not red at the bottom and the slider is all the way up. If that doesn't help click edit/preferences and check the mic boost box, then go to the mic boost tab and check the box.

Paul

---

### Post by yagood on 2007-07-06
You could also try switching from ALSA to OSS in Skype Options > Sound Devices.

---

