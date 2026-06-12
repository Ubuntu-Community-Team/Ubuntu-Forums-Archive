---
title: "Broadcom 4311 WPA help, Gusty Gibbon"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-11-14
I'm using Gusty, with a Broadcom 4311 wifi card, and I used the restricted drivers to get it working. Everything works, except for WPA. Can someone help me get it working? I've got no idea what's wrong.

I have the following in /etc/default/wpasupplicant
```
ENABLED=0
```

Still doesn't work. Every other Mac and PC in my school can connect to it, so I'm sure it's an ubuntu problem.

Thanks in advance.

---

### Post by rorestuff on 2007-11-14
Have you tried using nm-applet:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

i think you can install it with:

sudo aptitude install network-manager-gnome

---

