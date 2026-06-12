---
title: "I broke it...."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Cyann0923 on 2007-05-28
Finally killed Kubuntu.

I have been having issues with my current graphics card (ATI Radeon x1600 pro 512 ddr2) which appears to be one of the least compatible video cards out there.  So I switched to my older lower end card (Aopen Aeolus nVidia geofrce 6600GT 128mb) because I figured it was better supported.

I booted her up and everything was a little blurry and at a lower rez then usual.  So I went into my System and set everything the way it should be.  I rebooted and it was in that awful resolution that the PS3 comes in by default when you don't have the right TV (still haven't fixed that either) So I figured it was time to edit xorg.

I set everything the way it should be and rebooted.  Now the graphical interface won't load.  It tells me that there are no screens that are usable available.  Fatal error, and then nothing stuck in command prompt. 

Anybody have a way to fix this?

---

### Post by taurus on 2007-05-28
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by justifier on 2007-05-28
in text based more try running 

xorg -configure 

(it might need sudo)

---

