---
title: "Help! sudo apt-get"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-01-30
Hi

Im stetting up evolution so i can use me hotmail account
im using a 'how to' i found in this forum but..............

when i open a teminal and type:
' sudo apt-get install inetutils-inetd'
I type the admin password and get:
'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'

any advice or help would be great.

Thanks,
               Nolander

---

### Post by bruenig on 2007-01-30
Do what it says
```
dpkg --configure -a
```

---

### Post by Nolander on 2007-01-30
now it spits out:
'dpkg: requested operation requires superuser privilege,

:confused:

---

### Post by 3rdalbum on 2007-01-30
sudo dpkg --configure -a

Any operations involving dpkg or apt-get require the use of "sudo".

---

