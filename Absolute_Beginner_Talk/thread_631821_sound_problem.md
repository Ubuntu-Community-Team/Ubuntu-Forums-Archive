---
title: "sound problem"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by bsharp on 2007-12-04
I have been following this guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and both of my soundcards are recognized, one of them is a PCI Sound Blaster Live! 24-bit and the other an integrated nVidia HDA chipset.  According to the alsa-project page, both are supported and I have made sure that the modules with the drivers are loaded both by modprobe and also by adding them to /etc/modules.  I know that the cards and speakers are good because they work fine in Windows XP.  I have gone into alsamixer and made sure that nothing is muted, still no sound.  The only lead that I have is when I try and do a sound test in the Sound Preferences I get this error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

I have searched the forums and have no idea what the problem could be :confused:

---

### Post by bsharp on 2007-12-04
Never mind, I have gotten it to work with OSS. (If anyone knows how to do this with ALSA, please post)

---

