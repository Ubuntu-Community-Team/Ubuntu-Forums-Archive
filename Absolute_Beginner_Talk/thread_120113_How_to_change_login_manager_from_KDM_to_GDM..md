---
title: "How to change login manager from KDM to GDM."
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by rippon on 2006-01-20
I was wondering how to change my login manager from KDM to GDM. I changed it from GDM to KDM so I could use a KDM theme a while back. Now I would like to change it back to the original GDM ubuntu theme, but first I need to change the defualt from KDM to GDM after start-up. Thanks in advance.

---

### Post by morphodone on 2006-01-20
i only have gdm installed but i think the following will work...

sudo dpkg-reconfigure gdm

---

### Post by racecat on 2006-01-20
[QUOTE=morphodone]i only have gdm installed but i think the following will work...

sudo dpkg-reconfigure gdm[/QUOTE]

Right on! If that doesn't come up, this should:

```
sudo dpkg-reconfigure kdm
```

Bill

---

### Post by rippon on 2006-01-21
Thanks!

---

### Post by patrick295767 on 2006-01-21
Also ,to select your login manager:
edit the following file:
```
vi /etc/X11/default-display-manager
```
  
Greetings

Pat

---

### Post by b0rka7a on 2008-01-26
Thanks !! :D

---

