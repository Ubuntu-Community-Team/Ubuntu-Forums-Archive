---
title: "how do i check my LAMP version?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by spcoex on 2007-08-28
Im a newbie....and just finished installing Ubuntu Server 7.0.4
Now, what commands do i use to check which version of mySQL, php, and Apache I have installed? its a clean install and I've done no upgrading. 

Thanks

---

### Post by schorsch on 2007-08-28
```
dpkg -l|grep -i mysql
dpkg -l|grep -i php
dpkg -l|grep -i apache
```

---

