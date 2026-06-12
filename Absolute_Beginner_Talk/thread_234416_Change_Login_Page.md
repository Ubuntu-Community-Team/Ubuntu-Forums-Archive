---
title: "Change Login Page"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-08-11
I installed xubuntu desktop along with ubuntu and now at the login page I have the blue xubuntu screen.  How can I get the brown unbuntu login screen back?

---

### Post by JerMe on 2006-08-11
try:```
sudo gdmsetup
```

---

### Post by Hillbilly Tilley on 2006-08-11
Worked great!!   Changed the login page back to the brown ubuntu. Although there is still a blue screen before and after the login page.


Thanx for the help

---

### Post by JerMe on 2006-08-11
The blue screen before is the boot splash, and the blue after is the login splash.  You can google for different bootsplashes, and the login splash can be changed with gconf-editor by editing the apps > gnome-session > options > splash_image key.  I'm sure you can take it from here. ;)

---

### Post by patrick295767 on 2006-08-11
famous gdm site : [http://art.gnome.org/themes/gdm_greeter/](http://art.gnome.org/themes/gdm_greeter/)

---

