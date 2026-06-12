---
title: "[SOLVED] Auto-Start command line in terminal"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Ohwii on 2007-11-15
Hi Guys,

Well I am using a Siemens amilo7400 and I always have to type in 

>sudo modprobe fsam7400 

in the terminal. ( I guess it loads to driver) 

is there a way it starts automaticly when i log on. 

well i am a newbe.

See ya later,

Ohwii

---

### Post by Billy_McBong on 2007-11-15
system>preferences>sessions
then add a new start-up program

---

### Post by spupy on 2007-11-15
There is a file "/etc/modules", which says which modules to be loaded at startup. Add fsam7400 to the end of this file (you have to be root to edit it). It will be then loaded automaticaly.

---

### Post by Ohwii on 2007-11-15
> **spupy said:**
> There is a file "/etc/modules", which says which modules to be loaded at startup. Add fsam7400 to the end of this file (you have to be root to edit it). It will be then loaded automaticaly.


THANK YOU,spupy,

very helpful. 

just the root thing was kind of tricky.

cheers 

OhWii

---

### Post by spupy on 2007-11-15
> **Ohwii said:**
> THANK YOU,spupy,

very helpful. 

just the root thing was kind of tricky.

cheers 

OhWii

Glad to help. About the root:
```
sudo gedit /etc/modules
```

---

