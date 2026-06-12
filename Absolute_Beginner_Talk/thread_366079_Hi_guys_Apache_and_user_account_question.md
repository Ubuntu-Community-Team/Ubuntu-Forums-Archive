---
title: "Hi guys Apache and user account question"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jm240` on 2007-02-20
How can I set my machine up so that when I set up a new user a WWW internet folder gets created in the users folder and they are then able to use that folder as a webserver?

The url would obviously be [http://addres-of-mymachine/~username/](http://addres-of-mymachine/~username/)


Apache is set up and running.

Thanks guys

PS:- anyone know a good site which teaches the filesystem without boring you to much? (but more detail than the kubuntu filesystem page)

---

### Post by Bachstelze on 2007-02-20
To have such folders, each user must have a dir called public_html - by default, this can be changed - in his or her home dir. I don't know if there's a way to create it automatically.

---

### Post by jm240` on 2007-02-20
So public_html/ in their home folder will give them access. Is there a specific apache config file that you know that I can configure if say I wanted to change the folder name?

Thanks again so far. I guess I could write a BASH script to automatically create users and add the folder for me.

---

### Post by Bachstelze on 2007-02-20
```
sudo nano /etc/apache2/apache2.conf
```

Use Ctrl+W to find public_html and change it to whatever you want.

---

### Post by jm240` on 2007-02-20
> **HymnToLife said:**
> ```
sudo nano /etc/apache2/apache2.conf
```

Use Ctrl+W to find public_html and change it to whatever you want.


many thanks!

---

