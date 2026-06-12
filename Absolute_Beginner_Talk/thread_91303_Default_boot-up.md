---
title: "Default boot-up"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by rad_dreamer2kx on 2005-11-16
sup guys, i have windows xp and ubuntu on my hard drive,ubuntu boots up by defualt with grub how can i change that so xp boots up by defualt,is there any option 
with ubuntu?suse 10 had some options,but i cannot find it ubuntu.thanks!!

---

### Post by Kapre on 2005-11-16
[QUOTE=rad_dreamer2kx]sup guys, i have windows xp and ubuntu on my hard drive,ubuntu boots up by defualt with grub how can i change that so xp boots up by defualt,is there any option 
with ubuntu?suse 10 had some options,but i cannot find it ubuntu.thanks!![/QUOTE]

raddreamer - this [THREAD]("http://www.ubuntuforums.org/showthread.php?t=88533&highlight=grub+order") is what you need to look at.

K

---

### Post by aysiu on 2005-11-16
I don't know how to do it graphically, but if you type this in a terminal ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` you should see your boot configuration. One part of the configuration says ```
default 0
``` This means the first item is the default. If Windows is the fourth item, change it to ```
default 3
```

---

