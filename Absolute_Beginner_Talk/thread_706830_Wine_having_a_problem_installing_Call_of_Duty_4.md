---
title: "Wine: having a problem installing Call of Duty 4"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-02-24
the problem with COD 4 is that it says it doesn't support Windows NT, 2000, how do i get around this

---

### Post by mivo on 2008-02-24
A good starting point is the Wine Application Database. [See here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934").

---

### Post by gecko113 on 2008-02-25
this mite be a stupid question but is there a way to update Wine version through the terminal.

---

### Post by justin whitaker on 2008-02-25
> **gecko113 said:**
> this mite be a stupid question but is there a way to update Wine version through the terminal.

Type winecfg in a terminal, and a nice GUI should pop up. The first tab will be the Default settings, and you want to switch that from 2000 to XP, and hit apply.

---

### Post by mivo on 2008-02-25
> **gecko113 said:**
> this mite be a stupid question but is there a way to update Wine version through the terminal.

It's not a stupid question at all. You can update Wine by adding the WineHQ repository to your sources list and then updating the system. Using the terminal, follow these steps ...

This adds the WineHQ key to your trusted keys:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

The next command adds the new software source to your sources file:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

Note that this is for Gutsy / 7.10. For other Ubuntu versions, see [here]("http://www.winehq.org/site/download-deb").

Finally, update your system:

```
sudo apt-get update
```

Hope this helps!

---

### Post by gecko113 on 2008-02-25
I get an error with GPG heres a picture of the terminal:

---

### Post by gecko113 on 2008-02-25
kk well it updated but now i looked under applications n its not there what mite have happened to it

---

