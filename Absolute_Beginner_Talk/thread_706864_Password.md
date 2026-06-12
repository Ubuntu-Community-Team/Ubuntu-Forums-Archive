---
title: "Password"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by eleli on 2008-02-24
I've just been locked out of my computer. I forgot my password. What's the easiest way to get it back? Keep in mind I'm a linux   noob.

Thanks

---

### Post by JoshuaRL on 2008-02-24
Boot into Recovery Mode by choosing that from the Grub Menu at bootup.  If you're not dual-booting, just hit ESC and it will bring up the Grub Menu.

After it loads fully and drops you into a GUI-less system as root, try:
```

passwd <username>

```
and you can reset the password.

---

### Post by bazzawill on 2008-02-24
reboot the machine and boot into recovery mode from the grub menu (you may need to pres esc to show the grub menu) this will boot into a root shell so be very carefull type
```
passwd [your username]
``` 
then type in a new password twice
and then
```
reboot
``` to reboot the machine into normal mode

---

### Post by spiderbatdad on 2008-02-24
;)

---

