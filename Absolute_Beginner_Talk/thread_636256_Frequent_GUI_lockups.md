---
title: "Frequent GUI lockups"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by syzygy64 on 2007-12-09
I installed Ubuntu 7.10 on my PC today and everything is working fine except the GUI freezes randomly, sometimes after a few hours of use and sometimes after only a few minutes. It doesn't seem to stop any other running processes (if an MP3 is playing, it continues playing after the lockup), and I can move the cursor, but I can't click on anything and it doesn't respond to keyboard input. My video card is an ATI Radeon 8500 LE. As far as I can tell, it's using the right driver, but I'm fairly new to Linux so I'm not 100% sure everything is configured correctly.

How should I go about solving this problem? Thanks in advance for your help.

---

### Post by nikoPSK on 2007-12-09
try:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

or if that doesn't like you:

```
sudo dpkg-reconfigure -plow xserver-xorg
```

---

### Post by nikoPSK on 2007-12-09
EDIT: sorry, I posted on the wrong thread....

---

