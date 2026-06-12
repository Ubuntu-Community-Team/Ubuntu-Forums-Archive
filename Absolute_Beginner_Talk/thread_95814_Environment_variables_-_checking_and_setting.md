---
title: "Environment variables - checking and setting"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-27
People,

   I want to install JDK in my system, but I would like to know in which folder I must install in order to make it visible systemwide.  I mean a folder included in the PATH environment variable.
   I would like to know the commands/softwares necessary to manipulate environment variables, as the Cookbook does not include information about them.

---

### Post by cwaldbieser on 2005-11-27
[QUOTE=paulozzzz]People,

   I want to install JDK in my system, but I would like to know in which folder I must install in order to make it visible systemwide.  I mean a folder included in the PATH environment variable.
   I would like to know the commands/softwares necessary to manipulate environment variables, as the Cookbook does not include information about them.[/QUOTE]
/etc/environment can be used to set system-wide environemnt variables.
Your ~/.bashrc file is run every time you start a bash shell, so you can  add stuff to your PATH in there to make it available to just that user.

Normally, the system wide binaries are installed in a folder like /usr/bin or /usr/local/bin that are already included in the PATH, though.

---

### Post by kzutter on 2005-11-27
To find out what the current values are, open a terminal window and issue the 'set' command:
```
ken@u2:~$ set
```

Take a look at the PATH variable.
Some variables will  be different for different users.

-Ken

---

### Post by paulozzzz on 2005-11-27
Thanks, people.  With the information I managed to modify the execution script to be in accordance with my system path.:D

---

