---
title: "Application/toolbar - Tooltips how to remove them?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Abze on 2006-11-01
Im so sick of the tooltips that keeps apearing when my mouse is going over different application in the menu or on the Gnome menu. 

Benn searching for almost an hour now in Google, cant belive I havent found a way yet.

Someone with a good idea

Thanx for the help :) 


Looking forward to check out this forum, relative new to Linux and Ubuntu ;)

---

### Post by Joe_CoT on 2006-11-01
From the console, run:

```
gconf-editor
```

Then using the tree to the right, go / -> apps -> panel -> global , and then uncheck tooltips_enabled

Found the method [in this gnome bug report]("https://launchpad.net/products/gnome-panel/+bug/31102"), which says it doesn't work, but it appears to work for me :shrug:

---

### Post by Abze on 2006-11-02
DIdint work for me :(

I realy hope there is another way 


Edit: Ok it worked after an reboot :D And u learned me an usefull command :) thanx!

---

