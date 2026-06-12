---
title: "Edit Menu Fuction"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Manoau2002 on 2006-05-04
When you click on edit menus over applications on the top panel of gnome it opens the menu editor. In the list of choices of categories is Debian. Debian is fuzzed out in this menu. How do you tell the menu editor to enable debian under applications. I want to be able to see every program I install listed under applications on the panel and not scattered all over creation.

---

### Post by skippy81 on 2006-05-05
The reason "Debian" is fuzzed is because it is a menu group which doesn't contain anything.   Use the left hand panel of the menu editor to select "Debian" and then use the "new entry" button on the right-hand panel to add items to it. 

"Debian" is not a program or menu item, it is simply an empty application menu catagory which is pre-made with a pretty name and logo :)  If your aim is just to tidy up and reorganise your programs, then you can drag them between the panels, so you could put all your items in the "Games" section into a different section for instance.  

Hope I cleared that up for you.

---

### Post by Sutekh on 2006-05-05
You need to install the following packages to enable the Debian menu
```
sudo apt-get install menu menu-xdg
```

Description of the packages

[Ubuntu Packages - menu](http://packages.ubuntu.com/breezy/admin/menu)

[Ubuntu Packages - menu-xdg](http://packages.ubuntu.com/breezy/admin/menu-xdg)

---

