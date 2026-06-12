---
title: "Really need help - absolute beginner..."
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by ains on 2007-11-06
Ok so here's what happened.
I was trying to setup my new wacom graphics tablet following the instructions found here:
[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

After adding the serverlayout options I rebooted my computer.
Once it loaded it now comes up with loads of errors and basically wouldn't load my normal environment.
It's basically running a terminal but I cannot open anything.
I tried to edit the xorg.conf using sudo gedit but it tells me that it cannot be displayed.

Is there anything I can do to undo the damage I've done? 
I'm such a tool^^

Thankyou so much in advance
Ains
xx

---

### Post by rudeboyskunk on 2007-11-06
You can only use gedit when you have the gnome gui loaded.  Try using "sudo nano xorg.conf" instead.

---

### Post by ains on 2007-11-06
thankyou very much it seems to be working :)
learn something new every day  eh :D
tytytytyt
xxx

---

### Post by bodhi.zazen on 2007-11-06
If that fails, restore from back up

If you did not back up, type :

> I will back up system files before I edit themin the terminal.

Then try this :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

