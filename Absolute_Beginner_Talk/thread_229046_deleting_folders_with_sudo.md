---
title: "deleting folders with sudo"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-08-03
i recently copied a read only folder from my windows harddrive and when i try to delete it off the desktop it says that i don't have root permissions and therefore cannot delete it. is there a command i can use to delete it using the terminal?

Thanks much,
cptjaben

---

### Post by lord_zerg on 2006-08-03
try
```
sudo rm -R path
```
where path is the path to the folder.
i would recommend that u double check before erasing anything this way though.

---

### Post by cstudent on 2006-08-03
Since you say you put in on your desktop, I make the assumption for the path.

From the terminal
```

sudo rm -rf ~/Desktop/thefoldername

```

Hope this helps



cstudent

---

### Post by cptjaben on 2006-08-04
Thanks for the help guys

---

### Post by 3rdalbum on 2006-08-04
If you wanted to do it graphically, you could hit Alt-F2 and type "gksudo nautilus --browser".

---

