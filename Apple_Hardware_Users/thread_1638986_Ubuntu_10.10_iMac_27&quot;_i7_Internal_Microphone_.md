---
title: "Ubuntu 10.10: iMac 27&quot; i7: Internal Microphone issue."
date: 2010-12-06
forum: Apple Hardware Users
---

### Post by jisaac on 2010-12-06
Does someone manage to make the Internal Microphone work?

Thanks.

---

### Post by jisaac on 2010-12-06
Ok, there is workarround:

1) Install "PulseAudio Device Chooser" and boost your Internal Microphone as explained here: [http://ubuntuforums.org/showthread.php?t=1439009](http://ubuntuforums.org/showthread.php?t=1439009)
2) Then add this line "options snd-hda-intel model=mbp55" to "/etc/modprobe.d/alsa-base.conf".
3) Restart.

You should now have your Internal Microphone working, with Skype as well.

I don't mark this thread as "Solved" because I've noticed another problem: The recorded sounds are left speaker only!?

You can see it clearly with the PulseAudio Volume Meter.

Does anyone experience something similar?

---

### Post by artik1024 on 2010-12-12
jisaac so many thanks ! I followed you about the ATI bug, that result of a blank screen. Also, I had the microphone issue, with your trick it's solved !! many thanks for it. Hope ATI bug will be solved too, but it seems it's not really on the good way....

---

### Post by jisaac on 2010-12-14
You're welcome!

PS: Just to clarify one point, the ATI issues related to vsync and color depth is really progressing. The situation is now far better than before. See: [http://ubuntuforums.org/showthread.php?t=1638418](http://ubuntuforums.org/showthread.php?t=1638418) but at install time we still get the famous blank screen...

---

