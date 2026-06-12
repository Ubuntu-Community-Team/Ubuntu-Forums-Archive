---
title: "username and password help"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by elton1981 on 2007-02-22
Have just installed Ubuntu 6.10. I cant log on to the system. It doesnt' recognise my username/password. Is there a way I can re-set these?

---

### Post by nickoli_02 on 2007-02-22
Try booting into recovery mode, then when you come to the tty type "startx". From there go to System -> Administration -> Users and Groups. You should be able to reset your password there.

---

### Post by Extremely Annoyed on 2007-02-22
ok, I'm having the same problem, and I tried what you said...I get the following message when I click on Users and Groups:

**The configuration could not be loaded**

You are not allowed to access the system configuration.

---

### Post by mcduck on 2007-02-22
Try this other way to do it:

1. boot into recovery mode
2. run 'ls /home'. This will list all users of the machine, as they all have their home directories inside /home. Now you know the username.
3. run 'passwd <username>, replace <username> with your username of course. Now you can set a new password.
4. 'reboot' will reboot the machine. You should now be able to log in with your username and the password you just set.

---

### Post by nickoli_02 on 2007-02-22
ha, yea, my method won't work... just realized that

---

