---
title: "Root pwd"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by happyhacker on 2007-01-10
I have just installed UBUNTU 6.06 from a mag cd. I have my log-in fine, but I cannot get into root. I want to start up SWAT and SAMBA.

What is the default pwd for root? It is not "", root, <PCname>,!!

---

### Post by jvc26 on 2007-01-10
your root password is your user password - 'sudo' and the password is the one you use to log in.
Il

---

### Post by Bachstelze on 2007-01-10
There is no root password by default in Ubuntu :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Modernity on 2007-01-10
If you are going to use root, you will have to change the root password.

---

### Post by happyhacker on 2007-01-10
Sorry, hav'nt made myself clear.

Normal login: name=abcd; pwd=abcd OK login fine.

Want to change smd.conf to get windows networking going.

Can't edit smd.conf as it's owned by root. All permissions greyed out.

Switch user:

login: name=root; pwd (not been setup since install)=?????

---

### Post by glotz on 2007-01-10
Try gksudo gedit smb.conf. Then enter abcd as password.

---

### Post by pcomelade on 2007-01-10
The password for root is generated randomly during the installation. It is supposed that you don't need to know it if you use "sudo" instead. Nevertheless, you can change it:
$ sudo password root

and work with "su" as can be done in others distributions

Hope this helps,
Cheers

M;

---

### Post by scheuri on 2007-01-10
> **HymnToLife said:**
> There is no root password by default in Ubuntu :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

PLEASE read that...it will explain a lot to you!
It will not necessarily solve your problem, however it will help you to understand.

Thanks
Stefan

---

