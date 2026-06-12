---
title: "I can't boot to desktop anymore"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by discofro on 2005-12-07
Everything was working fine pretty recently.

My computer has an AGP slot, and an integrated video card. I took out the AGP card I had in when I first installed and ran ubuntu (no problems with the agp card and ubuntu). However, I just removed the AGP card and have switched to the integrated card. Now when I try to boot linux, it says X server failed, disabling GDM, restart GDM when you have fixed the problem.

What can I do? I tried booting to recovery mode but that also ended in just a command prompt. The integrated card works fine when I boot into windows. Really don't know what to do here.

---

### Post by burnhamd on 2005-12-07
The problem is in your xorg.conf file.  The driver is set to the card that you had before.  X cannot start because you are running the wrong driver.  To fix this you must edit the conf file under the devices entry and type in the name of the driver you need to use.  As I am unaware of the driver you need I cannt help you with this.

---

### Post by aysiu on 2005-12-07
When you're at the command prompt, go ahead and log in (not graphically, of course).

Then, type this command in ```
sudo dpkg-reconfigure xserver-xorg
```

---

