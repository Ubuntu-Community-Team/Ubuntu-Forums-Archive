---
title: "can't find the /www directory"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by strider* on 2008-01-23
i have already install apache2 in my ubuntu but it's funny that i cannot find the /www directory... please correct me if i'm wrong.. www directory is inside the var directory... but where is it? hoping for you help guys T_T

---

### Post by jeffus_il on 2008-01-23
try in a terminal ```
find /var -name www
```

---

### Post by strider* on 2008-01-23
i've already enter the command you told me.. but nothings shows up... is there something to do with my installation.. maybe my installation failed?..

---

### Post by NGSG on 2008-01-23
hi there,
check whether the (installed) apache server is running at least, by typing in a web browser:
[http://127.0.0.1](http://127.0.0.1)
then see whether the directory /var/www exists
hope this helps.

---

### Post by hyper_ch on 2008-01-23
```

cd /var/www

```

---

