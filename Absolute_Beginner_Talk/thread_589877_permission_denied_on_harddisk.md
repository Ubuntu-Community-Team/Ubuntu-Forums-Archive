---
title: "permission denied on harddisk"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by calimerox on 2007-10-24
Hello , I ´m new to linux so I guess this is an easy question:

I formatted a partition to ext3 on an external harddrive, now , when i want to copy data on it it tells me permission denied!! and tells me it´s root and i have no right to do it. 
if i put something like sudo mkdir it works on the drive, but to use a regular filebrowser, how do i get to work it? thanks for help!!:)

---

### Post by Ek0nomik on 2007-10-24
> **calimerox said:**
> Hello , I ´m new to linux so I guess this is an easy question:

I formatted a partition to ext3 on an external harddrive, now , when i want to copy data on it it tells me permission denied!! and tells me it´s root and i have no right to do it. 
if i put something like sudo mkdir it works on the drive, but to use a regular filebrowser, how do i get to work it? thanks for help!!:)

Give yourself permission to use the hard drive.

Find out where on /media... your hard drive is mounted.

Then:

```
sudo chown YourUserName:YourUserName /media/location
```

---

### Post by Iowan on 2007-10-24
You can **sudo chown** to change the ownership to your username... but the specifics escape me at the moment.

Outtyped again - better info anyway...

---

### Post by oldos2er on 2007-10-24
If you're using Gnome, in a terminal type 'gksudo nautilus' and your file browser will open as root. Or, under the Applications menu, System Tools, choose 'Root Terminal,' then type in 'nautilus.'

---

### Post by P4man on 2007-10-24
another easy trick is opening a console and typing "sudo nautilus". That will launch the file browser with root permissions. The slightly differently presented folder structure may confuse you though.

---

### Post by calimerox on 2007-10-24
its magic :)
thanks a lot!

---

### Post by Ek0nomik on 2007-10-25
> **calimerox said:**
> its magic :)
thanks a lot!

Mark the thread as solved, please.  :)

---

