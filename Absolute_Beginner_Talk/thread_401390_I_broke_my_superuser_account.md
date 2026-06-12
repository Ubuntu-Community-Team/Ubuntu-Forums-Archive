---
title: "I broke my superuser account"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by tjameson on 2007-04-04
First off, I did something very stupid, I messed with my original user account.  Here's my problem:

I wanted to create an administrator account with the administration privileges and all that.  I created an "admin"  user that I thought I gave administrative privileges to and I took off administration privileges for my original superuser account.  The problem is, the new "admin" user cannot manage users and my original user cannot manage users.  I figured out how to allow root to login, but root does not have user management abilities.

I need to know how to create users with privileges to add and remove users (administration privileges) from the terminal.  Thank-you!!

-jameson

---

### Post by Obor on 2007-04-04
This will add existing user into admin group. You will probably have to boot into the recovery mode so you are root and run it there.(change username to yours and groupname to admin)

```
 adduser username groupname
```

i.e  adduser tjameson admin

---

