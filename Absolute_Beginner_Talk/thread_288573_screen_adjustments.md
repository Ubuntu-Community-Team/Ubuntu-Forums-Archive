---
title: "screen adjustments"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by thor908 on 2006-10-30
how do i get ubuntu to fit my screen right?

---

### Post by land0 on 2006-10-30
It sounds like you may actually need to physically adjust the monitor. There should be some sort of buttons or button that you can use to do this with. After you have the screen just right you can easily shift between resolutions by going to System--> Preferences--> Screen Resolution. You may have to make some minor adjustments to the monitor after changing resolution.  

I hope this helps

---

### Post by Perfect Storm on 2006-10-30
Please post your xorg.conf,

```
cat /etc/X11/xorg.conf
```

and find your monitor manual (we need some numbers from there).


If you have nvidia card, make sure the 3D acc. binary driver is installed. This sometimes solve the problem.

---

