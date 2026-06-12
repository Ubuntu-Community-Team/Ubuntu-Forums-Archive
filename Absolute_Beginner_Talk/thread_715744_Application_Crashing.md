---
title: "Application Crashing"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-05
A couple of applications have crashed for me, since install. I don't know exactly what the problem is, but was wondering if there is:

a) A hot key to access a processes window?
b) A hot key to force quit?
c) A hot key to just do something! (stopping me from just simply resetting)

Is it strange that Ubuntu is not acting hugely stable?, although its fine most of the time..

---

### Post by kesman on 2008-03-05
you could make a hotkey to launch xkill, which turns your mouse pointer into a skull that you can kill any application with a single click. Be careful to click the application, not desktop or any panels though =D

---

### Post by TeoBigusGeekus on 2008-03-05
System->Administration->System Monitor
Tab Processes, find the crashed application, right click it and kill/end it.
You can also right click on your panel and
Add to panel->System Monitor

---

### Post by SOULRiDER on 2008-03-05
If everything seems to lock up you can try restarting X with 
```
 ctrl + alt + backspace
```
If that doesnt work you could try a reboot by pressing
```
alt + SysRq
``` and then quickily (while pressing those two) type
```
reisub
```

---

### Post by hungryOrb on 2008-03-05
Thanks <3

---

### Post by jan quark on 2008-03-05
if you know the process' name you can quit it with the command

```
killall process-name
```

to view all current processes running run the terminal command

```
top
```
or
```
ps -e
```

---

