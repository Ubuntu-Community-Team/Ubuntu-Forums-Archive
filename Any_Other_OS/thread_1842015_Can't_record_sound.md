---
title: "Can't record sound"
date: 2011-09-10
forum: Any Other OS
---

### Post by crazyfuturamanoob on 2011-09-10
I'm using Linux Mint, which is basically a low-fat Ubuntu.
Sound output works (finally!), but I can't record anything. I want to record what is coming out of speakers.

I have tried arecord, audacity and gtk-recordMyDesktop. They all record total silence. The only available input device is hw:0,0 or "default".
I have everything enabled and set to 100% in gnome-alsamixer. What should I do? :confused:

```

user@desktop:~/Desktop$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
user@desktop:~/Desktop$ 

```

EDIT:
I don't actually know which sound system I am using and why I have installed alsa, oss, esd, asound and jack. Wtf?
After reading a lot stuff about Linux audio, I think I should have OSS and nothing else.

---

### Post by Perfect Storm on 2011-09-10
Moved to Other OS/Distro Talk.

---

### Post by crazyfuturamanoob on 2011-09-10
Now I have installed OSS4, and sound is working great. But recording still doesn't work.
Edit: Now I managed to record static noise coming out of nowhere.

---

