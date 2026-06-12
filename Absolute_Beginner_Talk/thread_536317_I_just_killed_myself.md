---
title: "I just killed myself"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by michaelbesselman on 2007-08-27
Boy did it hurt!!!

When I got an account on my computer it was done under another person's account and I had admin privileges.  That person left and I removed his account and my admin privileges went away...:(

I know the root password, but have no way of modifying my permission.  And of course Ubuntu does not allow you to log in as root.  What can I do?

:lolflag:

Thanks

Michael Besselman

---

### Post by schorsch on 2007-08-27
Login as your user and do
```
su -
```
enter root password. Now:
```
usermod -aG admin *your_user_name*
```
and you should be done.

---

### Post by Seisen on 2007-08-27
You can try putting this in the terminal 

```
sudo adduser $user admin
``` change user to whatever you username is.

---

### Post by p_quarles on 2007-08-27
I took the OP to mean that he couldn't *use* sudo. 

When you say you know the root password, do you mean that you know the previous sudoers password (the account you deleted), or that the actual root password was set and you have it? If the latter:
```
su
```
and type in the root pwd.

If not, you'll have to boot into single user mode.

---

### Post by schorsch on 2007-08-27
Uhm, well, yes ...... you are right! It's getting late here .. ;-)

---

