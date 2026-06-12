---
title: "root"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-02-21
how to I change into the root directory

---

### Post by aysiu on 2008-02-21
> **harryliddic said:**
> how to I change into the root directory
```
cd /
``` or ```
cd /root
``` depending on what you mean by "the root directory."

If you mean "How do I make changes to root-owned files?" then you should read [this tutorial](http://www.psychocats.net/ubuntu/permissions).

---

### Post by zerhacke on 2008-02-21
sudo cd /root

---

### Post by Sukarn on 2008-02-21
> **zerhacke said:**
> sudo cd /root

You don't need to type sudo for that

---

### Post by aysiu on 2008-02-21
> **zerhacke said:**
> sudo cd /root
Actually, you don't need to use *sudo* to change to the root directory. See the attached screenshot.

---

### Post by harryliddic on 2008-02-21
sudo cd / gets a unknown command reply I need to get to ROOT@ROOT directory so I can mount my cdrom so I can install Corel WP 8

---

### Post by aysiu on 2008-02-21
You don't use *sudo cd /*. ```
cd /
``` alone should do it.

If you're trying to mount a CD-ROM, you shouldn't have to change to the / directory anyway. Something like ```
sudo mount /media/cdrom0/
``` should suffice.

Are you should Corel WP 8 will install in Ubuntu, anyway?

---

