---
title: "Create a User with no shell?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by netglen on 2007-08-03
Is there a way to crate a new user but don't give it a shell? I want to be able to logon with the account and all it does it run a tail of a log.

---

### Post by dreadlord_chris on 2007-08-03
```

sudo adduser --shell /bin/false NAME GROUP

```
This will create a user (NAME) with no login shell

---

### Post by apswartz on 2007-08-03
Yes, after you create the user, edit the /etc/passwd file... (this is potentially dangerous)
```
sudo vim /etc/passwd
```
or you can use a friendlier editor like nano instead of vim.

Where you see the shell entry in the user's line (at the very end), change it to /bin/false
There should be other entries like it, so you can follow the examples. Do NOT mistakenly delete the colon before the entry.

Oops,
forget my suggestion and use **dreadlord_chris**'s -- much easier.

---

### Post by netglen on 2007-08-03
Now is there a way to pass the "tail -f xxxxlog" or "tail -f xxxxlog | grep xyz" after the /bin/false in the passwd file?

---

### Post by Peter76 on 2007-08-03
A little experiment came up with this. Create the user, and under the advanced tab set the shell to a script that executes the tail command ( I put this in the users home directory, don't forget to make it executable ). I couldn't get ```
 tail -f /var/log/syslog
``` to work directly; that's why the script.

NB! I'm NOT sure how secure this is! If I hit ctrl-c, It throws me back to my normal user ( switched user with su ) Somebody with more expertise might give some comments here.

---

### Post by physx on 2007-08-03
My understanding is that the shell piece of user setup just runs a program -- universities used to use this on Unix machines to only allow folks to run email, for example.  If you try logging in without 'su', it should knock you back to a login command if you do the ctrl-c (but I can't check now).

Hope this helps!

---

