---
title: "[SOLVED] permissions"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Damanther on 2007-08-15
I feell like  a real noob asking this question, but I cannot for the life of me remember how to change it so that when a user creates a file, certain permissions are set.

Specifically, I would like it so that this users creates files with the group read and write permisisons set to something like 774, rwxrwxr--, or something to the like of that.

---

### Post by bodhi.zazen on 2007-08-15
You set it with a umask value.

[http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

