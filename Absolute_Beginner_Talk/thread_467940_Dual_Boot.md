---
title: "Dual Boot"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by cat143 on 2007-06-08
Thanks For the help with the dual boot I got it up and running does anyone know how do I turn off the logon and password so it will go to the desk top with out it

---

### Post by dstew on 2007-06-08
The user login with a password is the main way that Linux is protected from viruses and other malicious software. The reason Windows has so much trouble with malware is because whoever boots the computer is essentially a root user, with full administrative privleges that don't expire. In Linux, you log in as a user, without administrative privleges. If you need administrative privleges, the sudo command gives them to you for a little while, and then automatically takes those privleges away after about 5 minutes. That reduces the chance that any virus will be able to take over your computer. The login is your friend, don't try to go around it.

---

### Post by lamalex on 2007-06-08
for automatic login go to system>administration>Login WIndow>Security>Enable Automatic login and select your user.

---

