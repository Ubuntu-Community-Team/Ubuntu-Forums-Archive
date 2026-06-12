---
title: "can't open root/etc/local.rc"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by danijela on 2008-01-05
i've created a script local.rc
[I]#! /bin/sh
echo Hello world[/I]

and save it with :
[I]cp -a ~/etc/rc.local ~/etc/rc.local.backup
[/I]
i turn off my virtual machine (vmware)
and start it again and run local.rc script
and this is msg i've got *can't open root/etc/local.rc*

---

### Post by danijela on 2008-01-05
sorry rc.local :)

---

### Post by Tux.Ice on 2008-01-05
so is this solved??

---

### Post by danijela on 2008-01-05
no..:(

---

### Post by Tux.Ice on 2008-01-05
oh ok i wuz confused.you did use sudo didnt you?

---

### Post by danijela on 2008-01-05
just for root
sudo -i

---

### Post by danijela on 2008-01-05
when i type  $ $EDITOR ~/etc/rc.local
it says no such file or directory..and i dont know why :(

---

