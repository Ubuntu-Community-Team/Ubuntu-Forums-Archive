---
title: "Gnome panel on top?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Klejs on 2006-03-12
Hi all,

I have played alot with the gnomepanel and finally i have found the most satisfying look. But now then I maximize an window (any) it is on top of the 2 panels (with other words it covers the whole screen) and thats pretty annoying.

I have looked a bit in the gconf but I cant find any values for the panels to always stay on top...:-k :-k

---

### Post by Klejs on 2006-03-12
: Bump :  Anyone please?

---

### Post by BoyOfDestiny on 2006-03-12
Strange... does this happen with every app?

How about nautilus...

I can understand if it's tvtime full screen.

P.S. I don't think you should bump messages unless it's been a day...

---

### Post by jr.gotti on 2006-03-12
Have you done any playing around with xcompmgr or any other composite extensions? These things tend to make the panel go postal.

Try typing into a terminal

```
killall gnome-panel
```

See if that helps...

---

### Post by patrick295767 on 2006-03-12
[QUOTE=Klejs]Hi all,

I have played alot with the gnomepanel and finally i have found the most satisfying look. But now then I maximize an window (any) it is on top of the 2 panels (with other words it covers the whole screen) and thats pretty annoying.

I have looked a bit in the gconf but I cant find any values for the panels to always stay on top...:-k :-k[/QUOTE]
  
Which desktop are u using ? If you are using fvwm, u can customize this very easily ... 
(I guess it' s gnome ... )

---

### Post by Klejs on 2006-03-12
Yes it is gnome but the **killall gnome-panel** solved the problem, and
sorry for the :bump:...I've used the xcompmgr for a while but now that I've
uninstalled it this was what happened....


Thanks for the help guys!

---

