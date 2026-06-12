---
title: "root"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by djstarrock on 2006-10-21
how do u login root

---

### Post by bulldog on 2006-10-21
You can't!

It's disabled by default for security reasons.

You can become root when you're logged in by typing sudo -s.

This make you root till you type exit.

Normally you use sudo or gksudo for graphical applications,to do your administrative tasks.

---

### Post by Sef on 2006-10-21
Root is turned off by default.  Use Sudo.  It is a command that temporarily opens root when you need it.  With root turned off your system is much safer, and you have one less password to remember.

---

### Post by pstep9407 on 2006-10-21
I may be wrong about this, but I think Ubuntu does not allow root login(?). You can become rot with:
```
sudo su
```

---

### Post by djstarrock on 2006-10-21
thanx

---

### Post by madmetal on 2006-10-21
or give 
sudo passwd 
and then create a root password..
then su will work...

---

### Post by Gannin on 2006-10-21
You can also type "sudo bash" and that will give you root access until you type "exit".

---

