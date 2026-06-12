---
title: "su vs. sudo problem"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-09-08
I know what the root password is. If I sudo anything it asked for the password and accepts it OK. However, if I su it asks for the password and never accepts it.

What would cause this?

Thanks!

---

### Post by bswilson on 2006-09-08
You sure about that?  If you are logged on as a regular user, and use sudo to invoke a privileged command and it accepts the password, then that is not root's password.  It is your regular user account password.

---

### Post by Jucato on 2006-09-08
This page might help: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Daveski on 2006-10-20
I have a little tip if you need to do a series of commands that each require sudo.
I just type

**sudo bash**

and I have a root terminal.
I do all the suff I need root access for and then type **exit** to return my identity.

---

### Post by aysiu on 2006-10-20
Or ```
sudo su
``` or ```
sudo -s
``` or ```
sudo -i
```

---

### Post by ubuntuuser on 2006-10-20
su asks you for the password of the user you want to switch to. So if you are logged in as bill and want to switch to andy, you are asked for andy's password. su without a username switches to root, so you are asked for the root password.

sudo on the other hand is configured to always ask for your own password (at least in ubuntu it's configured that way).
You can change that with the visudo command, but be careful with that.

---

