---
title: "link"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by cconk01 on 2006-06-08
Hello, linux newb here, but i have done really well so far i think... not hard to when Apache, Mysql and PHP are already installed...:)  but i am trying to install wordpress and it installed under the /usr/share/wordpress directory, dont i need to create a link to it from my /var/www directory so i can access it via a web browser? also what is the command to make a link to a directory, i cant remember:-k

---

### Post by Jagot on 2006-06-08
'Fraid I can't answert the first bit, but to link directory:

```
sudo ln -s 1st_directory 2nd_directory
```

---

