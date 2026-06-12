---
title: "in xserver-xorg im propted with identifier intell 915"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-19
i have intell 3dagp intagrated video card it uses intel 845gv chipset intagrated controller what should i enter as the identifier? is there a way to to all this automaticly

---

### Post by overdrank on 2007-06-19
> **swoll1980 said:**
> i have intell 3dagp intagrated video card it uses intel 845gv chipset intagrated controller what should i enter as the identifier? is there a way to to all this automaticly

Ok I guess you are configuring your xorg so after you choose intel  then you dont need to enter any other identifier. After you restart then you can check your xorg with the command 
gksudo gedit /etc/X11/xorg.conf  and see which driver is being used. 
Hope this helps some good luck!

---

