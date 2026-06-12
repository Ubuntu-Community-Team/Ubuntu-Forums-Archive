---
title: "xorg failing to detect display resolution"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by niyi on 2007-07-30
I just installed Feisty Fawn (I had Edgy before) on my AMD64 and for some reason my nvidia drivers and Xorg are unable to detect that my monitors resolution is 1240x1024 and is setting it to 1024x768.

This never used to be a problem with Edgy. Anyone got any ideas on how i can counter this problem?

---

### Post by Rocket2DMn on 2007-07-30
A classic problem - you need to reconfigure xorg
```
sudo dpkg-reconfigure xserver-xorg
```
At the resolutions page, select your monitor's max resolution and everything less (TAB to move and SPACEBAR to select)
Then restart the X-server with CTRL+ALT+BACKSPACE.
Then you can select the higher resolutions

---

