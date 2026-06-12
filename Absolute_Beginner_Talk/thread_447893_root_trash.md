---
title: "root trash?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by norton1 on 2007-05-18
hi - i have some files that i just moved to trash as root - these dont show up in my normal trash can so is there a root trash can that needs emptying to delete these files permenately?

and if so - how do i get there?

thanks

---

### Post by chamberlain2006 on 2007-05-18
The trash for the root user is /root/.Trash.  To clear these files, do this command:
```
sudo rm -rf /root/.Trash/*
```

---

### Post by Najand on 2007-05-18
Yes.... Root has its own home and the trash folder is ".Trash" under the user home.
Root's home is /root... So if you want to remove them, you should look at /root/.Trash
ou can remove them using terminal:
```

sudo rm -rv /root/.Trash

```

---

### Post by norton1 on 2007-05-18
thanks!

---

### Post by aysiu on 2007-05-18
I'd **highly** recommend against ever typing or pasting this command into the terminal: ```
sudo rm -rf
``` Try ```
gksudo nautilus
``` enable the option to have a delete command that bypasses the trash, navigate to /root/.Trash (.Trash is a hidden file, so press Control-H to see it), then delete whatever's there.

A lot more steps, but a lot safer.

---

