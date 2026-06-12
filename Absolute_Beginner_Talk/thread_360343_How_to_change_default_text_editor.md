---
title: "How to change default text editor?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by mahy on 2007-02-13
Hi y'all,

whenever i run crontab -e, it opens in nano. So i have to quit it and run command "export VISUAL=vim", to have it started in Vim (i hate nano). However, after logout, nano is the deafult editor again. Why? How do i make this change permanent? TIA

---

### Post by highneko on 2007-02-13
After reading the man page I did this:
```
user@ubuntu:~$ file /usr/bin/editor
/usr/bin/editor: symbolic link to `/etc/alternatives/editor'
user@ubuntu:~$ file /etc/alternatives/editor
/etc/alternatives/editor: symbolic link to `/bin/nano'
```Does that help? Good luck, have fun.

---

### Post by mahy on 2007-02-13
Thanks, it helped! :KS

---

