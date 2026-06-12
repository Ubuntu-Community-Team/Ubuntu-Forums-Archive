---
title: "Ubuntu 10.10: iMac 27&quot; i7: Internal Speakers issue."
date: 2010-12-06
forum: Apple Hardware Users
---

### Post by jisaac on 2010-12-06
Does someone manage to make the Internal Speakers work?

Thanks.

---

### Post by jisaac on 2010-12-07
Here is the workaround:

1. sudo apt-get install linux-backports-modules-alsa-maverick-generic gnome-alsamixer
2. Reboot
3. Check output is on "Internal Audio Analog Stereo" on Sound Preferences.
4. Open gnome-alsamixer and increase "front sp" and "headphone" volume.

Thanks to markbirss, the original post was for 10.04 and it works too for 10.10:
[http://ubuntuforums.org/showthread.php?t=1457304](http://ubuntuforums.org/showthread.php?t=1457304)

---

### Post by tiogaphoto on 2011-01-21
That fixed it on a iMac 27" core 2 duo E7600.

---

