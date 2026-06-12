---
title: "Disabling sound devices"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-11-13
I have two sound cards on my computer, one is on-board and the other is an internal one.

The on-board one no longer works and I have disabled it in the BIOS but it still shows up in Ubuntu and it occasionally gets chosen as the default sound device.

Is there any way I can prevent it from being ever used?

---

### Post by linjofitnes on 2007-11-13
I had same problem and have managed to fix it this way:-

Open up terminal and enter - cat /proc/asound/modules

this will give you a list of your soundcards/onboard etc.

now enter - sudo nano /etc/modprobe.d/alsa-base

at the end of the file add  the following

options snd-[your preferred sound card] index=0
options snd-[your secondary sound card] index=1

I found all this at the following

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

hope this helps

---

### Post by so7777777os on 2007-11-13
> **linjofitnes said:**
> I had same problem and have managed to fix it this way:-

Open up terminal and enter - cat /proc/asound/modules

this will give you a list of your soundcards/onboard etc.

now enter - sudo nano /etc/modprobe.d/alsa-base

at the end of the file add  the following

options snd-[your preferred sound card] index=0
options snd-[your secondary sound card] index=1

I found all this at the following

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

hope this helps
Hope can make it.....Don't blame me gab&#65288;I'm noob)...How to do if soundcard on-board still show it on Ubuntu?

---

