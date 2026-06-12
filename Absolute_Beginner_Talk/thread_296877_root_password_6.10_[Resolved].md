---
title: "root password 6.10 [Resolved]"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by bigbadben on 2006-11-10
hi.................
dont know if i missed something..but at installation i never been asked for a root password.

so my problem is, when i try to (as root) upgrade or install or update. i dont have permission, has im not root.

how can i get to root, when i never input a password at installation.

when i su, it tells meto input my password.
but there is none.???

How to change this........... ;(

thx in advance

---

### Post by llamakc on 2006-11-10
Ubuntu uses sudo by default, so instead of attempting to `su` to root, type:

sudo nameofcommand

and it will prompt for your user password, but allow you to perform root's administrative tasks.

If you want to enable root, and please don't if you're new to Linux (but if you're more comfortable with it as I am), do:

sudo passwd root

and enter YOUR user p/w first, and then root's password. All fixed.

---

### Post by Sef on 2006-11-10
Read [RootSudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Bachstelze on 2006-11-10
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And by the way, *sudo passwd* will be enough since it will run *passwd* as root ;)

---

### Post by bigbadben on 2006-11-10
thx:mrgreen:

---

### Post by fseigert on 2007-03-31
There isn´t possible to login with root in first register screen!

---

