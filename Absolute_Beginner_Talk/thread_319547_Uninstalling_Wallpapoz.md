---
title: "Uninstalling Wallpapoz"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by suki on 2006-12-15
How do I uninstall wallpapoz? I've gotten rid of it's folder and such but the application is still there and under accessories.

---

### Post by _simon_ on 2006-12-16
Right click on your menu, choose edit menu's.

Locate the entry in the menu, right click and choose delete.

You don't say which version you are using so it may vary slightly.

---

### Post by suki on 2006-12-17
> **_simon_ said:**
> Right click on your menu, choose edit menu's.

Locate the entry in the menu, right click and choose delete.

You don't say which version you are using so it may vary slightly.

Thank you.

---

### Post by macogw on 2006-12-17
How did you install it?  If you used synaptic or apt-get, just go to the terminal and tell it

sudo apt-get remove wallpapoz


EDIT: nevermind

From the wallpapoz install instructions:

Later if you want to uninstall it:
# python install.py uninstall

---

### Post by confused! on 2008-02-10
Hey, tried running sudo apt-get remove wallpapoz but just getting the error message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wallpapoz

Any ideas? Can't just move the folder either --- get a permission denied error message.

---

### Post by apokkalyps on 2008-03-19
im no expert, but I think the sudo apt-get uninstall isnt working because you didn't install it as a package

follow macogws suggestions:> # python install.py uninstall

---

