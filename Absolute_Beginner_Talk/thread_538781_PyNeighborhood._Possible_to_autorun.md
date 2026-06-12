---
title: "PyNeighborhood. Possible to autorun?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-30
Following this guide: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)
I just installed PyNeighborhood in Xubuntu and is running really fine.
But now, I have two important things I must do

It is possible to autorun PyNeighborhood on each login? Does it always need to use sudo mode?

I need to create a "non privileged" user for a school and this user should be able to browse to the folder network mounted by PyNeighborhood and it should it be mounted automatically...
Do I'm asking too much maybe?

Help!!

---

### Post by Hobo Joe on 2007-08-30
I'm not familiar with this program, but for any other program you add a session for it under System > Preferences > Session.

Use the command like this: 
```

gksu <command for running program>

```

---

### Post by schorsch on 2007-08-30
I'd guess it is easier to mount the shares at boot time permanently via /etc/fstab.
Otherwise if you want to go your way AND sudo is necessary to use PyNeighborhood (which I do not know) you have to edit /etc/sudoers and give those "unpriviledged user" the permission to start PyNeighborhood.

---

### Post by Ubuntized! on 2007-08-30
Exactly, but that requires to input the admin password though! I heard u have to give the command
```
sudo visudo
```
and edit the file adding to it the application or the command u don't want it to require the password for!

---

