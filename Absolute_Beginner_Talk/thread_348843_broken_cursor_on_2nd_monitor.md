---
title: "broken cursor on 2nd monitor"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by eooon on 2007-01-29
Hello.

I just installed ubuntu and used Aticonfig to set up my dualscreen system the way i want it. I ran into one problem however. When i move the cursor over to the 2nd screen, it stops being an "arrow" and turns into a square that is about 2cm X 2cm. 

It should be noted that i got diffrent resolutions on the monitors, one is crt and the other lcd. And, the cursor worked just fine when the 2nd monitor was just a mirror of the first. The problem happend after i used Aticonfig to setup the monitors to be "seperate desktops".

It still works, i can click things but it looks ugly as hell and it really isnt practical to have a cursor that is 2cm X 2cm :)

Anyone know how to fix this? I tried googling and searching in these forums, but I really dont know what im looking for...

thanks, 
eooon

---

### Post by eooon on 2007-01-29
Things i have tried:
( [http://ubuntuforums.org/archive/index.php/t-245143.html](http://ubuntuforums.org/archive/index.php/t-245143.html) )
Adding the following to xorg.conf:
Section "Extensions"
   Option "Composite" "Disable"
EndSection 

Restarting X.

---

### Post by eooon on 2007-01-29
Also tried adding the following under the "screen" section in xorg.conf.

 Option     "HWCursor"     "false"
 Option     "SWCursor"     "true"

---

