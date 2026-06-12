---
title: "[SOLVED] Does this look normall"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-25
this looks very fuzzy on the writing and it is very squashed my screen can support 1440 x 900 but i dinut think that this is because 1.it looks weird compared to windows 2. its fuzzy 3. in the system administration>screen resolution it says only 1280 x 1024 please help me get proper clear resolution

---

### Post by Blutack on 2007-07-25
The screenshot looks ok, what graphics card do you have?
Try this anyways
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Jimmyfj on 2007-07-25
It would help us a lot to know what graphics card you have installed, and if you have the restricted driver installed for that too.

---

### Post by llzero1337 on 2007-07-25
nvida geforce fx 5200 and i have the rstricted dervier enabled/installed

---

### Post by llzero1337 on 2007-07-25
hey i found out it was on 1280 x 1024 so how can i get it to 1440 x 900 and i tried that guide and got nothing blutack

---

### Post by Cappy on 2007-07-25
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.settingres
```
```
sudo nvidia-settings
``` 
on the "X Server Display Configuration" Tab, you'll see a dropdown labeled as "resolution". Change that and click "Save to X Configuration File". Alt+Control+Backspace at the same time OR reboot to change your resolution.

---

### Post by llzero1337 on 2007-07-25
wow finally super screen quality thank alot cappy

---

