---
title: "configure wacom tablet"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-26
is there a way to do this?  i've had it working for about a month now, but i still can't change the buttons on the pen to do exactly what i want, the mouse scroll wheel scrolls backwards, and the two buttons and scroll wheel on the tablet don't work.  any ideas?  i don't see anything obvious in xorg.conf that would fix it.

---

### Post by uchuunoyanushi on 2007-04-28
Have you done this? [https://help.ubuntu.com/community/Wacom?highlight=%28wacom%29](https://help.ubuntu.com/community/Wacom?highlight=%28wacom%29)

---

### Post by gamx on 2007-04-28
With respect to the inverted wheel mystery, the workaround proposed for Edgy at
[https://help.ubuntu.com/community/Wacom?highlight=%28wacom%29](https://help.ubuntu.com/community/Wacom?highlight=%28wacom%29)

does not work in Feisty. The following one, though, works with my Wacom Sapphire 3 so far:
xsetwacom set cursor RelWUp "button 5"
xsetwacom set cursor RelWDn "button 4"

Check it out here:
[http://www.nabble.com/Scroll-wheel-inverted-t3499551.html](http://www.nabble.com/Scroll-wheel-inverted-t3499551.html)

---

### Post by jharbert on 2007-04-28
A [howto ]("http://ubuntuforums.org/showthread.php?t=371510")on Tablet PC's with Ubuntu - not sure if it will address your specific problem but it might.

---

### Post by locke.dragon on 2007-04-30
```

xsetwacom set cursor RelWUp "button 5"
xsetwacom set cursor RelWDn "button 4"

```

this worked for me.  now i followed the instructions on the previous link to make it run at start and i'm all set!  thanks guys!  :D

---

### Post by locke.dragon on 2007-04-30
now does anyone know how to get the two buttons and scroll wheel working that are located at the top of the tablet?  changing what the buttons on the pen do would be nice too.  ;)

---

### Post by jharbert on 2007-04-30
If you're referring to a tablet PC use the howto posted above.  If a usb wacom, try [this]("http://ubuntuforums.org/showthread.php?t=298914").

---

