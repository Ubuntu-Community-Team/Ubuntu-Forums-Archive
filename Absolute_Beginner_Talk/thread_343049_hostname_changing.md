---
title: "hostname changing"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-01-20
how do i change my hostname from what it currently is to something else?

Is there a way to do this in the console?

---

### Post by NeoLithium on 2007-01-20
I think if you have gnome, you can go into System -> Administration -> Network and it should list the one you selected at installation, just change it there.

---

### Post by taurus on 2007-01-20
Better make sure when you change hostname (/etc/hostname), you change /etc/hosts to the same name too or you won't be able to use sudo and your network would be dead.

---

### Post by Pobega on 2007-01-20
> nano /etc/hosts
nano /etc/hostnameJust make sure that they're both the same name for your local machine, otherwise you may run into difficulty using sudo with network applications.

**Edit:** Taurus beat me to it.

---

