---
title: "New Install , Damaged Main Menu."
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Wiebelhaus on 2007-08-03
Somehow after new installation I have managed to damage the main menu , Cannot Right click & edit main menu nor edit from System>Preferences>main menu , Just say's "Starting Main menu" and never show's up , I've ran "Killall gnome panel" & Rebooted.

Anyway to force an application? or is it possible to purge what ever is preventing it from starting?

Thanks.

---

### Post by Wiebelhaus on 2007-08-03
Interesting thing is that nothing installed is being added , like it's crashing and no new entries can be added.

---

### Post by PriceChild on 2007-08-03
I can't help with the real program... but by the way you would need```
killall gnome-panel
```not```
killall gnome panel
```

---

### Post by Wiebelhaus on 2007-08-03
> **PriceChild said:**
> I can't help with the real program... but by the way you would need```
killall gnome-panel
```not```
killall gnome panel
```

typo , my bad.

---

### Post by Wiebelhaus on 2007-08-03
I re-installed it via "sudo apt-get install gnome-main-menu" no luck.

---

### Post by Wiebelhaus on 2007-08-03
I Reinstalled gnome via "sudo apt-get install gnome" no luck..

---

### Post by Hospadar on 2007-08-03
try completely removing when you reinstall
```
sudo apt-get install --purge --reinstall gnome-menus
```
this should completely remove all your menu config files and reinstall the gnome menus.  Hopefully it won't damage anything =)
you may want to run the same command on gnome-panel
```
sudo apt-get install --purge --reinstall gnome-panel
```
If that doesn't work, you could try poking through synaptic and reinstalling other gnome packages with this method, I would continue to do it with the command line so you can completely reinstall things (with the --purge).  just reinstall with synaptic won't remove config files.

---

### Post by Wiebelhaus on 2007-08-03
> **Hospadar said:**
> try completely removing when you reinstall
```
sudo apt-get install --purge --reinstall gnome-menus
```
this should completely remove all your menu config files and reinstall the gnome menus.  Hopefully it won't damage anything =)
you may want to run the same command on gnome-panel
```
sudo apt-get install --purge --reinstall gnome-panel
```
If that doesn't work, you could try poking through synaptic and reinstalling other gnome packages with this method, I would continue to do it with the command line so you can completely reinstall things (with the --purge).  just reinstall with synaptic won't remove config files.

Thank you.

---

