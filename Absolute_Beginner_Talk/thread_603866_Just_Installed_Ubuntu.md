---
title: "Just Installed Ubuntu"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by HuddleHoop on 2007-11-05
Hi Guys,
Just partitioned my HD and installed ubuntu for the first time and i have no sound although my creative sound card works well with my Vista and my graphics card isn't brilliant either, is there a setting I can check to correct these problems

Thanks in advance.

---

### Post by mlentink on 2007-11-05
Try System>Preferences>Restricted Drivers

---

### Post by HuddleHoop on 2007-11-05
Hi,
There is only my Ati graphic driver and i installed that

---

### Post by Maestro23 on 2007-11-05
> **HuddleHoop said:**
> Hi,
There is only my Ati graphic driver and i installed that

What model is your soundcard? Are you running 32/64-bit Ubuntu?

---

### Post by jabeez on 2007-11-05
Did you reboot after installing ATI driver through restricted drivers manager? As for the soundcard, try opening a terminal and typing in "alsamixer" and go through all the sliders, depending on your card there is probably a slider/switch in there that needs to be turned on/up.

---

### Post by Pumalite on 2007-11-05
Post:

sudo lshw -C sound

---

### Post by HuddleHoop on 2007-11-05
Sorry didn't mean to have to threads:confused:

[http://ubuntuforums.org/showthread.php?t=603872](http://ubuntuforums.org/showthread.php?t=603872)

---

