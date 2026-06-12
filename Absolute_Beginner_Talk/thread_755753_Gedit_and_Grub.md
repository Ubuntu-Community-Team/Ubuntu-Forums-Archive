---
title: "Gedit and Grub"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by SpiceWeasel on 2008-04-15
I multi booted my laptop with Ubuntu and XP and being that I'm always doing something else while i wait for my laptop to boot the 10 seconds pass on grub and it boots into Ubuntu when i want to boot into windows. Anyways my problem is when i went to terminal and tried 

```
sudo gedit boot/grub/menu.lst
``` 

I get a blank page and I've tried nearly every possible variation of that commands spelling and syntax just in case i typed it wrong and i still get nothing but blank pages. But knowing me i probably overlooked some minor detail. I just cant seem to think of what it would be though. ](*,)

---

### Post by wblancqu on 2008-04-15
Should be
```
sudo gedit /boot/grub/menu.lst
```

Grtz

---

### Post by quinnten83 on 2008-04-15
everyting in the linux file systems starts "/".
"/" Is the center of the linux universe.
"/" where the sun sets, and the moon rises.
never forget you are nothing without "/" and "/" is nothing without you....

Now bow down and show "/" some resepct!!!

---

### Post by SpiceWeasel on 2008-04-15
Figured it was something minor, my insomnia is getting the better of me these days with my 10 hours of sleep a week. :cry:

---

### Post by quinnten83 on 2008-04-15
sokay Dude, 
don't worry about it, took me like 3 months b4 I could wrap my head around the concept. And then I kept making syntax errors too...

---

