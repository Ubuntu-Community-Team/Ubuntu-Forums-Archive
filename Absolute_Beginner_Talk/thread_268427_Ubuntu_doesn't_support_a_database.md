---
title: "Ubuntu doesn't support a database"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by pumpapa on 2006-09-30
Neither mysql nor postgresql install due to dependency failures. For instance, mysql requires libreadline4, but my system has 5 and most packages depend on it. 

From my perspective Ubuntu doesn't support a database.

---

### Post by LookTJ on 2006-09-30
yes it does, look in Packages manager, use lampp to save you the trouble

---

### Post by pumpapa on 2006-09-30
The problem is largely the Synaptic Pacakge Manager which adheres to strict (version based) dependencies. 

Installing mysql directly from/following [http://dev.mysql.com/doc/refman/5.0/en/installing-source.html](http://dev.mysql.com/doc/refman/5.0/en/installing-source.html) seems to work fine.

---

### Post by pumpapa on 2006-09-30
> **Taylor said:**
> yes it does, look in Packages manager, use lampp to save you the trouble

Point taken. Like I mentioned, Synaptics stumbled over dependencies which turn out to inessential. But the reason I switched from Suse to Ubuntu was precisely to avoid spending a lot of time installing software.

In any event, I've posted my workaround.

Cheers

---

