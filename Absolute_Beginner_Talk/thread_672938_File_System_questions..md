---
title: "File System questions."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-20
My first question is how do I get permisson to do everything? Like copy a file to /usr/share/amsn/skins

My second is how to view hidden files in the home folder.

Thanks

---

### Post by frup on 2008-01-20
sudo command or gksudo for GUI programs from terminal gives you admin permissions

CTRL+H in nautilus will allow you to see hidden files/folders or ls-al in terminal (you only need -a but I prefer the l as well it's clearer in a way)

---

### Post by Ludford on 2008-01-20
Cheers, My second question is there away to remove the need to have permissions all together?

Like away to get rid of asking for a password when doing certain things. Although I relise it's not reconmended I'm the only one that uses this partition, and the computer is safe in my room.

---

### Post by mali2297 on 2008-01-20
> **Ludford said:**
> My first question is how do I get permisson to do everything? Like copy a file to /usr/share/amsn/skins

My second is how to view hidden files in the home folder.

Thanks

If you are willing to use the terminal, add **sudo** in front of cp to copy files to directories that are own by root, **ls -A** will show hidden files (along with others).

If you want to use the default file manager Nautilus, press alt+f2 and type:
```

gksudo nautilus

```
Look through the menus, there should be an option to view hidden files.

---

### Post by frup on 2008-01-20
> **Ludford said:**
> Cheers, My second question is there away to remove the need to have permissions all together?

Like away to get rid of asking for a password when doing certain things. Although I relise it's not reconmended I'm the only one that uses this partition, and the computer is safe in my room.

Permissions are needed. Fullstop.

You could log in as root, which is disabled and a huge security risk to be running all the time.
You can make the login window at the beginning go away easily and that can be nice if you don't feel like logging in when you turn on your computer... Just don't loose it.
You can increase the time between sudo/admin apps asking you for your password. Right now it is 15 minutes I think.  Do you not think warning you that you are making a big change is a good idea though? You may break something if you run as root. I did when I first started using linux... more than once.

---

### Post by Ludford on 2008-01-20
I guess I'll keep it so I don't blow anything up.

---

### Post by frup on 2008-01-20
Yeah the passwords can be seen as a way of saying "make sure you understand what you are doing" :D

---

### Post by zero-9376 on 2008-01-20
the other thing is that if you are running an application as root and there is some sort of exploit in that application the application or an attacker has full access to your system and can do nasty things like make you a source of spam

---

