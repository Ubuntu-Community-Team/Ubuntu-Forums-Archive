---
title: "can't access /boot/grub/menu.lst"
date: 2006-08-27
forum: Art &amp; Design
---

### Post by dema on 2006-08-27
I can't edit /boot/grub/menu.lst because i'm not a admin-user.

How can I login as admin to edit this file? I'm using grub.

---

### Post by amo-ej1 on 2006-08-27
you can use sudo to raise your privileges e.g.
sudo vi /boot/grub/menu.lst
(but this does depend on you /etc/sudoers configuration) or you could use su if you have a root password set. But this only works if this is your own box and you have configured it as such.  The entire privilege system was invented to keep people from doing things they shouldn't be doing ;-)

---

### Post by dema on 2006-08-27
Can't I edit it from Gnome?

---

### Post by dema on 2006-08-27
Can I only edit a write-protected file from the terminal?

---

### Post by Klaidas on 2006-08-27
You can only edit it as root. See [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

> sudo gedit /boot/grub/menu.lst
In other news, this is not related to art :)
Please take some time to find an appropriate subforum before posting.

---

