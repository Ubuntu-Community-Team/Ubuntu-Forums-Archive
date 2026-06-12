---
title: "Realtek HD Audio broken"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by quanumphaze on 2007-11-03
Hello
I'm using an Acer Aspire 3680 with a Realtek High Definition Audio card that doesn't work.

Firstly unmuteing the surround in the volume control lets sound through the internal speakers but not the headphone jack.

I tried to compile the ALSA drivers from source as per instructions from [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") but that made things worse. Now nothing works and when I open the volume control I get "No volume control GStreamer plugins and/or devices found"

Here's the output from lspci for it:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

---

### Post by quanumphaze on 2007-11-04
Can anybody help me to uninstall ALSA so I can try again?
Or it could just be a problem with the mixer contols, but I don't know how to fix it.
I can't live without my music :guitar:

---

### Post by jonasbh on 2007-11-05
I have the same problem. I have a zepto 3215w

---

### Post by quanumphaze on 2007-11-05
I miraculously got it working .... sorta.
I don't know why but I have sound but coming from both my external speakers and the internal ones.
I folowed the instructions at the [alsa-project]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel") and added "options snd-hda-intel model=auto" to the end of "/etc/modprobe.d/alsa-base".

@jonasbh:
I went through 3 different ways to compile alsa from source before it worked.
Try these solutions:
[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
[HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
[Gutsy Intel HD Audio Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")
Keep trying and best of luck. Don't forget to reboot like I did.

---

