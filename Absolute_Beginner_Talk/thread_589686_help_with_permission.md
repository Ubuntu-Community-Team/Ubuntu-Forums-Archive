---
title: "help with permission"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-24
i have to do this ---------
Just add the appropriate lines to your /etc/apt/sources.list 

it wont allow me to change it im soz for help pls wil someone tell me how to edit that file -
do i have to login as root?? if so wat is default root passowrd?

---

### Post by Seisen on 2007-10-24
Just type in ```
gksudo gedit /etc/apt/sources.list
``` and enter you password in the terminal.

---

### Post by MegaJim on 2007-10-24
Drop into a terminal and enter

```
sudo gedit /etc/apt/sources.list
```

---

### Post by BillDozer on 2007-10-24
gksudo gedit /etc/apt/sources.list

And use your own password

But you can also use the menu:
System / Administration / Somthing with source (can't remember the menuitem)

---

### Post by reza81 on 2007-10-24
> **BillDozer said:**
> gksudo gedit /etc/apt/sources.list

And use your own password

[B]But you can also use the menu:
System / Administration / Somthing with source (can't remember the menuitem)[/B]

If you do use:
sudo gedit etc/apt/sources.list ... Don't remove any line of text. To disable, you can put a "#" at front of a line.

---

