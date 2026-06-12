---
title: "Cannot Login as new User"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2007-01-03
I've just created a new user on my system using the "Users And Groups" app, but when I try to login it first complained that the user has no /home. I checked, this was true, so I created a /home folder. Next attempt, it complains that the .dmrc is damaged. Well, it doesn't have one. Clearly all the files meant to be in /home weren't generated with the user, how do I solve this?

---

### Post by bluefrog on 2007-01-03
you created the /home/user directory in console? (sudo mkdir /home/user  ?)

if yes then you need to change the owner of this folder:
sudo chown -R user.user /home/user

if it still fails, create a new user with the GUI tool and make sure it has the correct folder in the advanced tab/advanced settings/home directory. then try to login and tell us the outcome.


what version of Ubuntu?  (in console    lsb_release -a | grep Codename)

James

---

### Post by amo-ej1 on 2007-01-03
and you willl also want to copy the files located in /etc/skel (ls -al since they're hidden) to the new homedirectory.

---

### Post by happy-and-lost on 2007-01-05
@bluefrog

Worked a charm thanks :)

---

### Post by Bachstelze on 2007-01-05
And next time, use the command line instead :)

```
sudo useradd -m USER_NAME
```

---

