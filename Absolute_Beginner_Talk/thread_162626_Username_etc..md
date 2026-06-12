---
title: "Username etc."
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-04-19
I am having a strange problem. Every time I try to login, Ubuntu reads my username incorrectly for the first time (there is an error message which says "Authentication Failed"); when I re-type the same username the second time, I get accepted.

What could be the problem?

Is there some way for me to change my username and password?

---

### Post by uteck on 2006-04-19
As odd as it sounds, you change your password with the adduser command followed by the user name.  "sudo adduser bob" it will then ask for a password, and to confirm the password.
But it is odd that it is failing on the username.  I would suspect that GDM may be putting a space on the end of the name the first time, and that it has that version cached.

---

### Post by xenmax on 2006-04-19
To change your password, you can simply type ```
passwd
``` This will ask for your current password and then you can specify a new password.

---

### Post by cgjones on 2006-04-19
To change your password, type the following at a terminal:
```
passwd
```
This will prompt you for your current password, then the new password

To change your username, type the following at a terminal:
```
usermod -lm *newusername*
```
This should change your username and copy your current home directory to the home directory of your new username. I'm not sure how the ownership of your files will be affected though.

---

