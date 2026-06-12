---
title: "Apache2 - can't write to the dir"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by morficus on 2005-10-02
Well... just got done with Appache.. but I seem to not have the permitions to write to /var/www
so.. how do I change the dir permitions?

also... how do I give myself sudo?
thanx

-morficus

---

### Post by matthewv on 2005-10-02
[QUOTE=morficus]Well... just got done with Appache.. but I seem to not have the permitions to write to /var/www
so.. how do I change the dir permitions?
also... how do I give myself sudo?
thanx
-morficus[/QUOTE]

Changing permissions is done with the chmod command. "chmod 777 /var/www" will allow all users to read and write /var/www, however, you'll probably need to run the command with sudo.

I think you give yourself sudo by making yourself a member of the sudo group.. could be wrong on this though

---

