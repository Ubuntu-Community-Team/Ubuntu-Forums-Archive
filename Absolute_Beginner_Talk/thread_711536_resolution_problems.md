---
title: "resolution problems"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-02-29
when i start the PC and choose ubuntu as the OS my monitor blacks out,with the following message-"out of range horizontal 63.5kHz vertical 58.9 Hz".then in a few seconds the ubuntu appears asking me to allow it to run in low graphics safe mode,and takes "plug"and "play"  and a crummy resolution.i tried to reconfigure from the terminal but couldn't.plz help.

---

### Post by taurus on 2008-02-29
How did you try to reconfigure X server?  Did you run something like

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Otherwise, make sure the horizontal and vertical refreshing rates for your monitor are correct in /etc/X11/xorg.conf.

---

### Post by erginemr on 2008-02-29
You may refer to the followin HOWTO to check if your symptoms match the ones I have explained there:
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

