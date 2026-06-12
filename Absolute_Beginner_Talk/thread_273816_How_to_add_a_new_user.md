---
title: "How to add a new user"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by afbase on 2006-10-08
how would one add a user with his own directory?

---

### Post by CatKiller on 2006-10-08
System -> Administration -> Users and Groups

---

### Post by afbase on 2006-10-08
> **CatKiller said:**
> System -> Administration -> Users and Groups

I use CLI.

---

### Post by CatKiller on 2006-10-08
> **afbase said:**
> I use CLI.

Then **man adduser** will tell you all you need to know.

---

### Post by zeveck on 2006-10-24
How do you install the Users and Groups tool? I did an Ubuntu server install and do not appear to have it. I tried KUser, but it doesn't appear as full featured as this amazing tool everybody keeps talking about!

---

### Post by taurus on 2006-10-24
> **zeveck said:**
> How do you install the Users and Groups tool? I did an Ubuntu server install and do not appear to have it. I tried KUser, but it doesn't appear as full featured as this amazing tool everybody keeps talking about!

The Users Groups tool is from Gnome!!!  You can add user from a terminal with

```

sudo useradd -m -G cdrom,video,audio,games john
sudo passwd john
-or-
man useradd

```

---

