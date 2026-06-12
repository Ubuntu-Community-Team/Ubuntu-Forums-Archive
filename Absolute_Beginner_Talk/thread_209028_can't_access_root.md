---
title: "can't access root"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by inf4my on 2006-07-04
when installing I created my username and password and I login to those but to access a lot of files I need to have root access and it does not accept my password and user name as the super account so i cannot change file permissions.

---

### Post by wolfmaniac on 2006-07-04
u have to enable login of root from GDM(KDM)

---

### Post by dougmwpsu on 2006-07-04
i'm way way new at this, but when i need to preform an action as root, i use the sudo command in the terminal.  i'm not sure if there is a way to log into gnome as root.

---

### Post by aysiu on 2006-07-04
I think instead of enabling root, you should try to fix why you can't use your password and username as the super account.
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Once that's fixed, you don't need root:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

[quote=dougmwpsu]i'm not sure if there is a way to log into gnome as root.[/quote] There is, but it's completely unnecessary and actually wastes time over just creating a "browse as root" launcher or keyboard shortcut.

---

### Post by dougmwpsu on 2006-07-04
[QUOTE=wolfmaniac]u have to enable login of root from GDM(KDM)[/QUOTE]


how do you do that?

---

### Post by aysiu on 2006-07-04
[QUOTE=dougmwpsu]how do you do that?[/QUOTE]
A better question would be *why* would you want to do that?

---

### Post by wolfmaniac on 2006-07-04
go to login screen setup (if u r in ubuntu i think it can be reached by clicking 3rd tab then administration)
i m using XFCE

then click security tab and chec the box of local sys administrator login.

---

