---
title: "how we can enter as a root user"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by cnu_sree on 2007-08-07
Iam new to ubuntu.
i enter my root name and password.
but i am getting an error as "unable to login from this screen".
how can i enter as a root user in ubuntu

---

### Post by hyper_ch on 2007-08-07
why do you want to login as root?

---

### Post by cnu_sree on 2007-08-07
i want  to test my project in root

---

### Post by CheeseEatingBulldog on 2007-08-07
That is a security feature, as it is not wise to log in as root. You can change this setting by allowing root login, I think it is under log in window --> allow local sys admin login.

But once again, this is NOT recommended.

---

### Post by hyper_ch on 2007-08-07
normally you assume temporary root rights in *buntu with 
```

sudo ...

```

---

### Post by Jimmyfj on 2007-08-07
Have you tried the gksu <filename> option? This will start the program in root mode:

gksu nautilus (just as an example)

---

### Post by silent1643 on 2007-08-07
[[IMG]http://img255.imageshack.us/img255/2396/rickjamesbk6.th.jpg[/IMG]](http://img255.imageshack.us/my.php?image=rickjamesbk6.jpg)

sorry had to :D

---

