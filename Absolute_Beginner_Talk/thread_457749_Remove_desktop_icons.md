---
title: "Remove desktop icons"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-05-29
I installed 1386 U-FF dual boot and the icons for the Windows and 2 Dell utility partitions show on the desktop.  How can I remove them from view?

---

### Post by Ek0nomik on 2007-05-29
Open a terminal and type:

```
gconf-editor
```

Apps --> Nautilus --> Desktop

---

### Post by bettyhills on 2007-05-29
I installed i386 U-FF and cannot find Nautilus anywhere under apps.  When I go to ADD-Remove, Nautilus is not one of the choices.  Can you direct me?

---

### Post by zodmaner on 2007-05-29
You have to open up the terminal, it is located at

Applications >> Accessories >> Terminal

Then, type in the code Ek0nomik gave you:

> gconf-editor

into the terminal.

If you have done everything correctly, a new window will pop up. 
On the left side, choose: Apps --> Nautilus --> Desktop and you should see the setting for desktop icons.

PS: Thanks Ek0nomik! I was also looking for a way to turn off those mounted icons! :)

---

### Post by bettyhills on 2007-05-29
Got it.  Thank you all.

---

