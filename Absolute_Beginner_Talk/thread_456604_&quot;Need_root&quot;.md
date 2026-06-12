---
title: "&quot;Need root&quot;"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-27
Is there any way to make your login name equivalent to root in the OS's eyes? I have added myself to the root group and I have full permissions, but every once in awhile I'll come across a command that tells me that I need root privileges.

---

### Post by DJ Wings on 2007-05-27
Use "sudo passwd root" to set the root password.

---

### Post by yabbadabbadont on 2007-05-27
```
sudo -i
```
will drop you into a root shell.

---

### Post by virgilnilson on 2007-05-27
Thanks to both of you. =]

---

### Post by mocqueanh on 2007-05-27
When you login as root in Ubuntu, you'll inside the bash shell environment ( similar to DOS ). It's not easy for new bie.
You can set root password by using User and Group Manager in Syste>Administration.

And if you want to do some things that only root can do.
Open terminal, type the command, and preface the command with sudo (shortname of super user do ).If you are asked pasword, type your account's password (not root password).

Example:

sudo gedit /etc/fstab

This will edit the file: /etc/fstab in Gedit (text editor ) because this file belong to root.

---

### Post by virgilnilson on 2007-05-27
> **mocqueanh said:**
> When you login as root in Ubuntu, you'll inside the bash shell environment ( similar to DOS ). It's not easy for new bie.
You can set root password by using User and Group Manager in Syste>Administration.

And if you want to do some things that only root can do.
Open terminal, type the command, and preface the command with sudo (shortname of super user do ).If you are asked pasword, type your account's password (not root password).

Example:

sudo gedit /etc/fstab

This will edit the file: /etc/fstab in Gedit (text editor ) because this file belong to root.

Thank you. =]

---

