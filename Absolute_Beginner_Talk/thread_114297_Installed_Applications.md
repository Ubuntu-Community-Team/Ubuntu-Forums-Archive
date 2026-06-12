---
title: "Installed Applications"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by biguns on 2006-01-08
Can someone point me in the direction of getting a complete list of all the applications that are installed?

I have searched and just can't find the answer.

---

### Post by lha on 2006-01-08
```
dpkg-query -l
``` lists all packages you have installed.

---

### Post by jon_z on 2006-01-08
also try:
$ sudo killall -9 kicker
$ kicker

kills and then restarts the KDE or GDE menubar. incase the install didnt put the shortcut in there.

---

### Post by biguns on 2006-01-08
Perfect!

Thanks.

---

### Post by jon_z on 2006-01-08
glad to help

---

### Post by Delkster on 2006-01-08
You could also use Synaptic and select 'Status' as the type of filtering and 'Installed' as the filter. That would give you a graphical list of installed packages. Of course that doesn't list only applications but also all kinds of libraries and other such things not obvious to all normal users.

---

### Post by biguns on 2006-01-08
Seriously folks, this has to be the friendliest and most helpful forum known to mankind...hopefully I will become good at this stuff so I can one day help and inspire a newbie myself.

Thanks everyone!

---

