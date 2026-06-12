---
title: "Listing all users from command line"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by viniosity on 2006-08-25
Is there a way to show a list of all users on the command line?  

```

users

```

only shows the users that are currently logged in.  I'm looking for a list of all users regardless of whether thy are logged in or not. If there is a user in my system I want to know what groups it belongs to as well.  

Thanks..

---

### Post by neilp85 on 2006-08-25
If all the users home directories are at the same mountpoint you could do something like 
```
ls /home
```
Not sure of a command to list all the systems users and their groups though.

---

### Post by viniosity on 2006-08-25
I ended up just doing

```

cat /etc/group

```

and going through the list.  Not perfect but I got the info I was looking for.

---

### Post by neilp85 on 2006-08-25
Your post got me curious so I looked around somemore and each user along with some other info about them is listed in the /etc/passwd file.

---

### Post by uberg on 2006-08-25
Simply type in who from the command line.

---

### Post by prkfriryce on 2006-08-25
cat /etc/passwd | awk -F: '{print $1}'

:-#

---

### Post by viniosity on 2006-08-25
> **prkfriryce said:**
> cat /etc/passwd | awk -F: '{print $1}'

:-#


Yup, that does it.  Thanks

---

### Post by prkfriryce on 2006-08-25
> **viniosity said:**
> Yup, that does it.  Thanks

np :-D

---

### Post by bswilson on 2006-08-25
Better yet, get the descriptive user name.

```
cat /etc/passwd | awk -F: '{print $1,","$5}
```

---

