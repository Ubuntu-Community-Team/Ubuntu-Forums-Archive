---
title: "Lost Desktop Permission"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by GearedForWar on 2007-11-10
For some reason I lost my permission to anything on my desktop and I can't delete, move, paste anything on the desktop.  It says that owner is root on the properties.  How do I get my permission back to my user account?

---

### Post by amaroKer on 2007-11-10
Open a terminal window
Do:
```
ls -l /home/*username*
```

set the permissions and owner the same for desktop as the other folders that you can use correctly.

see signature link for permission and ownership help

---

### Post by init1 on 2007-11-10
> **GearedForWar said:**
> For some reason I lost my permission to anything on my desktop and I can't delete, move, paste anything on the desktop.  It says that owner is root on the properties.  How do I get my permission back to my user account?
The easiest way to change the file permissions is 
```

chmod 777 ~/Desktop/*

```
Type this into the terminal. 
There may be a better way to do this, but this should work.

---

### Post by amaroKer on 2007-11-10
post output from terminal command ```
ls-l /home/*username*
```

---

### Post by Harpoon on 2007-11-10
A preferable way is to regain ownership:

sudo chown -R your-username:your-username ~/home/your-username

Preferable in that some config files **may** require that the user be the owner of the file and writable **only**by the owner (eg, .dmrc)

---

### Post by GearedForWar on 2007-11-10
amaroKer your link in your sig fixed it Thanks a whole lot!!!!

---

### Post by amaroKer on 2007-11-15
My pleasure.

---

