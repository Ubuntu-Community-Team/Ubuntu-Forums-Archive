---
title: "invisible file"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by sabitha on 2005-11-14
how to make/hidden my file/folder to everyone

---

### Post by adwait on 2005-11-14
I don' know about making a file invisible.......but you can try setting the permissions of the directory such that nobody but you is able to read it. So nobody can change into that directory and hence can't see the files. To do this:
```
chmod 700 <dirname>
```

---

### Post by jasay on 2005-11-14
You can make a file/folder hidden by putting a "." in front of the file name. 
```
mv filename .filename
```
Then change the permissions as outlined above.

---

### Post by Kvark on 2005-11-14
But hidden files can still be seen by all users if they tell the file browser, search tool, open/save dialog or anything else to show hidden files. So if you want to make sure they can't peak in it then use permissions instead.

---

