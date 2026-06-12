---
title: "Forcing tomcat6 to start when i boot up?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by iangregson on 2007-09-25
Hi there,

I recently went through a guide to install apache/tomcat6 etc on ubuntu .. and it works... i issue this command to start tomcat

 sudo /usr/share/tomcat6/bin/./startup.sh 

but i was wondering if i can get everything to automatically start when i boot up?

Also would it possible to get my PC to automaticallly log me in with my user and password on gUI...

Any advice really appreciated

tHANKS

---

### Post by Dr Small on 2007-09-25
If you run the following two commands, it should make it automatically start at bootup:
```
ln -s /usr/share/tomcat6/bin/./startup.sh /etc/init.d/tomcat6
update-rc.d tomcat6 defaults
```

And to make your pc to auto-login, type 
```
gksudo gdmsetup
```

Security Tab > [Check] Enable Automatic Login... enter the users name.

Dr Small

---

### Post by iangregson on 2007-09-25
Cool! got it automatically loggin in now,..

These commands, what do they actually do?

ln -s /usr/share/tomcat6/bin/./startup.sh /etc/init.d/tomcat6
update-rc.d tomcat6 defaults

and what if i need to remove it later??

I found something ... System Prferences, Sessions, startup programs... is this the same thing??

Thanks again

---

### Post by Dr Small on 2007-09-25
I am pretty sure those commands will start tomcat6 as a daemon at startup. I was given those commands, a long time ago, and they served my purpose. How to remove them ? No idea, but there is bound to be some way.

You could try startup programs, although I thought that was for GUI and not daemons.
But have a shot at it!

Dr Small

---

### Post by iangregson on 2007-09-27
thanks!! much appreciated

---

