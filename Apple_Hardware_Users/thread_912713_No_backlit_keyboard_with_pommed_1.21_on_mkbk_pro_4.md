---
title: "No backlit keyboard with pommed 1.21 on mkbk pro 4.1"
date: 2008-09-07
forum: Apple Hardware Users
---

### Post by JECHO on 2008-09-07
hey guys im running ubuntu 8.04 and have got everything working great with the exception of the keyboards backlight. both turning it on manually and the ambient sensor arent working.

like i said ive got ubuntu 8.04 and pommed 1.21. everything works except the backlight. Please help!:confused:

---

### Post by hajk on 2008-09-07
Apart from enabling/configuring keyboard backlighting in /etc/pommed.conf, you must also load the "applesmc" module. There is a problem, though, with this module producing an unending stream of error or debugging messages, filling up the system logs... This problem even persists in the module for the 2.6.26 kernel, reason why I have decided not to use it for now.

---

### Post by JECHO on 2008-09-07
> **hajk said:**
> Apart from enabling/configuring keyboard backlighting in /etc/pommed.conf, you must also load the "applesmc" module. There is a problem, though, with this module producing an unending stream of error or debugging messages, filling up the system logs... This problem even persists in the module for the 2.6.26 kernel, reason why I have decided not to use it for now.



alright so theres no way t fix that? 

Also, are there any problems with the other fn keys (i.e. excessive eror loging, debugging, etc...) that i should know about or fix?

---

