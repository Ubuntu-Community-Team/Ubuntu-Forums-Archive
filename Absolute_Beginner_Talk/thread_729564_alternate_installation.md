---
title: "alternate installation?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-20
Does the alternate installation have all the great features of the graphical installation including the nice animated windows?

---

### Post by mikewhatever on 2008-03-20
No, none of them. See some screenshots [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
After you are done installing and boot from the HDD, enable graphics drivers and turn the effects on, it's that same, as if installed from a live CD.

---

### Post by mahela007 on 2008-03-20
but after I install ubuntu will be just the same right?

---

### Post by Jimmyfj on 2008-03-20
The alternate install Cd is simply an install without the fancy GUI but when you first have your system up and running after install the result is the same. Personally I find the alternate install Cd a better way of installing any system than the fancy GUI on the Live Cd.

---

### Post by uberlube on 2008-03-20
> **Jimmyfj said:**
> The alternate install Cd is simply an install without the fancy GUI but when you first have your system up and running after install the result is the same. Personally I find the alternate install Cd a better way of installing any system than the fancy GUI on the Live Cd.

+1

---

### Post by PmDematagoda on 2008-03-20
> **mahela007 said:**
> but after I install ubuntu will be just the same right?

The installed applications will be the same, but you may have to configure your X-Server to get a working GUI.

You can boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
and restart Ubuntu with:-
```
reboot
```

---

