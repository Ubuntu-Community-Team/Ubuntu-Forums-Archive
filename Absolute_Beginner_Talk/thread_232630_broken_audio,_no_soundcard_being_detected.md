---
title: "broken audio, no soundcard being detected"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-08-09
i had sound, but it broke when i tried to update the driver. now i have no sound and the soundcard is not even being detected.

```
aplay: device_list:221: no soundcards found...

```

this is how i broke the soundcard

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop
```

thanks for any help!

---

### Post by orb9220 on 2006-08-09
Comprehensive Sound Problem Solutions Guide

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

### Post by shanepardue on 2006-08-09
yeah..i was following that to get an updated driver and i broke it with the above command..i've followed the entire guide to no avail

---

### Post by shanepardue on 2006-08-09
i love ubuntu, but i think one place it's very weak is it's driver management. right now i have an integrated soundcard that it's not seeing because the driver was messed up, but there's no way to install a driver for the hardware. (that's how it seems)

---

