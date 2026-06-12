---
title: "Uninstalling .deb?`"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by SurR3AL on 2007-03-14
i downloaded and installed the transgaming cedega thing from a .deb, but i dint realise it wasnt free :(  so now i want to uninstall it. it doesnt appear in add/remove programs. what should i do? 
thanks!

---

### Post by Kateikyoushi on 2007-03-14
You can remove it by typing this to the terminal.
```
sudo dpkg -r package.name
```

---

### Post by undertakingyou on 2007-03-14
One quick note that kept me baffled about dpkg for a long time.  You can't say "package.deb"  You have to give the specific package name. (i.e. cedega, firefox etc.)

---

### Post by silhouette on 2007-03-14
Can't you also just say "apt-get remove PACKAGE"?

---

### Post by mcduck on 2007-03-14
You can also uninstall it with Synaptic package manager.

---

### Post by aijazbaig1 on 2007-03-14
One thing that comes to my mind in this is that one can have the debian menu installed so that it appears as a sub-menu in the applications menu.

Many a times programs which do not appear in the applications menu are found there. 

u can istall the debian menu using [[COLOR="Blue"]automatix[/COLOR]]("http://www.getautomatix.com"). Then u shud use the following command :
```
sudo update-menus 
```

This would hopefully populate the menus depending on if u have any of the programs under the corresponding categories intalled..

Hope then u have ur debian menu configured and every time u make an install through any of the ways..be it thru add/remove, terminal(apt-get or aptitude), synaptic or manually then they shud appear in that menu...

I hope that would help..

Aijaz.

---

