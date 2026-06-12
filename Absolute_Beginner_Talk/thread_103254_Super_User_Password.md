---
title: "Super User Password?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Kreat on 2005-12-13
Hey everyone.  I had an old version of Ubuntu and then got a wireless system in my house and my wireless card wasn't supported.  Well the new one supports it so yay get to learn linux now that i've basically mastered that piece of crap OS ::cough windows::  But I have a problem.  

When I did my first install it asked me for the SU password i wanted.  This time when i reinstalled, it never asked me and I can't install any programs w/o having the su password.  Is there a way to retrieve this, or to set up another user for su?  Thanks

---

### Post by nikopol on 2005-12-13
the first user is in fact the su user of sorts.

if you want to do something as su type:
```
sudo <command-you-want-todo>
```
and enter the password for the main user and it will execute as root.

If you don't want to add sudo to every command in a terminal session type:
```
sudo -s 
```
and you will be as root in that terminal. 

Does that help?

---

### Post by Kreat on 2005-12-13
Yeah I think that will do it.  I just need to start learning some of the basic commands.  Thanks a lot for the help =)

---

### Post by nikopol on 2005-12-13
No problemo :)

BTW, it is possible to setup a root (su) account that is seperate from the main one but sudo tends to work fine so I stuck with it.
See here if you want to set a root password
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

---

