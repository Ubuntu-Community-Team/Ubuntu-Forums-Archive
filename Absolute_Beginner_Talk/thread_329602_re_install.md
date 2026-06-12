---
title: "re install"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by CriticalStealth on 2007-01-01
is there a way to reboot the linux (like clear and start over) or should i just use the boot cd, and re install it? because mine if f'd up... and nothing seems to be helping....   is re-installing the best way to go?

---

### Post by Tenicus on 2007-01-01
It depends.
What exactly "F-ed up"?

---

### Post by CriticalStealth on 2007-01-01
[http://www.ubuntuforums.org/showthread.php?t=328883]("http://www.ubuntuforums.org/showthread.php?t=328883")

read through there.. theres no hope.. i will stratv from fresh, i havent done anyhting on here anyway, and +_ im just gettignthe feel for ubuntu, untill i gte my new/old computer working to make it my linux machine.. (i have this as a virtual drive using vmware) then ill actually get into it...

---

### Post by WiseElben on 2007-01-01
Reinstalling should be your last resort. What are your problems? Maybe we can help.

You might want to try to reconfig your xorg.conf file by doing:
```
sudo dpkg-reconfigure xserver-xorg
```
in a terminal. Again, this depends on what you messed up.

EDIT: Oh.. it looks like you used Automatix 2. I wouldn't use that if I were you. Many say it is unsafe and causes a lot of breakage. If you want to install codec's (to play mp3s and so on), use the guide [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs"). Good luck.

---

### Post by CriticalStealth on 2007-01-01
ok, well i will re install, then take your advice on not using this gay program! thanks

---

