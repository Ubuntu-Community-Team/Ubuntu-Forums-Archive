---
title: "[SOLVED] new Gutsy install password problem"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2007-11-04
Hi, I've just done a fresh install of Gutsy Gibbon and I've got a problem with the username/password - at no point has it asked me to set up any users, or to set a root password; otherwise, the install went fine (using the alternate CD), smooth install with no problems, booted right up to the gdm login screen and sat there.  Any ideas what to do now? :-s

---

### Post by Pumalite on 2007-11-04
Ubuntu does not use root name or password, but it does use username and password. You might have a defective CD. Did you do md5sum on iso before burn and installation?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sailor2001 on 2007-11-04
system/admin/login window.........set users ,  etc..

---

### Post by Big_Croc7 on 2007-11-04
The problem is, I can't log in to set up any users... I get the gdm screen where it asks for a username, and that's it.  A while back, when I did my Dapper install, I remember there being a screen to set up a first user account, but I didn't get anything like that this time round.  The md5 is fine.

---

### Post by arochester on 2007-11-04
Did you user the oem install instead of the text install? Try username: oem and password: (either)oem (or) [BLANK]

---

### Post by Big_Croc7 on 2007-11-04
No, just the standard text install (first option I think).  Will reboot and try the combination anyway though.

---

### Post by sisco311 on 2007-11-04
select the Recovery Mode from the grub menu.
in Recovery Mode you are automatically logged in as root. 
you can add an admin user with tis commands:
```
adduser username
adduser username admin
```
reboot and login

---

### Post by Big_Croc7 on 2007-11-04
Thanks, that's great!  For some reason though it didn't add me to the sudoers file... had to do that manually.  Strange that it didn't ask to set up a user the first time round.

disturbing sig by the way!

---

