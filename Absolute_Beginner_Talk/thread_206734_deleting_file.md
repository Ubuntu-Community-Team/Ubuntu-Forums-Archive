---
title: "deleting file"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by treehopper29 on 2006-06-30
I accidentaly installed somthing in the package manager and i tryed removing it completly from there but the fils were still there. The files are in the root directory and if i try to delete them i get the message "you dont have premision" or somthing like that. How do I delete this file.

---

### Post by invalid on 2006-06-30
[QUOTE=treehopper29]I accidentaly installed somthing in the package manager and i tryed removing it completly from there but the fils were still there. The files are in the root directory and if i try to delete them i get the message "you dont have premision" or somthing like that. How do I delete this file.[/QUOTE]
You will need to do it with a superuser. Try using sudo in front of your command:
```
sudo rm filename
```
It will ask you for your password, security reasons.

---

### Post by joshrobinson on 2006-06-30
[QUOTE=invalid]You will need to do it with a superuser. Try using sudo in front of your command:
```
sudo rm filename
```
It will ask you for your password, security reasons.[/QUOTE]

that will work.. if you want to do it with a gui through nautilus you can type

```
gksudo nautilus
```

but make sure you know what your deleting, and dont get rid of anything the system depends on

---

