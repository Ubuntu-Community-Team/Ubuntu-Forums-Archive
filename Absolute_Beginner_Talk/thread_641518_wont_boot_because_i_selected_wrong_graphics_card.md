---
title: "wont boot because i selected wrong graphics card"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by yuffie8 on 2007-12-15
hey, im an absolute beginner and have only been using ubuntu a little while. I have 7.10 and as i was able to run beryl fairly well i was mistified when i upgraded to 7.10 (i did a fresh install) i cant run any of the desktop effects - which really isnt a big deal and not essential. anyways i was messing about in the select graphics card settings bit and it had ATI-xxxxx (something) at the top of the box. But it had a generic Graphics card selected, so i selected the ATI card and rebooted but now ubuntu wont load.

At the load screen the bar loads fully then the computer freezes and the monitor turns off. I tried to boot into recovery mode and after a few seconds it has

root@barfird-desktop:~# _

as you can imagine as a complete rookie this scares me a little .... if anyone could help that would be fantastic

---

### Post by overdrank on 2007-12-15
> **yuffie8 said:**
> hey, im an absolute beginner and have only been using ubuntu a little while. I have 7.10 and as i was able to run beryl fairly well i was mistified when i upgraded to 7.10 (i did a fresh install) i cant run any of the desktop effects - which really isnt a big deal and not essential. anyways i was messing about in the select graphics card settings bit and it had ATI-xxxxx (something) at the top of the box. But it had a generic Graphics card selected, so i selected the ATI card and rebooted but now ubuntu wont load.

At the load screen the bar loads fully then the computer freezes and the monitor turns off. I tried to boot into recovery mode and after a few seconds it has

root@barfird-desktop:~# _

as you can imagine as a complete rookie this scares me a little .... if anyone could help that would be fantastic

HI and when in recovery mode use this command ```
 dpkg-reconfigure -phigh xserver-xorg
``` and use the command  ```
startx
``` or to  reboot ```
 reboot
``` Hope this helps and good luck!

---

### Post by yuffie8 on 2007-12-15
hey, thanks for your quick reply, when i type in 

 dpkg-reconfigure -phigh xserver-xorg

i get : 
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20071215201533
root@barford-desktop:~#

if i then type startx or reboot the screen turns off after a few seconds :s ... do i need to type anything else in ?

---

### Post by yuffie8 on 2007-12-15
hey i know i should wait a while before bumping this thread but does anyone think there is not much chance of this working ?

its POSSIBLY for a fresh install ... i dont want to because i will lose some stuff but it isnt the end of the world.

---

### Post by cub682 on 2007-12-15
Try this code
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by yuffie8 on 2007-12-15
thanks guys, i typed in 

```
sudo dpkg-reconfigure xserver-xorg
```

and went through it .... odd though im sure i had typed that in numerous times ...anyway all is well now :) thanks

---

