---
title: "Install for many computer"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by luckymancvp on 2008-03-15
I have a low computer (celeron 1.8 ; ram 256).I want to install ubuntu so I install it on other power computer(with my hard disk).
When I bring hard disk to home and try but it doesn't appear graphic mode.Please help me
(In power computer my partition is sda,  in my computer it is hdd).

---

### Post by Gyzome on 2008-03-15
Sorry mate, but that doesn't work that way. Ubuntu configures hardware during the installation. So if you suddenly change it's whole hardware environment, it gets confused and can't reconfigure itself. Try placing some extra or more powerful RAM chips in your old computer and install it locally. Switching between computers only works when they have a similar hardware environment. Changing the CPU may be risky, so DO **NOT** DO IT.

Good luck.

---

### Post by ugm6hr on 2008-03-15
Maybe try this:
[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

```
sudo dpkg-reconfigure xserver-xorg
```

This is a more complete explanantion: [http://ubuntuforums.org/showpost.php?p=3956118&postcount=6](http://ubuntuforums.org/showpost.php?p=3956118&postcount=6)

---

