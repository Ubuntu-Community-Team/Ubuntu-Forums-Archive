---
title: "Change the clock in Enlightenment"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-02
Is there a way to change the clock in Enlightenment from analog to digital.

---

### Post by LuisAugusto on 2007-06-03
Yes, open your e17 menu, select modules, disable the clock module, and enable Tclock module, then add it to your shelve.

---

### Post by jonward0690 on 2007-06-03
How would I get it off of 24hour time and change it to 12hour time.

---

### Post by Co.Sinecure on 2007-06-03
Right-click on the clock, and go to 'Configuration'.
Then google 'strftime(3)'. I don't know the syntax off the top of my head!

---

### Post by jonward0690 on 2007-06-03
> **Co.Sinecure said:**
> Right-click on the clock, and go to 'Configuration'.
Then google 'strftime(3)'. I don't know the syntax off the top of my head!

I fixed it it was set to %M or something and I set it to %X and that set it write.

---

### Post by Co.Sinecure on 2007-06-04
I actually found that the tclock is barely legible in alot of the themes, I'm using the blue-eyed theme at the moment and it works with the themed shelf background.

Does anyone know of a large, configurable digital clock to use instead? I have seen them in other people's e17 screenshots...

---

### Post by worldwithoutgurus on 2007-06-05
Is that big enough ? :p
[http://perso.orange.fr/pinguSODalon/screens/xdaliclock.png](http://perso.orange.fr/pinguSODalon/screens/xdaliclock.png)

(I used this command:  xdaliclock  -24 -fullscreen -transparent -fg grey)

Xdaliclock is a configurable digital clock you may like.
See man xdaliclock and have fun !

---

### Post by LuisAugusto on 2007-06-10
> **Co.Sinecure said:**
> I actually found that the tclock is barely legible in alot of the themes, I'm using the blue-eyed theme at the moment and it works with the themed shelf background.

Does anyone know of a large, configurable digital clock to use instead? I have seen them in other people's e17 screenshots...

In the theme e17 manager, select advanced, then select the module/clock and use the one from any theme you got install, you can make it big, just use put it in it's own shelve. BTW: You really should test the detour theme: [http://code.google.com/p/detour/](http://code.google.com/p/detour/)

---

