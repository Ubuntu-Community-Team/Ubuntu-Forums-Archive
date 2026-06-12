---
title: "aria help"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-01-15
there is an option that says execute command after download.. what would be a command for shutting down the computer?

---

### Post by yabbadabbadont on 2008-01-15
```
sudo shutdown -h now
```

It will prompt you for your password unless you have modified the /etc/sudoers file (using "sudo visudo") so that the shutdown command can be run without password.

Edit: It is left as an exercise for the student to read the sudoers man page in order to learn the details.  ;)

---

### Post by patchido on 2008-01-27
how do i have to make this work?? so it wont ask me for password??

---

