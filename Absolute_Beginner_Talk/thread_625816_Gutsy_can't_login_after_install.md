---
title: "Gutsy can't login after install"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by faux_05 on 2007-11-28
i just installed gutsy from livecd with wubi. it dint install grub so i spent ages trying to get that to work. now that i finally have, ubuntu is booting, but i cant get past the ubuntu graphical login screen. i did specify my user/pass when i was installing, but when i put them in i get the message that user/pass is incorrect. the recovery grub option throws me to a logged in root console. is there any way to check my username & reset my pass, or create a new user/pass from here? or from the livecd?

thanks

---

### Post by DutyDuty on 2007-11-28
Check your CAPS LOCK, and if you remember the root password, try that.

---

### Post by faux_05 on 2007-11-28
the ubuntu installer doesn't ask about a root password. and i have been careful to keep everything in lower case as it was when i enteredt it originally..

i have also tried usin ubuntu/ubuntu, but still no effect

---

### Post by jasay on 2007-11-29
If you have a root console you should be able to change your password with passwd.  It will work something like this (with your login instead of "username"):
```
# passwd username
Changing password for username.
Enter new UNIX password: 
Retype new UNIX password: 

```

If the problem is the username instead of the password you can make a new user like this:
```
adduser username
```

---

