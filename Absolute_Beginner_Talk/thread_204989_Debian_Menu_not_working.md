---
title: "Debian Menu not working"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by underworld288 on 2006-06-27
ok, Ubuntu 6.06 Dapper Drake comes with it installed, or atleast mine did, but it is not showing up. How do i make it show up?

---

### Post by glinsvad on 2006-06-27
It's in the Universe repositories:
```

sudo apt-get install menu

```

---

### Post by az on 2006-06-27
..and it was not there by default in Breezy.  Nor Hoary nor Warty,

---

### Post by underworld288 on 2006-06-27
i know it wasn't there in previous versions but it is saying that it is installed, but it isn't showing up. I gues i can try uninstalling then reinstalling.

---

### Post by catlett on 2006-06-27
For some reason the debian menu in Dapper wouldn't work for me until I installed menu-xdg as well. Try running these and see what happens.
```
sudo apt-get update
```
```
sudo apt-get install menu 
```
```
sudo apt-get install menu-xdg 
```
```
killall gnome-panel
```
Then check under Applications again and see if it is there.

---

### Post by underworld288 on 2006-06-27
thanks that did it.

---

