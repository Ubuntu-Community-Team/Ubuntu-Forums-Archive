---
title: "macbook 5,1 ubuntu 11.10 backlight macros dont work"
date: 2011-11-17
forum: Apple Hardware Users
---

### Post by kpholmes on 2011-11-17
upgraded from 11.04, mactel installed, was working in 11.04 but now in 11.10 its not working. anyone having this problem aswell?

---

### Post by kpholmes on 2011-11-17
fixed it, info on this page


 [https://help.ubuntu.com/community/MacBook5-1/Natty](https://help.ubuntu.com/community/MacBook5-1/Natty)

Adjusting the screen brightness works out of the box with the default "nv" graphics driver. ¿?

Using restricted NVIDIA graphics driver(Current Version) need to edit /etc/X11/xorg.conf and add to device section:

        Option  "RegistryDwords" "EnableBrightnessControl=1"

---

