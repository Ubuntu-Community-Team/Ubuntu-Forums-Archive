---
title: "How do I change my Main Menu Icon?"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-17
Hi,

How do I change my Main Menu Icon?

Can this be done without a Icon theme?

Thanks

---

### Post by endersshadow on 2006-05-17
```
locate main-menu.png
```

Replace all instances with the image you would like.

Note that if you want to change the applications menu logo, you will need to locate distributor-logo.png and change that.

---

### Post by Nano Geek on 2006-05-17
Check this [thread]("http://www.ubuntuforums.org/showthread.php?t=156462").

---

### Post by aktiwers on 2006-05-18
Thanks! It worked!

I just 

```
sudo nautilus
```

then went to[FONT=monospace] 
```
[/FONT]/usr/share/icons/hicolor/48x48/apps/
``` 

Then made a copy of 
distributor-logo.png

Renamed my .png file and replaced it!

Incase someone else wanted to know :)

---

