---
title: "How to remove from desktop jre 1.6.0_01locked folder."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-05-11
How to remove from desktop jre 1.6.0_01locked folder. 

When I try to delete, it says you do not have permission to remove.I am a single user .

---

### Post by Najand on 2007-05-11
> **drpas2k said:**
> How to remove from desktop jre 1.6.0_01locked folder. 

When I try to delete, it says you do not have permission to remove.I am a single user .

```
sudo rm -rf /Desktop/jre\ 1.6.0_01
```

---

### Post by drpas2k on 2007-05-11
I tried .Failed.

---

### Post by Najand on 2007-05-11
Any error messages?

---

### Post by drpas2k on 2007-05-11
Cannot move "/home/ohm...e1.6.0_01" to the trash because you do not have permissions to change it or its parent folder.

---

### Post by Najand on 2007-05-11
Did you use the command I gave you in a terminal or just tried to drag and drop it into the trash box?

---

### Post by nbayiha on 2007-06-11
what you can do is 
open a terminal first of all
 after 
```
cd Desktop 
sudo chmod a+rw 
 
```

and now you can go back to your Desktop and everything will be fine

---

### Post by Seisen on 2007-06-11
You could also try this.

```
gksudo nautilus
``` and it will give nautilus super user rights.

---

### Post by lazyart on 2007-06-11
> **Seisen said:**
> You could also try this.

```
gksudo nautilus
``` and it will give nautilus super user rights.

Use this only if the other stuff doesn't work.  gksudo + Nautilus can also be used to do a lot of unintentional damage.

---

### Post by @vijay@ on 2007-06-11
try this may be  it will work

first change the permissions

sudo chmod -R 777 /Desktop/jre\ 1.6.0_01

and as above told

sudo rm -rf /Desktop/jre\ 1.6.0_01

---

