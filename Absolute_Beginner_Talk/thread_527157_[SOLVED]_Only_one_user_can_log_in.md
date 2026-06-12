---
title: "[SOLVED] Only one user can log in"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by gregj5916 on 2007-08-16
I have installed 7.x on my daughters computer and it works great, no issues at all with the install EXCEPT she is the only user allowed to login when the system is booted.  I have myself set up as a user with admin privileges but to no avail.  I created her account first.

How do I get the initial login to allow multiple users?

Thank you.

---

### Post by aysiu on 2007-08-16
> **gregj5916 said:**
> I have installed 7.x on my daughters computer and it works great, no issues at all with the install EXCEPT she is the only user allowed to login when the system is booted.  I have myself set up as a user with admin privileges but to no avail.  I created her account first.

How do I get the initial login to allow multiple users?

Thank you.
What happens when you try to log in?

---

### Post by gregj5916 on 2007-08-16
It rejects my login as invalid username and password.

In the lower right corner of the login screen it says "leah-desktop //" which i should have mentioned before.

---

### Post by aysiu on 2007-08-16
Well, I've never heard of a Linux system *not* allowing multiple user logins.

So it's probably one or more of the following:

1) You mistyped your username or password (either when you created them... or when you're now trying to log in)

2) You have Caps Lock on

3) Something is wrong with your keyboard so that one or more keys repeats or doesn't work... and one of those keys is in your password but not your daughter's password

I think your best bet is to boot into recovery mode. Type ```
cd /home
ls
``` Verify that your username is spelled the way you, in fact, want it to be spelled. Then reset your password: ```
passwd *yourusername*
``` where *yourusername* is your actual username (say, *greg*, for example). ```
reboot
```

---

### Post by gregj5916 on 2007-08-17
The problem was that the user number was not in sync with the user name.  My home directory said the files belonged to user 1001, but the number associated with my login name was 1003.  When i changed it to 1001, rebooted and logged in again it worked fine.

---

