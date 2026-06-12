---
title: "Simple LAMP"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-03-30
Is there a simple lamp server available for ubuntu? something like XAMPP, or WAMP Server on windows.. where i get a menu entry and can just start / stop from there :)

---

### Post by zvacet on 2007-03-30
In Ubuntu server you have option to install LAMP.You can also install desktop version and after that LAMP.I don´t know wich way is better because I never use server.Anyway you can get LAMP with Ubuntu.

---

### Post by JNowka on 2007-03-30
You need to install Apache2, PHP5, and MySQL5

There are no icons like that, to my knowledge, but I created my own menu icons with the commands to do just that.  This is the commands for the shortcuts:

Start:  
gksu 'apache2ctl start'

Stop:  
gksu 'apache2ctl stop'

Restart: 
gksu 'apache2ctl restart'

Hope this helps.

p.s.  if you are running kubuntu change all the gksu to kdesu, and do not leave out the apostrophe.

---

