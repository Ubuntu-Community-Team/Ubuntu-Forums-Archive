---
title: "Navigate to File in Nautilus, How to Open Terminal as SU?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by GregA on 2008-03-12
I'm missing Konqueror's easy ability to navigate to any file in the tree, then open a terminal with F4 - having the terminal at that location (no need for cd commands.   Is something similar available in gnome?  

I have read that "alt+F2" will open the run window, and then "gksudo nautilus" will open nautilus as super user - - that helps, but is not the same as easing the navigation to a file several levels deep, via the gui, and then going to the terminal.

(I'm not a great typist, so using the gui often helps me with speed).

Thanks

---

### Post by Oldsoldier2003 on 2008-03-12
> **GregA said:**
> I'm missing Konqueror's easy ability to navigate to any file in the tree, then open a terminal with F4 - having the terminal at that location (no need for cd commands.   Is something similar available in gnome?  

I have read that "alt+F2" will open the run window, and then "gksudo nautilus" will open nautilus as super user - - that helps, but is not the same as easing the navigation to a file several levels deep, via the gui, and then going to the terminal.

(I'm not a great typist, so using the gui often helps me with speed).

Thanks

```
sudo aptitude install nautilus-open-terminal
```
then after it installs:

```
killall nautilus
```

this will restart all instances of nautilus and you'll be able to use the terminal from here plugin

---

### Post by GregA on 2008-03-12
Thanks very much!  I'm still learning how to work in gnome-land, it seems to be going well in large part because of the great help at these forums.

---

### Post by forrestcupp on 2008-03-12
also,
```
sudo apt-get install nautilus-gksu
```
allows you to open files in nautilus with super user privileges.

---

