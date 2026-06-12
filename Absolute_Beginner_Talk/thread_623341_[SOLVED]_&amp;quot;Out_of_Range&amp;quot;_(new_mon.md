---
title: "[SOLVED] &amp;quot;Out of Range&amp;quot; (new monitor)"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by n3tfury on 2007-11-25
Hi folks,

Just got a new 22" monitor, reconfigured X using

```
sudo dpkg-reconfigure xserver-xorg
```

since my monitor wouldn't do the proper rez (1680x1050) when i first booted into ubuntu.  after reconfiguring X things seemed to work okay, but after a reboot i'm stuck with the "Out of Range" error on my monitor and i cannot get a prompt of any kind.  i know this has to do with the Hz being set too high, but can anyone steer me in the right direction to recover?

---

### Post by Majorix on 2007-11-25
Look on the internet for your monitor's horizontal and vertical refresh rates.
Start in recovery mode by selecting it at the bootup.
Do a dpkg-reconfigure xserver-xorg. No need for "sudo" at the beginning.
When prompted for monitor settings choose "advanced" and fill in the info you got.
Do a "reboot" and you will be in X.

Good luck.

---

### Post by n3tfury on 2007-11-25
thanks Majorix, that did the trick.  posting from ubuntu right now. :)

---

