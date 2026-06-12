---
title: "Sound must be set manually at startup"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Napjar on 2006-11-14
Hello,

I just managed to install the ALSA driver for my soundcard (SoundBlaster AWE32) and it worked !
Unfortunately when i shut down the PC and restart it later the sound must be activated manually by doing "modprobe snd-card-sbawe" ...
How can i let this start automaically at boot time ?

---

### Post by po0f on 2006-11-14
Napjar,

Follow [this](http://ubuntuforums.org/archive/index.php/t-6963.html) to get an rc.local script setup and just add `modprobe snd-card-sbawe` inside it.  The kernel *should* load the driver for it automatcially, but I guess it's not in your case.

---

### Post by grim918 on 2006-11-14
The above will or should work. Another quick fix way is to add the command as a startup program under System->Preferences->Sessions then just click the Startup Programs Tab and click Add.

This will only give sound for the current user and will need to be added to every other user in the sytem. This is only convenient if there is only one user on the system.

---

### Post by Napjar on 2006-11-15
OK thanks a lot, this seem to work !
I added the modprobe commands in the rc.local script and restarted ... sound came on !
Thx

---

