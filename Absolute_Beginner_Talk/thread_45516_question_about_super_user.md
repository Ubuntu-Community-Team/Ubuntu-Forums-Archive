---
title: "question about super user"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by kook44 on 2005-06-30
Can someone explain how the whole disabling root/sudo thing works?  When I use sudo commands, I enter my password (the password I created for the default user "foo" during install).  Does that mean foo is the super user? Or that ubuntu just takes the password you specify during install and uses that for the root password?

---

### Post by jasmuz on 2005-06-30
[QUOTE=kook44]Can someone explain how the whole disabling root/sudo thing works?  When I use sudo commands, I enter my password (the password I created for the default user "foo" during install).  Does that mean foo is the super user? Or that ubuntu just takes the password you specify during install and uses that for the root password?[/QUOTE]
 The user **Foo** is a normal user who is listed in the sudo allow file, this means he can run certain superuser privilages, as whereas a normal user not listed couldnt.

When a normal user uses sudo, he becomes the superuser in a temporary basis.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=kook44]Can someone explain how the whole disabling root/sudo thing works?  When I use sudo commands, I enter my password (the password I created for the default user "foo" during install).  Does that mean foo is the super user? Or that ubuntu just takes the password you specify during install and uses that for the root password?[/QUOTE]


We don't have a root account in Ubuntu- At all by default. Instead the regular user becomes a super user by using the sudo command. That way no one is tempted to run as root all the time (really bad thing to do).

Apples do the same thing.

---

