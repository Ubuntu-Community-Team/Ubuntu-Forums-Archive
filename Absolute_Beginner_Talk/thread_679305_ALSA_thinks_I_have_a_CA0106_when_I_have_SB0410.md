---
title: "ALSA thinks I have a CA0106 when I have SB0410"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by antisomnic on 2008-01-26
I was wondering why I had less options in alsa then other people with my card. ALSA lists me having a CA0106 which my understanding is an audigy, and it also lists nothig in chipset. I have a Sound Blaster Live! 24-bit PCI. How can I tell alsa I have a different card? I tried that reconfigure and it doesn't list my card in there. Is my card a subset of the audigy and should work the same?

---

### Post by click4851 on 2008-01-26
I am by no means a sound card pro, I was able to straighten my mess  using a combo of ALSA website and this post...

[http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is)

I hope that helps give you a place to start. Sound has been a sore point for a number of releases, I am looking forward to Pulseaudio and Ubuntu sound "just working" in the future.

---

### Post by antisomnic on 2008-01-27
Turns out CA0106 is right, and I got 4 speakers to work by unchecking a bunch of stuff in volume control.... I was thinking like windows where if you uncheck it, it just doesn't show up in the volume control but it still works, in this one it disables it. Now I have the problem of getting my 5th speaker to work and also get bass controls working for the subwoofer, but I think I can find info about that. Thanks for your help.

---

