---
title: "Change menu.1st"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Bill de Garis on 2007-05-08
Hi,
I have found menu.1st and changed it so that my system will boot W2K by default instead of Ubuntu.
But Ubuntu (7.04)  will not let me save the file.
This is most annoying!
Apparently I have to log in as root or superuser to do this but how?
TIA

Bill

---

### Post by NeoLithium on 2007-05-08
gksu gedit /boot/grub/menu.lst

It will give you the superuser permissions you need :)

---

### Post by Cypher on 2007-05-08
Try
```

gksudo gedit /boot/grub/menu.list

```

---

### Post by Kobalt on 2007-05-08
Press Alt+F2 then enter *gksu gedit /boot/grub/menu.lst* 
It will ask you for your admin password, give it, and you'll be able to edit & save the file.

---

### Post by Bill de Garis on 2007-05-08
Good Grief! Replies seemingly the instant I posted.
Thanks Much!

---

### Post by rsambuca on 2007-05-08
> **Cypher said:**
> Try
```

gksudo gedit /boot/grub/menu[COLOR="Red"].list[/COLOR]

```
That should actually be [COLOR="Red"]lst[/COLOR]

---

### Post by Cypher on 2007-05-08
Thanks for the correction..I always seem to make that mistake..

---

