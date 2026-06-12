---
title: "How do you change the boot screen in Ubuntu?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by jclmusic on 2006-07-06
i can't find it in the system menu.

---

### Post by kencoe on 2006-07-06
[QUOTE=jclmusic]i can't find it in the system menu.[/QUOTE]
If you are talking about putting in a splash screen, then try going to System>Preferences>Splash Screen.

---

### Post by Dr. Nick on 2006-07-06
To changet the grub screen

[http://ubuntuforums.org/showthread.php?t=89916&highlight=grub+splash+screen](http://ubuntuforums.org/showthread.php?t=89916&highlight=grub+splash+screen)

---

### Post by jclmusic on 2006-07-06
[QUOTE=kencoe]If you are talking about putting in a splash screen, then try going to System>Preferences>Splash Screen.[/QUOTE]

this is what i was talking about. in every other version of linux i've used that uses gnome, it's been there, but not ubuntu 6.06.

:???: :-?

---

### Post by crossedout on 2006-07-07
If you are trying to change the login screen (GDM):
Open System --> Administration --> Login Window

If you are trying to change the login splash screen, you'll need to open terminal and type:

```
sudo apt-get install gnome-splashscreen-manager
```

Open: System --> Preferences --> Splash Screen
Choose the Splash Screen you want to use and click activate.
You can download splash screens at gnome-look.org

-crossedout

---

### Post by jclmusic on 2006-07-07
aha! marvellous, thank you!

---

### Post by MR.UNOWEN on 2008-01-12
How do I change the screen that comes before login and after grub? It's the one that's black with the orange bar loading across the screen?

---

### Post by jargoman on 2008-02-06
The link that Dr nick posted shows how to change the boot splash that comes after grub loads.

---

