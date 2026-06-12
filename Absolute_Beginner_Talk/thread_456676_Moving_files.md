---
title: "Moving files"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Scummy007 on 2007-05-27
I need to move a .tar.gz from my desktop to /opt
can someone give me the bash commands for that because i need it done today and it appears that i cant just login as root to move them through the gui.

cheers

Scummy

---

### Post by darklemming54 on 2007-05-27
the command "mv" will move files or "cp" will copy them


```

sudo mv /home/[username]/Desktop /opt

```

---

### Post by Scummy007 on 2007-05-27
awesome, cheers mate

Scummy

---

### Post by bikeboy on 2007-05-27
As a side note, while the command line is quicker and easier for something like this, it is possible to do root filesystem operations using a gui.

The built in way would be to open a terminal and type the following command.
```
gksudo nautilus
```

gksudo is for getting root privalages for a gui program and it will ask for your user password, nautilus is the gnome file-manager. Remember to close nautilus as soon as you've the need for it has ended.

---

