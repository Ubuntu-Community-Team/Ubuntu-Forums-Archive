---
title: "Can't login as root"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by geckoprogrammer on 2007-05-19
Thanks for reading this message...

I am a Linux Newbie and want to install some programs and edit some root-created files. :confused:
However, I have failed on recent attempts to to log in as root, and using the "su" command in Terminal. Would anyone know how to do this?

Thank you. :KS



:lolflag: Go Ubuntu!

---

### Post by lazyart on 2007-05-19
sudo *command*

When you installed Ubuntu the root pass is set to the same as the first user you created.

---

### Post by tchoklat on 2007-05-19
Ubuntu uises sudo.
 
Try sudo aptitude update or sudo whatever
you willl be asked for your root password then

---

### Post by sessine on 2007-05-19
You don't need to log in as root.  The first user created is part of the admin group.  Just use the 'sudo' command, e.g.
```
siudo cp /some/file /some/location
```

You will be prompted for your password, just use your normal login one.

---

### Post by Najand on 2007-05-19
Check: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
> **lazyart said:**
> sudo *command*

When you installed Ubuntu the root pass is set to the same as the first user you created.

Sorry, lazyart! Root Password is not as same as your first user password. The root password has been disabled in ubuntu and the first user is a member of "adm"  group which its members are allowed to "sudo". That is a big difference between Root and a sudoer user.

---

### Post by elints on 2007-05-19
Check here

[http://ubuntuforums.org/showthread.php?t=397003](http://ubuntuforums.org/showthread.php?t=397003)

---

