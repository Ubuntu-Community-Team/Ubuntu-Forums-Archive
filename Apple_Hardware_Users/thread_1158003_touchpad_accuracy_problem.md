---
title: "touchpad accuracy problem"
date: 2009-05-13
forum: Apple Hardware Users
---

### Post by tiam87 on 2009-05-13
hi, i'm usign macbook 3,1 with jaunty 9.04.

i'm having problem with the touchpad configuration.
 i've copied xorg.conf from my previous intrepid installation and paste it in my new xorg.conf(i'm not using the /etc/hal/fdi/policy/preferences.fdi).
now everything  works normally (right click,scroll...).

The only difference beetwen the two version is that now i'm having  a bad feeling with the mouse pointer. in other words  when i try to click for example into a button or in window, i 'm not able to click with the  first click. i need to redo other time in order to be more accurate.
i try to change the setting of my xorg.conf but nothing change. i think its a problem of accuracy. 
if i try to move more slowly the mouse from the up to down side of screen, i can see that it's not moving in a straight line.
i attached my xorg.conf.
does someone else found this problem and a way to solve?

p.s: it's not hardware problem because using os x or intrepid mouse works very well.


Thanks
Mattia

---

### Post by gotgenes on 2009-05-13
> **tiam87 said:**
> i've copied xorg.conf from my previous intrepid installation and paste it in my new xorg.conf(i'm not using the /etc/hal/fdi/policy/preferences.fdi).
now everything  works normally (right click,scroll...).

You will need to migrate your settings over to a HAL FDI policy. Ubuntu switched over to Xorg 1.5, which means your input device settings in Xorg will now be ignored, and will instead be taken from a policy file. Looks like somebody already provided an example policy for you: [https://help.ubuntu.com/community/MacBook3-1/Jaunty#Touchpad%20(appletouch](https://help.ubuntu.com/community/MacBook3-1/Jaunty#Touchpad%20(appletouch))

---

### Post by tiam87 on 2009-05-14
ok.now works well :p. 
thanks!
how i can post this thread as "solved"?

---

