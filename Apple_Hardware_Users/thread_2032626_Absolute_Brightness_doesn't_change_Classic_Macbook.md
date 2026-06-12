---
title: "Absolute Brightness doesn't change: Classic Macbook"
date: 2012-07-24
forum: Apple Hardware Users
---

### Post by Hedgehog9597 on 2012-07-24
Hello!  I'm not sure if this is in the right support category, but hopefully somebody here can help me out.

I am on a classic macbook, running ubuntu 12.04.  When I use the  brightness keys, the little window pops up in the upper-right hand  corner of the screen, and changes.  Also, the file  /sys/class/backlight/apple_backlight/brightness does change when I  attempt to change the brightness.  However, the file  /sys/class/backlight/apple_backlight/absolute_brightness stays constant  at 15.  How can I make it so that the file "absolute_brightness" changes as the file "brightness" does?

Thanks!

---

### Post by Lunarts on 2012-07-25
It does not change even on current apple hardware, you will have to do the following everytime at console:

```
 xrandr --output LVDS --brightness 0.8
```

change the last value for what hurts less your eyes.

The imac auto-brightness does not work also.

---

