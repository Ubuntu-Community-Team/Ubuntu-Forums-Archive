---
title: "root password?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Aan Vazhapilly on 2007-08-26
Hi I just installed ubuntu (Fiesty Fawn) on Dell laptop and while installing installer asked for username and password and i gvve them and it installed sucessfully.

I need to know root password now?
How can i find it? Is there a default password for root?

Thanks much
-AAn

---

### Post by llamakc on 2007-08-26
sudo passwd root

---

### Post by Aan Vazhapilly on 2007-08-26
got it.Thanks

---

### Post by kerry_s on 2007-08-26
> **Aan Vazhapilly said:**
> Hi I just installed ubuntu (Fiesty Fawn) on Dell laptop and while installing installer asked for username and password and i gvve them and it installed sucessfully.

I need to know root password now?
How can i find it? Is there a default password for root?

Thanks much
-AAn

your password is the root password.
if you add a root passwd with>  sudo passwd root < you just cut security in half. run> sudo passwd -l root  <to remove the root passwd you set.

---

### Post by init1 on 2007-08-26
> **kerry_s said:**
> your password is the root password.
if you add a root passwd with>  sudo passwd root < you just cut security in half. run> sudo passwd -l root  <to remove the root passwd you set.
Yes, but it is far easier to use su once instead of sudo every time.

---

### Post by anewguy on 2007-08-26
If you want to be able to log on to the desktop as root send me a private message.  It's a simple 2 step process, but I don't want to post it here because this is the "Absolute Beginner Talk" forum, and I don't think it's wise for the novice to have direct root access.

---

### Post by kerry_s on 2007-08-26
> **init1 said:**
> Yes, but it is far easier to use su once instead of sudo every time.

sudo su <is the equivalent of> su
and you don't cut your security any.

---

