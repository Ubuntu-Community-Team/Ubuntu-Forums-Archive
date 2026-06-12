---
title: "permission problem =("
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by DillPill on 2006-07-01
um i try to delete, make folders, anything with the desktop and i get this error:

You do not have permissions to write to the destination.

how do i fix this?

---

### Post by joshrobinson on 2006-07-01
[QUOTE=DillPill]um i try to delete, make folders, anything with the desktop and i get this error:

You do not have permissions to write to the destination.

how do i fix this?[/QUOTE]

you dont want to fix it.. its there for security reasons.. you can delete files and or folders with the command line or use a root enabled file browser

type this code in a terminal to browse your computer with all permissions.. just dont delete anything important and be carefull

```
gksudo nautilus
```

edit: this is assuming you are using Ubuntu with gnome.. if you use kubuntu/kde follow aysiu's link below

---

### Post by aysiu on 2006-07-01
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by DillPill on 2006-07-01
well, about 5 mins ago it was working perfectly and now i cant do anything.....

---

### Post by DillPill on 2006-07-01
btw thanks for quick response

---

### Post by aysiu on 2006-07-01
Are you saying you can't even write to /home/dillpill?

---

### Post by DillPill on 2006-07-01
i can write to home/dillpill but not home/dillpill/desktop

which i could do a few hours ago

---

### Post by aysiu on 2006-07-01
How about this? ```
sudo chown -R dillpill:dillpill ~/Desktop
```

---

### Post by DillPill on 2006-07-01
ahh thats it! thanks alot!

---

