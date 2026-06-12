---
title: "su command"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by pcl on 2007-05-15
Hi,
After my previous post which noone could find an answer yet, I have purchased an Introduction book to unix.
Now I would like to understand why when I type in su my current user password is ineffective "auth...failure" I don't remember having registered any other pwd.
Any help still welcome for my first issue with Ubuntu...
pcl

---

### Post by chamberlain2006 on 2007-05-15
Su changes the current user.  Doing sudo su will result in a change to the root user account.  Doing su *user* will result in a change to the specified user.  In any case, you will need to know the password of the specified user.

---

### Post by wormser on 2007-05-15
The su command is switching to the root or super user account.   By default Ubuntu disables the root account.  To set a password for root type in **sudo passwd root**.  But you really do not need to do this.  If you need rights to install a program or what ever just use the **sudo** command before the command.  Then type in your password.

---

### Post by annda on 2007-05-15
hi!

su needs a root password. root account is disabled by default in ubuntu. use sudo before any command that needs root privileges and type your user password.

---

### Post by pcl on 2007-05-15
Thanks

---

