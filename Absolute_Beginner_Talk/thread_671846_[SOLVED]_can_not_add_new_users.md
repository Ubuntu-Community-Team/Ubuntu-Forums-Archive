---
title: "[SOLVED] can not add new users"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by chuck88 on 2008-01-19
when I try to add new users nothing happens I type in the required info press ok and nothing.
I put in the command line users-admin and got The configuration could not be loaded You are not allowed to access the system configuration.

---

### Post by sumguy231 on 2008-01-19
Try doing it from a terminal with:
```
sudo adduser <username_goes_here>
```
Where <username_goes_here> is replaced with what you want the username to be. Report back on what happens.

---

### Post by aysiu on 2008-01-19
Try ```
gksudo users-admin
```

---

### Post by chuck88 on 2008-01-19
command said only one or two users is allowed

---

### Post by sumguy231 on 2008-01-19
Can you post exactly what you typed?

---

### Post by chuck88 on 2008-01-19
now I git  The group `chuck' already exists. but I don't want a group I want a user

---

### Post by chuck88 on 2008-01-19
alright I was just able to add a new user with a name I had never used before, but how do I erase the old name completly, so I can use it again if I want?

---

### Post by aysiu on 2008-01-19
> **chuck88 said:**
> alright I was just able to add a new user with a name I had never used before, but how do I erase the old name completly, so I can use it again if I want?
```
gksudo users-admin
``` is also known as System > Administration > Users and Groups

Once that dialogue opens, select **Manage Groups** and you can delete whatever groups you want.

---

