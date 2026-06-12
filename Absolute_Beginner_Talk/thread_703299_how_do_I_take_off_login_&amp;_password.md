---
title: "how do I take off login &amp; password ?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by carioca on 2008-02-21
hi, ubuntu linuxers!

:confused:

I've just installed ubuntu 7.10 and I'm a fresh linux user. how do I take off login & password to open directly to ubuntu? fyi I use ubuntu 7.10 in dual boot with xp pro. I'd appreciate your helpful hints. best regards.

:lolflag:

---

### Post by tangibleorange on 2008-02-21
Hi there! Try typing the following into a terminal (Application --> Accesories --> Terminal):

```
gksu gdmsetup
```

Then on the window that pops up, click the "Security" tab, and then select the user you want to login on the "Automatic Login" drop-down box.

Hope that helps!

---

### Post by thisismalhotra on 2008-02-21
> **carioca said:**
> hi, ubuntu linuxers!

:confused:

I've just installed ubuntu 7.10 and I'm a fresh linux user. how do I take off login & password to open directly to ubuntu? fyi I use ubuntu 7.10 in dual boot with xp pro. I'd appreciate your helpful hints. best regards.

:lolflag:

I would say setup autologin on whatever user you want to, you can do this in

System -> Administration - Login Windows
 and in security tab setup autologin for whatever user you want...

---

### Post by jcitguy78 on 2008-02-21
It may seem like a pain but having to login helps to keep your friends that don't know how linux works from clicking around your machine and messing things up, just a thought, works for small children too. :lolflag:

---

