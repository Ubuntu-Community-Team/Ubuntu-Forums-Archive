---
title: "[SOLVED] Beryl On Intel Gma 900"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by vsugadhan on 2007-07-15
Just before installing beryl, i would like to know if there are any known issues with the intel gma 900 chipset..? 

Thanks in advance....

---

### Post by wolfen69 on 2007-07-15
best to just install and try it. post back if any problems.

---

### Post by vsugadhan on 2007-07-16
Below is my screenshot using beryl.... There panel below doesnt seem to be working...and i cant see the headers of any of the windows.... 
Anyone know what to correct????

---

### Post by walkerk on 2007-07-16
```
sudo apt-get install beryl-manager
```

then run it with alt+f2:
```
beryl-manager
```


you can reload window manager and window decorater from the systray..

if you want to theme beryl then install emerald:
```
sudo apt-get install emerald emerald-themes libemeraldengine0
```

---

### Post by vsugadhan on 2007-07-16
> **walkerk said:**
> ```
sudo apt-get install beryl-manager
```

then run it with alt+f2:
```
beryl-manager
```


you can reload window manager and window decorater from the systray..

if you want to theme beryl then install emerald:
```
sudo apt-get install emerald emerald-themes libemeraldengine0
```

Thanks.. That worked... Now have another dilemma... I can't seem to view videos in my computer...It just displays a blank screen.. Have seen many others post the same problem in this forum, but couldn't find a solution as such...

---

### Post by walkerk on 2007-07-18
> **vsugadhan said:**
> Thanks.. That worked... Now have another dilemma... I can't seem to view videos in my computer...It just displays a blank screen.. Have seen many others post the same problem in this forum, but couldn't find a solution as such...
hello again.. go into your video programs preferences and change it's video output to 'x11'

---

### Post by vsugadhan on 2007-07-21
Thanks... Solved

---

