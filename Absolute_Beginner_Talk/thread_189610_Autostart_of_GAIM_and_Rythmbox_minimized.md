---
title: "Autostart of GAIM and Rythmbox minimized"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Lomz on 2006-06-05
I have now managed to set autostart for GAIM and Rythmbox on my Ubuntu 6.06:
But I want those programs to start minimized.
How do I do that?

---

### Post by GarethMB on 2006-06-05
Add 

```
-run --minimised
``` to the startup command.

---

### Post by frodon on 2006-06-05
Or learn how to use devilspie, it's so powerful !!
[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

---

### Post by Lomz on 2006-06-05
[QUOTE=GarethMB]Add 

```
-run --minimised
``` to the startup command.[/QUOTE]

So how should the line in the "startupmanager" look like?
Now it looks like this: ```
rhythmbox -run --minimised 
```
But there was no difference in how the program started

---

### Post by GarethMB on 2006-06-05
[QUOTE=Lomz]So how should the line in the "startupmanager" look like?
Now it looks like this: ```
rhythmbox -run --minimised 
```
But there was no difference in how the program started[/QUOTE]
It should work, it works for me. It won't work for gaim though.:-k

---

