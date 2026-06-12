---
title: "Very basic Trash"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by j002 on 2007-04-10
Okay, how do I empty the trash ?

I know there was some command to make you the administrator (gksudo ...something), but I can't find it on this site anywhere.

---

### Post by heimo on 2007-04-10
I assume you're using Gnome (default Ubuntu, not Kubuntu or Xubuntu) In nautilus (file browser), select File->Empty Trash. Or right-click trashcan symbol (lower left corner) and select Empty Trash.

---

### Post by kfrance on 2007-04-10
I'm not sure exactly what you mean.  If it is what i think you are asking you just open up the trash folder by clicking on the icon on your task bar, selecting all the files and pushing delete.  You can also go to ~/.Trash on the command line and type rm -rf *.  Make sure there isn't anything you want because it's gone after this.

---

### Post by j002 on 2007-04-10
I can't do it graphically it says "Permission not granted".

I'll try from the CLI.

---

### Post by heimo on 2007-04-10
You could try to fix permissions (if .Trash is owned someone else than you) with:
```
sudo chown -R $USER:$USER ~/.Trash/
```

---

