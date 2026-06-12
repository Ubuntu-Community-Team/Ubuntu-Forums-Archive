---
title: "Debian menu help"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Zakama on 2008-02-21
Hey all, first post here and I have a problem. I installed the menu-xdg package and the debian menu will show up in the menu editor, I can check the box, but there is no apply button. I've tried checking it and clicking close, no dice there. I took a screenshot of the menu so you can see where I get stuck, Thanks in advance.

[[IMG]http://img85.imageshack.us/img85/8082/menuvv4.png[/IMG]](http://imageshack.us)

---

### Post by wolfen69 on 2008-02-21
first, try
```
sudo apt-get install menu
```
then see if it will work

---

### Post by Zakama on 2008-02-21
> **wolfen69 said:**
> first, try
```
sudo apt-get install menu
```
then see if it will work

Nope, nothing.

---

### Post by p_quarles on 2008-02-21
The menu won't show up if there's nothing in it. And, by default, there is nothing in it.

---

### Post by ubuntu27 on 2008-02-21
Install Debian menu:

```
sudo apt-get install menu menu-xdg
```

Update the menu entries in Debian Menu:

```
sudo update-menus
```

Seei if that helps. :)

If that dosn't work, try the follwing

```
sudo dpkg-reconfigure menu
```
```
sudo dpkg-reconfigure menu-xdg
```

And again:
```
sudo update-menus
```

---

