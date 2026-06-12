---
title: "No Sound"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2007-02-05
I've got no sound from my built-in speakers or plug-in headphones and external speakers in my laptop.  This problem just started today and I don't remember changing anything.  I've already tried the solutions at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and I've still got nothing.  I'm not sure what you would need to know but my aplay -l output in the terminal is:
> **** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

If you need any other information or anything just let me know.
Thanks,
Nolan

---

### Post by carlosfocker on 2007-02-08
Is PCM at a reasonable level.  You can check it thru alsamixer

---

