---
title: "[SOLVED] just wondering"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-10-22
i noticed that every time i re/start ubuntu, the num lock is off
is it supposed to do that?
(i know this is no major problem, but i just need to know) :)

---

### Post by Dr Small on 2007-10-22
Yes, or at least ways, it does on mine.

---

### Post by maxxym on 2007-10-22
Yeah mine does it too..

How do you enable it so it stays ON?

---

### Post by Arwen on 2007-10-22
And mine too and I think it's also off in my XP when booting..

---

### Post by Fanin on 2007-10-22
ok, thanks.. like i said, just wondering :)

---

### Post by Fanin on 2007-10-22
> **maxxym said:**
> Yeah mine does it too..

How do you enable it so it stays ON?

i was thinking about the same thing

---

### Post by evilregis on 2007-10-22
I've set my NumLock to be on in my computer's BIOS.  You might want to check there first.

---

### Post by Fanin on 2007-10-22
> **evilregis said:**
> I've set my NumLock to be on in my computer's BIOS.  You might want to check there first.

i did try that but it is on "on" already, is there any setting in the ubuntu system that could be changed, or do i just have to press NumLock every time i start ubuntu (not that it's a big problem!)

---

### Post by Fanin on 2007-10-22
i did try that but it is on "on" already, is there any setting in the ubuntu system that could be changed, or do i just have to press NumLock every time i start ubuntu (not that it's a big problem!)

---

### Post by evilregis on 2007-10-23
Not sure what to say... I don't remember specifically setting my numlock to stay on but it's on by default for me.  Perhaps you can try this:

[http://www.ubuntugeek.com/numlock-activate-at-startup-in-login-screen.html](http://www.ubuntugeek.com/numlock-activate-at-startup-in-login-screen.html)

---

### Post by Fanin on 2007-10-24
> **evilregis said:**
> Not sure what to say... I don't remember specifically setting my numlock to stay on but it's on by default for me.  Perhaps you can try this:

[http://www.ubuntugeek.com/numlock-activate-at-startup-in-login-screen.html](http://www.ubuntugeek.com/numlock-activate-at-startup-in-login-screen.html)

this did not work for me, or i am doing it wrong, because when i type the "sudo gedit /etc/X11/gdm/Init/Default" command i get the gedit text editor but it's empty!
oh, and i wanted to thank you for this site.. didn't know it existed :D

---

### Post by Fanin on 2007-11-11
:confused:

---

### Post by Fanin on 2007-11-26
> **Fanin said:**
> :confused:

just bumping again. :)
please help

---

### Post by CatKiller on 2007-11-26
Their path is wrong. And you should use **gksudo** for graphical apps like GEdit. So the command you want is ```
gksudo gedit /etc/gdm/Init/Default
```

---

### Post by Fanin on 2007-11-26
> **CatKiller said:**
> Their path is wrong. And you should use **gksudo** for graphical apps like GEdit. So the command you want is ```
gksudo gedit /etc/gdm/Init/Default
```

\\:D/
it worked.. you're a genius CatKiller :)

---

### Post by philinux on 2007-11-26
> **Fanin said:**
> this did not work for me, or i am doing it wrong, because when i type the "sudo gedit /etc/X11/gdm/Init/Default" command i get the gedit text editor but it's empty!
oh, and i wanted to thank you for this site.. didn't know it existed :D

Whenever you get the path wrong or file does not exist the system just opens an empty file for you.

---

### Post by Fanin on 2007-11-26
> **philinux said:**
> Whenever you get the path wrong or file does not exist the system just opens an empty file for you.

oooh.. I did not know that :)

---

