---
title: "[SOLVED] Can't switch  to bottom workspaces (compiz)"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Jake90 on 2008-01-20
Hi, I recently enabled compiz and it's great I have mac4lin and everything.If I have 4 workspaces in one row and press ctrl-alt-right then it switches to the next one and I can access all 4. My problem comes come up when I have 4 workspaces in 2 columns and 2 rows. I can press the window button (I think it's called the special button) and e and it will show all 4 workspaces and I can select one. Also when I press ctrl-alt-right I can go from 1 to 2 or 3 to 4, but I can't get from 1 to 3 or 2 to 4. I can only go right or left i can't go up or down. I am probabaly not giving enough information so if you need more just tell me. Thanks a lot

---

### Post by SOULRiDER on 2008-01-20
With crtl + alt + up/down you should be able to switch workspaces vertically.

---

### Post by Jake90 on 2008-01-20
> **SOULRiDER said:**
> With crtl + alt + up/down you should be able to switch workspaces vertically.

That is my problem exactly when I press ctrl + alt + right/left it switches to it fine but when I try ctrl + alt + up/down nothing happens

---

### Post by DrMega on 2008-01-20
I get the same problem. :(

---

### Post by SOULRiDER on 2008-01-20
Install the package compiz-gnome
```
sudo aptitude install compiz-gnome
```
Witht hat package you can configure in detail all the desktop effects.

---

### Post by Jake90 on 2008-01-20
> **SOULRiDER said:**
> Install the package compiz-gnome
```
sudo aptitude install compiz-gnome
```
Witht hat package you can configure in detail all the desktop effects.
Ok, now what do I do?

---

### Post by SOULRiDER on 2008-01-20
You should be able to configure everything under system > Preferences > and i cant remember where else :P Check the button bindings for the actions.

---

### Post by Jake90 on 2008-01-20
Ok, I figured it out. I had Cube enabled so I disabled it and enabled Desktop Plane instead. Cube only works across not down.

---

### Post by SOULRiDER on 2008-01-20
Good thing its working now :)

---

