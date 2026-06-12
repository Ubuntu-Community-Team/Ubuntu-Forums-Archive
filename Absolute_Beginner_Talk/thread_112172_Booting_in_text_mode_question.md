---
title: "Booting in text mode question"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by listerine on 2006-01-03
Hello,
I just got an old server to play with and I installed Kubuntu 5.10 on it. Its a PIII 450Mhz with 128 megs of RAM, I'm not sure about the video card. I have the box configured how I like it, as a webserver. 

Wat I would like to do is to get it to boot in text mode so I can save on resources and not start KDE when it starts up. But I would like to be able to start KDE when I need it.

BTW theses forums and Kubuntu are both awsome!

Thanks for your help.

---

### Post by LaSSarD on 2006-01-03
I'm not sure if that's the best way to do it, but I'm sure it works:
```
sudo update-rc.d kdm remove
```

---

### Post by listerine on 2006-01-03
[QUOTE=LaSSarD]I'm not sure if that's the best way to do it, but I'm sure it works:
```
sudo update-rc.d kdm remove
```[/QUOTE]


How would I start KDE when I'm in text mode?

---

### Post by listerine on 2006-01-03
I think I found a fix, I did your command but I'm not sure if I hade to. By choosing "console" in mode when you log in it dosent load KDE. And if you do log in on the GUI you can log off and go back to console mode and it will shutdown kdm and Xorg.

---

### Post by mithion on 2006-01-19
I might have another solution that's pretty simple.  If you install the package called "bum" which stands for boot up manager, you can edit which applications are launched when the computer boots.  I for example use gnome so I used bum and deselected gdm in the startup programs.  That way I can boot in much lighter text mode.  When I need to use the desktop, I just type "startx" and boom i'm back.  Hope this helps.

---

