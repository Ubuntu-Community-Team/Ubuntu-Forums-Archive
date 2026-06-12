---
title: "User Accounts"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-07-09
Right got Ubuntu on now, however upon research I hear there is no root, so my  account which i created during install, is this one for like surfing around the net on or should i create another one?

---

### Post by aysiu on 2006-07-09
Read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

and this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Dinerty on 2006-07-09
Thanks for that mate I understand it now, so infact it does not matter what account I use (Using the one created for initial install) i use sudo <command> and then loggout from terminal that way.

But i could access a root as a account if need be

---

### Post by aysiu on 2006-07-09
Well... sort of.

The first account you create during installation belongs to the *admin* group, which is allowed to *sudo* commands for temporary root privileges.

You can create accounts that are **not** part of the *admin* group, and those people will not be allowed to *sudo* anything.

But... you can also create new accounts that *are* part of the *admin* group, and they will be able to *sudo*.

---

