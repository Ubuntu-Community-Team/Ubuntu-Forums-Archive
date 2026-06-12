---
title: "Update / user admin problems"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by jakobp on 2006-05-26
Ok... just installed Breezy Badger, but about to go crazy ](*,) 

When installing I added myself as a daily user (as an alternative to a root user, so I at least could log on to Gnome). When logging on I would like to have the updates shown, but I receive an error (Child process ended at -1 and similar things) or nothing happens. What is this all about? Preferably I would like to be able to get full read/write priviliges for the system (i.e. log on as root user in Gnome)as I am the only one using it, and installed it to familiarise myself with Ubuntu. Doe anyone know how?

---

### Post by Sef on 2006-05-26
> When installing I added myself as a daily user (as an alternative to a root user,

1) Did you do an expert install?

2) If not, you are not in root user.  

3) Root is disabled by default.

4) Read this > [RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by jakobp on 2006-05-26
Thanks,

Did install in expert mode, so the root user account is enabled. Am trying to change user privilige in Gnome (Administration -> user/groups), but when promted for password and entering User account password, nothing happens i.e. the user administation program does start. Would I have to add my 'daily user' as sudo, and in that case how do I do this? Tried opening visudo (export EDITOR = gedit && sudo visudo) but reported error. What should I do?

---

