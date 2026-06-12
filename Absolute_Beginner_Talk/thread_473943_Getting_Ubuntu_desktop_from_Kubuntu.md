---
title: "Getting Ubuntu desktop from Kubuntu"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by solcore on 2007-06-14
I'm running Feisty Kubuntu and I want to try the Ubuntu and Xubuntu desktops as well.  Can anyone help me with what code to use?

(I've seen the code to get kubuntu or xubuntu from ubuntu, but not from kubuntu)

Is there a repository I have to load first?

---

### Post by mlentink on 2007-06-14
```
sudo apt-get install ubuntu-desktop
```
to install the gnome variant, and
```
sudo apt-get install xubuntu-desktop
```
to install the xfce variant

---

### Post by gn2 on 2007-06-14
Easiest way would be to open the package manager, (Adept I think?) and mark the ubuntu-desktop package for installation.

or "apt-get install ubuntu-desktop"  in a terminal (without the quotes)


**EDIT:**Obviously with sudo first... terminal's just not my thing. Point-and-click does the trick!

---

### Post by NeoLithium on 2007-06-14
```

sudo aptitude install ubuntu-desktop

```

Apt-get and aptitude will both work, though if you decide to remove one, aptitude handles dependencies a little better and will make for a smoother add/remove.

The repositories, you can get a commonly used list from [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

