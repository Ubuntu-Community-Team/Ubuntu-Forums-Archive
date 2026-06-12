---
title: "KDE panel questions"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Alex6969 on 2006-07-28
I just installed ubuntu on my laptop, witch is dual booted with XP. When I first loaded it it had the Gnome session installed, i love the wireless signal, and battery lvl indicator on the top panel, but i like the looks of KDE better. Is there a way to enable this with KDE? Thanks for you replys guys, this is my 2nd day of running linux (actually I've used it before in my CCNA class but not ubuntu), and I'm learning alot.

---

### Post by richardward101 on 2006-07-28
try kbatt and kwifi, they run as applets in the system tray rather than being panel objects.

---

### Post by Alex6969 on 2006-07-28
when i went to add the applet kbatt and kwifi were not on the list. where can the be added from?

---

### Post by richardward101 on 2006-07-28
They are not panel applets like in gnome, they are normal programs, look in the main menu (forget exactly where) or just run kwifi or kbatt from a console to check they're there. If you can't find them in the menu try:
```
sudo apt-get install kwifi kbatt
```

---

### Post by Alex6969 on 2006-07-28
when i ran it in the console it said that it couldn't find the package

---

### Post by davebgimp on 2006-07-28
You probably need to add repositories to your sources.list.

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Then try again.

---

### Post by richardward101 on 2006-07-29
My appologies, it would appear i'm an idiot.
the package is kwifimanager, so
```
sudo apt-get install kwifimanager
```
will install it, then either run kwifimanager from the console or it should be in the start menu. You should be able to add it to the session so it runs by default.

However, there is also a proper panel applet that'd probably be better to use...```
sudo apt-get install kwavecontrol
```then just add it to your panel.

As for battery...

---

