---
title: "xserver freezes iMac g3"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by Mariofreak64 on 2008-06-09
As root in the command prompt with no GUI, i use apt-get installl xorg xserver-xorg-dev  to install xorg. I then put in startx to start it and my screen goes black. control-alt-backspace won't get it back to the command prompt. Whats the deal.

---

### Post by stream303 on 2008-06-09
Depending on what version you are running, I think you just apt-get install xorg, or if very much older, x-window-system-core.

This might help - even though the title is about low-memory, it goes into detail about server installs with X layered on top:

[https://help.ubuntu.com/community/Installation/LowMemorySystems#head-84b061dd2d8081bbfb62af4003b5843dfbc5dc99](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-84b061dd2d8081bbfb62af4003b5843dfbc5dc99)

I've got a feeling the major problem is that your some of your setting in /etc/X11/xorg.conf are not right and need manual editing:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

---

