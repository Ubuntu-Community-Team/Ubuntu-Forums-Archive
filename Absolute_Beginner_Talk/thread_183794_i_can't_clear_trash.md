---
title: "i can't clear trash"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-28
i have trashed some documents and tried to remove them from trash,it says u don't have permission to do this.
plz tell me how to do this .

---

### Post by Perfect Storm on 2006-05-28
```
 cd .Trash
sudo rm -rf XXXXXXX

```

---

### Post by barbarian on 2006-05-28
hi,
I normally fire up konqueror, then go to folder 'trash', then remove files over there..

---

### Post by u04f061 on 2006-05-28
what is the command for
fire up konqueror

---

### Post by skippy81 on 2006-05-28
konquerer is a KDE thing.  If your using gnome then you have nautilus as your file browser.  

IF you do > gksudo nautilus from a terminal you will be able to manipulate files graphically with admin rights.

---

### Post by manicka on 2006-05-28
[QUOTE=u04f061]i have trashed some documents and tried to remove them from trash,it says u don't have permission to do this.
plz tell me how to do this .[/QUOTE]

how did you try to remove them?

---

### Post by barbarian on 2006-05-29
> what is the command for
fire up konqueror

alt-f2>konqueror

with root privileges: alt-f2>kdesu konqueror

---

