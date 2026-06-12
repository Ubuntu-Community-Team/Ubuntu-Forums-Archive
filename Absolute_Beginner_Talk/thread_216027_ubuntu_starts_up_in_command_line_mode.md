---
title: "ubuntu starts up in command line mode"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by stripeypants on 2006-07-14
Hi, I installed 6.06 on a an ibook g3.

Everything seemed to go fine during the install.

When the system starts up, there is no gnome or kde; it just asks for a login in text mode.  I can log in and browse the filesystem no problem.

how do i get gnome to start up automatically?

---

### Post by adam.tropics on 2006-07-14
if you log in and enter

```
startx
```

what happens?

---

### Post by kinematic on 2006-07-14
did you by any chance install the server edition?
if so do a "sudo aptitude update" and then "sudo aptitude install ubuntu-desktop"(without the quotes)
you will be asked for your root password,that's the one you set up during install.

---

### Post by aysiu on 2006-07-14
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

