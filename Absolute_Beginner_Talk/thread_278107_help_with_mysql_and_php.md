---
title: "help with mysql and php"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by thebouzouker on 2006-10-15
after installing the lamp server it installed php 5 and mysql 5.how can install php 4 and myslq 4???and if i do it,will i have to install apache2 again?

---

### Post by thebouzouker on 2006-10-15
two days now i am searching for an answer!

---

### Post by dmizer on 2006-10-16
not sure exactly ... you might try:
```
sudo aptitude install php4
```

aptitude should (should) discover that you have a newer version of php installed and offer you a solution to remove the php5 and replace it with php4.  same for mysql.

i'm also not sure, but i think that php4 and php5 (as well as mysql) can live together on the same machine with no problems.  you just have to tell apache which one to use (no idea how to do that).

---

