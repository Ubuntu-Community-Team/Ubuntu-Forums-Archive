---
title: "re-install selectively?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by adza on 2007-04-28
Hi there, i was wondering... i've totally screwed up my xorg/NVIDIA install... nothing i've done seems to be able to fix... so, is there a way that i can re-install xserver and graphics only from live cd? Or do i have to re-install the whole lot and wipe my HDD?

---

### Post by zvacet on 2007-04-28
Did you try 

```
 sudo dpkg-reconfigure xserver-xorg
```

and maybe instead of **nvidia** select **nv**

---

### Post by freebird54 on 2007-04-28
And follow this for more info as you do it... (if you want)

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

It should keep you from getting lost in there :)

---

