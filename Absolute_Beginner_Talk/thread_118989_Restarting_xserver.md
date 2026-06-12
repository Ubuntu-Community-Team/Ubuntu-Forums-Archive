---
title: "Restarting xserver?"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by Deaf_Head on 2006-01-18
What I want to do is set my crt as the primary monitor and turn off the laptop monitor. I have the ati drivers installed (thanks to [http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+driver)) so i'm using teh ATI control panel ... 

Whenever I try to change my display setup it tells me I need to restart x-server for changes to take effect. Rebooting the comptuer doesn't do the trick .. so does anybody have any suggestions?

---

### Post by 23meg on 2006-01-18
Rebooting includes restarting the X server, so it should help; I'm not sure why it doesn't but hitting Ctrl + Alt + Backspace restarts X and you can use it to make X-related changes take effect without rebooting.

---

### Post by mvandeg on 2006-01-29
Yes, there seems to be a problem with the settings from the ATI control panel. They are not saved somehow, so restarting X doesn't have any effect. If someone has a solution I would be really grateful, because dual monitor setups become a real problem this way.

---

