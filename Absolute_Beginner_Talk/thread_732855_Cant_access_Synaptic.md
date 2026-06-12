---
title: "Cant access Synaptic"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Mesenja on 2008-03-23
[SIZE="3"]I am unable to get into my Synaptic Package Manager. The following mesage appears:

An unresolved problem occured while initializing the package information.

Please report this bug against the 'update manager' package and include the following error message.

'E:Malformed line 55 in source list etc/apt/sources.list(dist parse),E;'The list of sources could not be read.'[/SIZE]

---

### Post by jken146 on 2008-03-23
Please post the contents of /etc/apt/sources.list

---

### Post by wormser on 2008-03-23
Here is the command to view the file.

```
sudo gedit /etc/apt/sources.list
```

The error is telling you that something is wrong with line 55.  If you post the file we can help you.

---

### Post by Mesenja on 2008-03-23
[FONT="Franklin Gothic Medium"]I followed the directory tree until I found the folder  sources.list and then delted my last entry. I can now open up Synaptic[/FONT]

---

### Post by Mesenja on 2008-04-03
:)

---

