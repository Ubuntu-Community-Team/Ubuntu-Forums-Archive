---
title: "root access"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2007-06-02
how do i get root access?

---

### Post by kernel tom on 2007-06-02
sudo -i
will make you root

sudo before a comand will run that command as root

---

### Post by lsalminen on 2007-06-02
Applications -> Accesories -> Terminal

type " sudo -i "
type your root password
press enter or return

there you go.

If you want to login as root:

logout
type "root" for username
then, type your root password.

---

### Post by jonward0690 on 2007-06-02
> **lsalminen said:**
> Applications -> Accesories -> Terminal

type " sudo -i "
type your root password
press enter or return

there you go.

If you want to login as root:

logout
type "root" for username
then, type your root password.

Yea but first he will need to set his root password by typing "sudo passwd"then he will need to go to system preferences then to the login window then to security and put a check next to allow system administrater to graphicaly login in.

---

### Post by dpzektor on 2007-06-02
Or, if you want root access in the GUI file manager:

sudo nautilus

And if running Xubuntu:

sudo thunar


This is great if you don't want to navigate as root via terminal. I use this method quite often actually.

---

### Post by Rita G. on 2007-06-02
thank you all very much.

---

