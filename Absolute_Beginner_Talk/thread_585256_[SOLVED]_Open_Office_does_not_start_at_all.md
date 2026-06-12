---
title: "[SOLVED] Open Office does not start at all"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-21
hey having trouble with OO, ive tried the updates that were released from a couple hours ago, but even after that - clicking on word processor or database etc etc nothing happens and no crash logs are made in /var/crash,  i tried completely reinstalling OO, but still have the same issues, anyone know of a solution?

---

### Post by oilchangeguy on 2007-10-21
> **dynamethod said:**
> hey having trouble with OO, ive done the update from a couple hours ago, but even after clicking on word processor or database etc etc nothing happens and now crash logs are made in /var/crash,  i tried completely reinstalling OO, but still have the same issues, anyone know of a solution?

"i've done the update from a couple hours ago" means nothing. what update did you do?

---

### Post by Colro on 2007-10-21
Do you have a custom desktop theme enabled? 

If not, I'm not quite sure what your problem is.

If so, try going back to the default theme (Human) and opening OO again -- it loves to crash when it doesn't like a theme. A fix for this if you want to keep your theme is to remove OO.org's gtk package. Keep in mind that this will make it open in full screen mode, so you'll probably want to put it on a separate desktop/workstation when you open it:

```
sudo apt-get remove openoffice.org-gtk
```

---

### Post by dynamethod on 2007-10-21
when you run update manager, you update correct? well there were some updates for OO released a couple hours ago, and i updated OO at that point, although the updates did nothing

---

### Post by dynamethod on 2007-10-21
> **oilchangeguy said:**
> "i've done the update from a couple hours ago" means nothing. what update did you do?

and sorry, but i cant remember the EXACT name for each update, i dont have a photographic memory

---

### Post by dynamethod on 2007-10-21
> **Colro said:**
> Do you have a custom desktop theme enabled? 

If not, I'm not quite sure what your problem is.

If so, try going back to the default theme (Human) and opening OO again -- it loves to crash when it doesn't like a theme. A fix for this if you want to keep your theme is to remove OO.org's gtk package. Keep in mind that this will make it open in full screen mode, so you'll probably want to put it on a separate desktop/workstation when you open it:

```
sudo apt-get remove openoffice.org-gtk
```

Actually my DE is customized, i have compiz-fusion, emerald and AWN running, would this conflict with OO?

---

### Post by Colro on 2007-10-21
It might. Just try removing that package and see if it helps your problem. You can re-install it very easily anyway:

```
sudo apt-get install openoffice.org-gtk
```

---

### Post by dynamethod on 2007-10-21
unfortunatly doesnt help :S

---

