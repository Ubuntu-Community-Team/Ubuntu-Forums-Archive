---
title: "Force quit??!?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by RealG187 on 2007-04-13
Automatic is using apt-get and it isn;t responding so I cant use apt-get! Can I force it to quit, like CTRL ALT DEL?

---

### Post by thegreenblob on 2007-04-13
If you right click on one of your panels and click "Add to panel" there is a force quit button you can add.

---

### Post by RealG187 on 2007-04-13
I cant find it I see Dock application bar, External task bar,etc I am in KDE...

---

### Post by thegreenblob on 2007-04-13
Oh, sorry. I assumed you were in gnome.

Try pressing ALT+F2 then typing in "xkill" your mouse will turn into a skull. Click the app you want to close to close it.

---

### Post by RealG187 on 2007-04-13
> **thegreenblob said:**
> Oh, sorry. I assumed you were in gnome.

Try pressing ALT+F2 then typing in "xkill" your mouse will turn into a skull. Click the app you want to close to close it.

Thanks, I logged out I couln't b4 cuz I was downloading [gonna try xubuntu!]....

But for the hell of it, is this safe to try, could I just open an app and try, I obviously wouln't do it to an app I am using, like my Banshee ripping a CD [its fast ripping, way faster than what comes w/ KDE, I looked at the percentage bar and it's high, and thats for the whole CD, while in xbuntu ripper it was at 1/6 that for the fisr track!]

---

### Post by oomingmak on 2007-04-14
1. How can I add the force quit applet to the menu bar in Gnome (I'd don't want it on the panel and would rather have it on the menu under Applications > System Tools).

2. And how can I assign my own keyboard shortcut to it?

Thanks

---

### Post by RealG187 on 2007-04-14
BTE this happened back in Gnome and not in KDE yet but the menu bar at the top and taskbar at the bootom froze and didn't work!

---

### Post by RealG187 on 2007-04-14
> **thegreenblob said:**
> Oh, sorry. I assumed you were in gnome.


not ur fault...

I should have said that, by default it is Gnome and not KDE, i have some signature updating to do!

---

### Post by octoberdan on 2007-04-14
There's always pidof and kill. ```
pidof <name of process>
``` will give you the process id which you can then pass to kill ```
 kill <pid> 
```
for example:
```

daniel@ubernix:~$ pidof apt-get
25273
daniel@ubernix:~$ sudo kill 25273

```

As a side note, **ps axu ** is also handy (Give it a try! It's safe). Especially when compound with piping and grep.

---

### Post by RealG187 on 2007-04-15
how do i use px axu? also how do i know wat number a process is?

---

