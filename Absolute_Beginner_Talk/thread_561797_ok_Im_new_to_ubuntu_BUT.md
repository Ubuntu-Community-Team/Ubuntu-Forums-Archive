---
title: "ok Im new to ubuntu BUT"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by jaysons on 2007-09-28
I want the eye candy, can anybody PLEASE help me set up my os to do this  [http://www.youtube.com/watch?v=lawkc3jH3ws&mode=related&search=](http://www.youtube.com/watch?v=lawkc3jH3ws&mode=related&search=)

I want the 3D box and weird wabble windows soo bad ***!!!

---

### Post by dpar on 2007-09-28
Here is some reading for you......[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by ramjet_1953 on 2007-09-28
To be able to help you, we need specific information about your system.

We mainly need to know what video card and model that you have, or the video chipset that is on your motherboard, as you may need to install the driver for that chipset to enable all of the 3D effects.

Regards,
Roger 8)

---

### Post by kakalaky on 2007-09-28
post the output of
```
lspci | grep VGA
```

---

### Post by jaysons on 2007-09-28
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

I have beryl up and running, I have windows fire thing and they wabble  but I cant figure out how to get the cube

---

### Post by kakalaky on 2007-09-28
Beryl is no longer developed.  You would probably be better of using compiz-fusion.  There is a backports from gutsy repo and a git repo.  I would recommend the backports repo unless you are ready for things to break every now and then.

Instructions for backports repo here: [http://forum.compiz-fusion.org/showthread.php?t=3153]("http://forum.compiz-fusion.org/showthread.php?t=3153")

Instructions for git repo here:  [http://forum.compiz-fusion.org/showthread.php?t=1012]("http://forum.compiz-fusion.org/showthread.php?t=1012")

---

### Post by lyceum on 2007-09-28
> **jaysons said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

I have beryl up and running, I have windows fire thing and they wabble  but I cant figure out how to get the cube

Ctrl+tab+arrows. If you have Beryl, install the manager as well. You can then cusomize. It will take a bit of playing with everything to get it the way to want it. Have fun :)

---

