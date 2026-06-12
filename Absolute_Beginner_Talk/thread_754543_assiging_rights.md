---
title: "assiging rights"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by richardd2137 on 2008-04-13
hello, i;m trying to assign rights to a folder throguh the terminal, how would I do this?
Thanks

---

### Post by Oldsoldier2003 on 2008-04-13
> **richardd2137 said:**
> hello, i;m trying to assign rights to a folder throguh the terminal, how would I do this?
Thanks
to change ownership rights you use chown to change rights for groups use chmod. if you explain more what you are trying to accomplish we could help you out a little better,

---

### Post by Duckyspetrie on 2008-04-13
It would probably be easier to right-click the folder and edit permissions that way.

---

### Post by richardd2137 on 2008-04-13
u see i can't change the rights unless i logon as root, also i am running ubuntu on a compaq f750 us laptop and when u plug in head phones the deck speakers don't turn off. Any one know how 2 fix this?

---

### Post by richardd2137 on 2008-04-13
update 2 quesion, its a folder that im trying 2 get access to,`I it has a little pad lock in the top right hand corner in my home folder

---

### Post by wormser on 2008-04-13
Try to cd into the directory before it and then listing the permissions.  Post the results.

```
cd /path/to/folder
```
```
ls -lad foldername
```

---

### Post by Duckyspetrie on 2008-04-14
That happened to me also. If wormser's idea doesn't work, just right-click on the folder, go to properties, then permissions, and change it to read-write (this enables you to move the folder). Hope this helps.

---

