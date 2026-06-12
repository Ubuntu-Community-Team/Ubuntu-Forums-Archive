---
title: "Removing installed applications"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2007-01-01
How to remove installed applications like Ekiga and Evolution? I try to remove it using synaptic and I selected "Complete Uninstallation", but it will also remove ubuntu-desktop.

---

### Post by meng on 2007-01-01
ubuntu-desktop is a meta-package (think empty package or phantom package). Removing it will NOT break your system and will NOT remove GNOME, it only exists to provide an easy way to install lots of applications at once.

---

### Post by oliviacond on 2007-01-01
So it become useless after applications are installed?
I saw this in ubuntu-desktop decription:
> 
It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

---

### Post by jvc26 on 2007-01-01
I was about to ask that one too! If I remove ekiga (and consequestly ubuntu-desktop) will this cause absolutely no problems? And if not does this mean the same issue for an xubuntu system - removing xubuntu-desktop wont cause any problems either?

Thanks,
Il

---

### Post by meng on 2007-01-01
It is true that if you want to upgrade from Dapper to Edgy (or from Edgy to Feisty), then ubuntu-desktop should be installed. So you should not upgrade from one version of Ubuntu to the other without having ubuntu-desktop intact. However, the day-to-day operation of your computer is not affected by removing ubuntu-desktop. There is no way of removing default applications without removing ubuntu-desktop. So either keep the default applications or remove ubuntu-desktop!!!

xubuntu-desktop, ubuntu-desktop and kubuntu-desktop are all meta-packages - they are empty themselves, but they list several dependencies which aid in installation of several programs at the same time.

---

