---
title: "Gutsy freezes during update"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by KILGETTY on 2007-11-26
Have just installed Gutsy to hard disc, it downloaded 88 updates and then started to install them but all I get is this error message :-

E; dpgk was interrupted, you must manually run 'dpkg --configure -a' to correct problem.
E:_cache->open()failed, please report.

I have typed this command into Terminal but all I get back is a load of statements I do not understand.
Has anyone else had this problem?
Can anyone help with my problem?
I am a Linux virgin so please be gentle with me.

---

### Post by reesy on 2007-11-26
Put this into the terminal and it should be back to normal

sudo dpkg --configure -a

---

### Post by KILGETTY on 2007-11-26
SORTED! Did as you suggested after finding out what "sudo" meant, all updates are now installed.
Thanks very much for your help.

---

