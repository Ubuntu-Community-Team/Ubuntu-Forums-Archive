---
title: "admin rights for a single user"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by pentium on 2006-10-03
Even though I have owned ubuntu for over a week and have grown used to sudo and root terminal, I really don't want to use it forever.
I would like to find out how I can chang all rights the root (admin?) has so I can actually move files around my drive without needing root terminal or running qtparted without being told that I am not the admin and thus the program won't work for me.
Any help?

---

### Post by podunk on 2006-10-03
sudo su

I think you'll be sorry though. :-)

---

### Post by aysiu on 2006-10-03
Create launchers with *gksudo*.

For example, your launcher for QTParted should be ```
gksudo qtparted
``` or ```
kdesu qtparted
``` If you want to drag and drop things around, create a launcher for the command ```
gksudo nautilus
```

---

### Post by pentium on 2006-10-03
Thanks man!

---

### Post by comppsyco on 2006-10-03
If you really need to, use sudo su, then change the password with the passwd. As has been said, though, you'll be sorry.

---

