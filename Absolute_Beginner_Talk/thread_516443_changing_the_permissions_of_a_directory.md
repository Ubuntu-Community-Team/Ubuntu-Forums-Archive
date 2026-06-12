---
title: "changing the permissions of a directory"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-08-03
I want to   change the permission of /var/www directory  as a normal user so that i can write file there without the need of being superuser. what should I do?

---

### Post by panther_sn on 2007-08-03
you can do 
```
 sudo chmod 777 /var/www/

```  But that means anybody has access to that folder to read/write/and execute can be dangerous if that directory has web access
there may be a better way, but in my limited (very limited) experience that is the only way, there probably other ways

---

### Post by atomkarinca on 2007-08-03
```
sudo gedit /etc/apache2/sites-available/default
```

and then you can comment out "Deny from all". i think this way it's healthier.

---

### Post by jamil_1 on 2007-08-03
what does 777 stand for

---

### Post by panther_sn on 2007-08-03
read write execute, I think, though I could be wrong lol

---

