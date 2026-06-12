---
title: "Metacity removed from startup programs"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-10
I followed [this]("http://ubuntuforums.org/showpost.php?p=1741561&postcount=3") link's advice and it suggested removing metacity from startup
 programs and now i'm stuck with only a terminal since my beryl isn't running
 right. I need to figure out how to add metacity back into my sessions from 
the terminal to be able to run ubuntu graphically again! Please help!

---

### Post by bruenig on 2006-11-10
I use xubuntu so I can't tell you for sure it would work. You should be able to do 
```
startx
``` and then run ```
metacity
``` after it starts or something else. Once you do get it running, modify the sessions graphically.

However...

The stuff that autostarts is, at least in xubuntu, in ~/.config/autostart. Judging from the format of the files in there I would say doing the following may work.
```
cd ~/.config/autostart
nano metacity.desktop
```

put this in the file
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=metacity
Comment=
Exec=metacity
StartupNotify=false
Terminal=false
Hidden=false
```
Note in this, all that probably matters is the Exec and the stuff underneath it.

---

### Post by shanepardue on 2006-11-10
Awesome! I didn't think I'd be able to get in by "startx". I should've known
better! I appreciate your help!

---

### Post by olieviya on 2006-11-23
> **bruenig said:**
> I use xubuntu so I can't tell you for sure it would work. You should be able to do 
```
startx
``` and then run ```
metacity
``` after it starts or something else. Once you do get it running, modify the sessions graphically.

However...

The stuff that autostarts is, at least in xubuntu, in ~/.config/autostart. Judging from the format of the files in there I would say doing the following may work.
```
cd ~/.config/autostart
nano metacity.desktop
```

put this in the file
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=metacity
Comment=
Exec=metacity
StartupNotify=false
Terminal=false
Hidden=false
```
Note in this, all that probably matters is the Exec and the stuff underneath it.


Is that the general way of adding programs to the start up? :-k

---

