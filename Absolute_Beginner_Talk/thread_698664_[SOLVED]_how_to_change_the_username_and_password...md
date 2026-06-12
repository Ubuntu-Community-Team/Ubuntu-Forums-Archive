---
title: "[SOLVED] how to change the username and password..."
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-16
...via command line? I'm logged in as root. do i do "pwchange" or something?

thanx!


sv

---

### Post by spiderbatdad on 2008-02-16
Are you trying to create a root password or change your user password?

To change user password, you do not need to be root. just enter```
passwd
```

---

### Post by Rocket2DMn on 2008-02-16
To fiddle with the password of the user, you use the passwd command.  To change settings for the user, you use the usermod command.
Ex:
```
passwd bob
```
Will prompt you for a new password for the user bob.

```
usermod -l bill bob
```
Will change the login name from bob to bill.  You will probably have to use usermod to change the home directory as well.

Please proceed with caution using these commands, read the man pages, etc, etc.  They require root privileges (which you have already).  You can also just run passwd from the user account to change your password, no root login necessary.  Make sure the user is not logged in when you try to change the name or home directory.

---

### Post by staticvoid on 2008-02-17
cool thanx! i found if you want to add a user you just do,
```
adduser
```

awesome stuff the cli is :)

again, thank you for your quick responces,

sv

---

