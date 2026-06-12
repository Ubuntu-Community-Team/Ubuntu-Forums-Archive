---
title: "LG Studioworks 552v resolution"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by Cool Surfer on 2005-09-04
Hi ubunto's

I am having a screen resolution of 600 x 400 and cant change it.

Tried many times but couldnt do it.

my monitor is **LG Studioworks 552v resolution** , and it supports 800x600 resolution. Can someone make the changes for me pl, i can open the concerned file and do the changes.

If needed I will reinstall ubunto also.  ](*,) 
Thanks

---

### Post by adwait on 2005-09-04
Have you tried System>Preferences>Resolution? If the option for the resolution isn't there, maybe you can reconfigure xserver. For that, press shift+Alt+Ctrl+F1 then,
```

sudo killall gdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

---

### Post by Cool Surfer on 2005-09-04
[QUOTE=adwait]Have you tried System>Preferences>Resolution? If the option for the resolution isn't there, maybe you can reconfigure xserver. For that, press shift+Alt+Ctrl+F1 then,
```

sudo killall gdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```[/QUOTE]
 yes I did , but it asks for a lot of parameters, I dunno which one to choose.
Horizontal and vertical screen ... etc...
I tried making 800 x600 resolution but it does not work.

Any help pl.

---

### Post by ubuntme on 2005-09-05
maybe you could find the modes you monitor can support (manual)

i.e. res + depth + refresh rate

most likely you need to turn down the bit depth.

---

### Post by Cool Surfer on 2005-09-05
No manual came with my monitor. :( Got is just like that.

---

### Post by ubuntme on 2005-09-06
Did you try looking on the net?

---

### Post by ubuntme on 2005-09-06
Anyway,

Often you will get higher res in linux than windows.. whats in your xorg.conf file?

cat /etc/X11/xorg.conf

---

