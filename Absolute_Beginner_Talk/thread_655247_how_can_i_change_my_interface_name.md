---
title: "how can i change my interface name"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by linux44 on 2008-01-01
hi 
what command do i need to use in order to change my interface name ?
i mean like change etho to any thing i want 
any help please?

---

### Post by RomeReactor on 2008-01-01
Hi. Are you having connectivity problems? are you getting two interfaces labeled the same?

---

### Post by linux44 on 2008-01-14
hi 
the problem is i have 3 int and want to change their name (confusion)
can u please help

---

### Post by szymon_g on 2008-01-14
you have to (re)write udev rules

---

### Post by linux44 on 2008-01-14
hi
i have change my interface name in 2 place and it has successfully changed but the only problem is when i click on network tools it can show the int name but when i click on configure it say interface doe not exist
.....
the place i have used to change int name
/etc/udev/rules.d/70-presistant....
/etc.network/interfaces
is there any where else that i have to change?
thanks

---

### Post by szymon_g on 2008-01-14
read that. seems to be a nice howto

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

btw, is it thread for 'absolute beginner talk' :-)?

---

### Post by linux44 on 2008-01-15
just can u tell 
where are the place that int name are stored 
apart from the 2 place i said

---

