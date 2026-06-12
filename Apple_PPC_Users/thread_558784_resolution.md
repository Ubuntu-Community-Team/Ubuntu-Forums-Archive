---
title: "resolution"
date: 2007-09-24
forum: Apple PPC Users
---

### Post by mkr55 on 2007-09-24
Hi hope someone can help. I am trying to install xubnutu on an ibook G3 laptop. It boots of the cd ok but the maximum resolution i can select is 640x480. This means i cant see the whole of the screen/ dialog boxes and so cant select the options to install.

The ibook displays much higher resolution when booting into OS X. How do i go about installing xubuntu?

---

### Post by anemptygun on 2007-09-24
Which version where you trying to install?

---

### Post by mkr55 on 2007-09-25
its dapper drake (6.06.1)

---

### Post by anemptygun on 2007-09-25
Have you tried the alternate installation cd..

---

### Post by stream303 on 2008-02-14
> **mkr55 said:**
> Hi hope someone can help. I am trying to install xubnutu on an ibook G3 laptop. It boots of the cd ok but the maximum resolution i can select is 640x480. This means i cant see the whole of the screen/ dialog boxes and so cant select the options to install.

Try using **xrandr** from a terminal.

For example, on my G5 iMac, using xrandr in Feisty shows this:
```
 SZ:    Pixels          Physical       Refresh
*0   1680 x 1050   ( 569mm x 356mm )  *60  
 1   1400 x 1050   ( 569mm x 356mm )   60  
 2   1280 x 1024   ( 569mm x 356mm )   60  
 3   1440 x 900    ( 569mm x 356mm )   60  
 4   1280 x 960    ( 569mm x 356mm )   60  
 5   1280 x 800    ( 569mm x 356mm )   60  
 6   1280 x 768    ( 569mm x 356mm )   60  
 7   1152 x 768    ( 569mm x 356mm )   55  
 8   1024 x 768    ( 569mm x 356mm )   60  
 9    800 x 600    ( 569mm x 356mm )   60   56  
 10   640 x 480    ( 569mm x 356mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
```


If you just type xrandr it should show a list of the resolutions your monitor is capable of.  When you see your native resolution, for example 1400x1050 , you can try

```
xrandr -s 1400x1050
```

Hopefully the display will change, and you'll even be able to get to the resolution menu option in gnome to see if you can make it permanent.

---

