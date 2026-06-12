---
title: "Lost Username and Password!"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Slenkar on 2006-05-28
Hi I know how to use GRUB and change my root password
but I lost my Username and userpassword

I can only get as far as the input screen when you hear the drum noise.

Is there a way to completely get rid of the login screen when I do recover my username and password?

and how do I recover them? (or create a new user from GRUB)?

thanks

---

### Post by Rinzwind on 2006-05-28
You need to goto into failsafe mode (from Grub).

When you are at failsafe you'll have a #
With that you can do a:
**more /etc/hosts**

Your username is probably somewhere along the last lines of this file.

**passwd {username}**

will let you have your username another password. After that you can login again with the new password.

---

### Post by hw-tph on 2006-05-28
In GRUB, select Recovery Mode. When the system is up and running in single user mode, type **passwd username** where username is the name of your user (list the contents of the /home directory to see what regular users exist.


Håkan

*Edit:* I was beaten to the punch, but the file that lists all users (both regular and system users) is /etc/passwd, not /etc/hosts.

---

### Post by Slenkar on 2006-05-28
Thanks guys that worked!

---

