---
title: "Changing a folder's owner?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by JEBB on 2007-06-18
I tried to install the browser SeaMonkey.  The instructions had me create a folder for the program.  The folder I created has root as owner.  How can I change the ownership to me?  Thanks.

---

### Post by skymera on 2007-06-18
how about installing as Root.

```
sudo -s
```

---

### Post by marc321 on 2007-06-18
To change ownership of a folder, use 
```
sudo chown username:users folder
```

To change ownership of a folder and all of it's contents and subdirectories, use 
```
sudo chown -R username:users folder
```

Replace **username** with your username, and leave **users** as is (it is the name of the "users" group).

---

