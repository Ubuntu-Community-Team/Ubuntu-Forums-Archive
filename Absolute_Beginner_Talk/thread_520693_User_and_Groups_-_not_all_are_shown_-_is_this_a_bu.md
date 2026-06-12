---
title: "User and Groups - not all are shown - is this a bug?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-08
mtink for example says to add your user to the group LP but this does not show in the list.

I tried gconf-editor and checked show all, but this does solve the problem.

---

### Post by reckless2k2 on 2007-08-08
no it's not a bug but there is an option in the users and groups menu to show all.

---

### Post by philinux on 2007-08-08
Sorry had a look no option to show all. Gconf-editor has a tick box to show all but that don't work either.

---

### Post by philinux on 2007-08-08
Seems that this is a bug with the GUI in that there was a check box in the previous incarnation to show all users and groups.

---

### Post by philinux on 2007-08-09
one bump, it's later now maybe someones awake, :lolflag:

---

### Post by schorsch on 2007-08-09
I do not see the group "lp" in the GUI, too. So, if you REALLY have to add the user to the group "lp" (not "lpadmin"? Just guessing as I do not know what you really want to do ....), please try:

```
gksu gedit /etc/group
```

and add the user to the group with the GID 7.  A membership in group "lpadmin" should be sufficient, but as mentioned before I do not know what you want to do ....

---

