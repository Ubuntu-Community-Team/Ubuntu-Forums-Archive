---
title: "Nautilus broken on Places Menu in Tool Bar"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Mahyar on 2007-08-09
I recently tried Thunar, but quickly rejected it and returned to Nautilus.

The problem is that in my Places menu on the tool bar, all the items are still directed at Thunar and don't work anymore through Nautilus.  I get a popup with "Could not launch menu item" for my desktop, home folder and computer.

Does anyone know how I can re-assign Nautilus as the default window manager for those buttons?

Thanks if you can.  I've looked everywhere to no avail.

---

### Post by felicity on 2007-08-09
Did you try this?

From [Psychocats]("http://www.psychocats.net"):
Restoring Nautilus as the default
If you wish to restore Nautilus as the default file manager in Gnome, download [this script]("http://www.psychocats.net/ubuntu/restorenautilus.sh") to your desktop and paste these commands in the terminal:
```
cd ~/Desktop
```
```
chmod +x restorenautilus.sh
```
```
./restorenautilus.sh
```

---

### Post by Mahyar on 2007-08-10
Thank you Felicity.  It worked a treat!

---

