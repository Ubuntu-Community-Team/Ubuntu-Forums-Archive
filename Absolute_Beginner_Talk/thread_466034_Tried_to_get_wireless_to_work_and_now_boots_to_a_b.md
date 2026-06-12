---
title: "Tried to get wireless to work and now boots to a black screen"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by soler on 2007-06-06
Hey all,

 I successfully installed 7.04 on an IBM T22 laptop with all the updates but in trying to get my Belkin F5D7010 wireless card working, I've managed to bugger up the system and now it only boots to a black screen. I can get into recovery mode though.

 I was typing in ndiswrapper and modprobe commands when the system froze. I rebooted and now get a black screen after seeing the Ubuntu logo and progress bar. I have tried running the xserver-xorg to redo the configuration but that didn't help.

Any suggestions would be appreciated... TIA.

---

### Post by tdrusk on 2007-06-06
> **soler said:**
> Hey all,

 I successfully installed 7.04 on an IBM T22 laptop with all the updates but in trying to get my Belkin F5D7010 wireless card working, I've managed to bugger up the system and now it only boots to a black screen. I can get into recovery mode though.

 I was typing in ndiswrapper and modprobe commands when the system froze. I rebooted and now get a black screen after seeing the Ubuntu logo and progress bar. I have tried running the xserver-xorg to redo the configuration but that didn't help.

Any suggestions would be appreciated... TIA.
If worst comes to worst you could reinstall ubuntu-desktop. 
```
sudo aptitude reinstall ubuntu-desktop
```

---

