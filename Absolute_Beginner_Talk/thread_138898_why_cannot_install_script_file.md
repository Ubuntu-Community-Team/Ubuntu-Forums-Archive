---
title: "why cannot install script file"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-02
The file was untared and the mixmaster folder has a lock attached to it:cool: :cool: :cool: 


dodger@lex~$ cd /mixmaster-3.0b2
bdodger@lex:/mixmaster-3.0b2$ sudo ./Install
sudo: ./Install: command not found
dodger@lex:/mixmaster-3.0b2$ ./Install
bash: ./Install: Permission denied
dodger1@lex:/mixmaster-3.0b2$

---

### Post by Sandlst on 2006-03-02
sudo ./ doesnt work: if you ever have to do this ```
sudo sh (file)
``` should work fine.  Post back if you have any problems.

---

