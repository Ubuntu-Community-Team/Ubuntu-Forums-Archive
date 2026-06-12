---
title: "An error occured???"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Liamkerrigan on 2007-09-17
Hello there,

W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)

is the error message i get whilst trying to get Ubuntu updates.. help please

Cheers

---

### Post by overdrank on 2007-09-17
> **Liamkerrigan said:**
> Hello there,

W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)

is the error message i get whilst trying to get Ubuntu updates.. help please

Cheers

Hi you can edit your sources list with this command 
```
gksudo gedit /etc/apt/sources.list
```
Remove the duplicate entry and save then update. Good luck!

---

