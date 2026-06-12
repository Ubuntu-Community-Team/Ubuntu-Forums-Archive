---
title: "how to start/stop services in ubuntu"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by bangkok on 2007-05-21
hi gang,

just test driving ubuntu. been FCx user for quite some time but thought i would give ubuntu a test drive on one of my laptops here.

how do i start/stop servicesin ubuntu? i don't even see services* in /sbin.

please don't flame me for using FCx example but it's my comfortable point of reference... 
> sudo service sshd start (because /sbin is in my path)... ez-peezy

but i can't seem to get ssh cooking on ubutu with any kind of variation of /sbin/service. also no luck with finding any useful gui (although i do prefer the terminal to gui).

sorry for the almost-certainly lamer n00b question.

---

### Post by oilchangeguy on 2007-05-21
go to, system, admin, services

---

### Post by Bachstelze on 2007-05-21
With init scripts :

```
sudo /etc/init.d/serviceName (start|stop|rerstart)
```

---

### Post by ruy_lopez on 2007-05-21
You can use the GUI for basic services. Thats in -->System-->Administration-->Services. Mainly, though, I just use "/etc/init.d/<service> start|stop|restart" i.e. "sudo /etc/init.d/ssh start"

---

### Post by glotz on 2007-05-21
Also see [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Medieval_Creations on 2007-05-21
There is also another GUI that is a possible option, BUM (Boot Up Manager).
You can use which ever package manager you prefer to download/install.

---

