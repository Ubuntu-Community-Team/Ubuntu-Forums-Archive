---
title: "Trying to upgrade -- Help wanted"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by jamesrose on 2006-10-26
Says cannot open display!

PRessed CTRL + ALT + F1 , then entered gksu "sh /cdrom/cdromupgrade" 

also tryed gksudo "sh /cdrom/cdromupgrade"

---

### Post by ReaderRat on 2006-10-26
Upgrade to Edgy
         [**Edgy Upgrade**](http://www.ubuntuforums.org/showthread.php?t=269729)

---

### Post by jamesrose on 2006-10-26
> **ReaderRat said:**
> Upgrade to Edgy
         [**Edgy Upgrade**](http://www.ubuntuforums.org/showthread.php?t=269729)

when going sudo apt-get update i get this :

```
root@admin-Desktop:/home/admin# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
root@admin-Desktop:/home/admin#

```

---

### Post by chuckyp on 2006-10-26
That would mean an instance of update-manager or apt-get or synaptic is already running.  You need to kill that first then try again.  Also make sure you are using sudo first.

---

### Post by jamesrose on 2006-10-26
> **chuckyp said:**
> That would mean an instance of update-manager or apt-get or synaptic is already running.  You need to kill that first then try again.  Also make sure you are using sudo first.

How do i kill a tty?

---

### Post by chuckyp on 2006-10-26
Well you can type exit in the tty will kill it.  Also you should gksu "update-manager -c" is the prefered way to upgrade if you have X running.

---

### Post by jamesrose on 2006-10-26
> **chuckyp said:**
> Well you can type exit in the tty will kill it.  Also you should gksu "update-manager -c" is the prefered way to upgrade if you have X running.


Its upgrading!!!

YES!

I would hug you at this moment in time :D 

Cheers!

---

