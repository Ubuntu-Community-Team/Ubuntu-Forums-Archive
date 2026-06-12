---
title: "Desktop to terminal"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-03-20
My ubuntu setup currently starts up in desktop mode; how can I set it to start up in terminal mode?

---

### Post by Brunellus on 2006-03-20
if all you want is a textomode console, just hit CTRL+ALT+F1 and you'll get one.

---

### Post by My-dial-up on 2006-03-20
Thanks for that, but I'm after switching over to terminal as my future start up default - is it something like init ??

---

### Post by stuporglue on 2006-03-20
This is probalby the wrong way to do this, but you could probably just:

$ sudo chmod -x /etc/init.d/gdm

That will remove execute privs on the gdm launcher. Someone here probalby knows the right way to do it though.

---

### Post by mlind on 2006-03-20
System > Administration > Services 

disable gdm

---

### Post by My-dial-up on 2006-03-20
Thanks.

---

