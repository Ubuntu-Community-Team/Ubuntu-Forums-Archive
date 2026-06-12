---
title: "how to change start menu icon size?"
date: 2007-03-10
forum: Art &amp; Design
---

### Post by factor on 2007-03-10
Hi, i want to change start menu icon size, i want big icons for a dark theme i'm using, before i was using HighContrast Inverse them and the icon size was correct for me, i would like something like that but i haven't seen any way of changing icon size of application menu, nautilus left bar, places, system menu, etc.

I suppose i should have to change a config file and modify some parameters, could someone be so kind as to point me what should i do?

thanks in advance for your help.

Regards.

---

### Post by siciliancasanova on 2007-03-12
I saw [this]("http://ubuntuforums.org/showthread.php?t=222546&highlight=usp") and saw something about changing icon size in it.

---

### Post by factor on 2007-03-13
thabks, but it seems to be unsupported since august 2006 :-/

---

### Post by kpolice on 2007-03-13
Create a file called .gtkrc-2.0 in your HOME and paste:

```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-menu=16,16:gtk-large-toolbar=24,24:gtk-button=16,16"
```

panel-menu is the one you are looking for, you can remove the rest or change it to whatever size you want.

---

### Post by factor on 2007-03-14
i tried that too, didn't work either, even after rebooting. I'm using feisty AMD 64 with latest updates (gnome 2.18.0). And what seems weird, is that there is a .gtkrc-1.2-gnome2 file in my home too that is recreated if i delete it. It's autowritten by gnome-settings-daemon and i'm told not to edit it.

These are the values i'm using:
```

gtk-icon-sizes = "panel-menu=48,48:panel=48,48:gtk-menu=48,48:gtk-large-toolbar=48,48:gtk-button=48,48"

```

I tried with 32,32 too and it isn't affecting anything.

Any idea?

Regards.

---

### Post by kerry_s on 2007-03-14
-> [http://www.ubuntuforums.org/showthread.php?t=383148](http://www.ubuntuforums.org/showthread.php?t=383148)

---

### Post by kpolice on 2007-03-14
Maybe the theme you are using defines the size for the panel, you have to check it or try another theme.

---

