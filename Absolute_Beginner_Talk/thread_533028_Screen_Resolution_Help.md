---
title: "Screen Resolution Help"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Rylin on 2007-08-23
I recently installed Ubuntu 7.4 (64-bit version) and I installed the latest nvidia drivers. I'm on a Samsung SyncMaster 225BW 22in' widescreen lcd monitor and the highest resolution available in the settings is 1024x768.

Ive looked through various other threads and had no success. I'm in the process of reinstalling Ubuntu due to messing with the xorg conf file too much. Hopefully someone can shed some light on increasing my resolution to its native size of 1680x1050.

Much appreciated

-Rylin

---

### Post by wolfen69 on 2007-08-23
in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Rylin on 2007-08-23
Thanks for the quick reply wolfen.

Will try this as soon as ubuntu is finished installing and see if that fixed the problem. :)

---

### Post by Rylin on 2007-08-23
Ok I remember going through this screen last time and had to reinstall ubuntu because of it. Given I have included what monitor I use, can anyone walk me through the steps to setup my screen to support my 1680x1050 resolution?

---

### Post by alienexplorers on 2007-08-23
Is your Nvidia card able to reach 1680x1050?  Have you tried using nvidia-settings run in sudo mode to alter the screen size?

---

### Post by Rylin on 2007-08-23
I went to applications > accessories > terminal and typed:

sudo nvidia-settings

it tells me

"sudo: nvidia-settings: command not found"

---

### Post by por100pre1 on 2007-08-23
Check this [thread]("http://ubuntuforums.org/showthread.php?t=83973"). Hope this helps. :)

---

### Post by Rylin on 2007-08-23
Problem solved! :) 

Had to make sure both screen and monitor settings were the same as far as depth and frequencies. 

Appreciate the help guys,

-Rylin

---

