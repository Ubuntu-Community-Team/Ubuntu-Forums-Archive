---
title: "Usb Headset (Automatic Detection?)"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Baufo on 2007-09-16
I have a USB headset. I got it working hacking /etc/modprobe.d/alsa-base and setting snd_usb_audio to 0 and snd_intel8x0 to -2. Then I reboot and the headset works. If I want to work without my headset I have to modify the file and reboot once again. Needless to say that this is not very convenient. I wonder if I somehow could get Ubuntu to automatically use the loudspeakers if the headset is not plugged in but use it if it is.

Thank you in advance,
Baufo

---

### Post by questpro on 2007-09-16
Try to solve by using this thread

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


It helped me to solve mine:)


EDIT: In the above thread, the section **"Configuring default soundcards / stopping multiple soundcards from switching" ** helps you.
make the usb card as default by making its index 0 as explained in that section.

---

### Post by Baufo on 2007-09-16
Thank you!

---

