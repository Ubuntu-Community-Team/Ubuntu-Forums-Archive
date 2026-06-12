---
title: "gdm what?!?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-11-08
okay i go to system => administrator then i click login windows and it brings this stupid error

You might in fact be using a different display manager, such as KDM (KDE Display Manager) or xdm. If you still wish to use this feature, either start GDM yourself or ask your system administrator to start GDM.



all i want to do is make it so i can login automatically using ubuntu...

---

### Post by cubeist on 2007-11-08
Hey, did you start out using KDE and then switch to gnome at some point? or are you using KDE and you want GDM?  Anyway, what I would do is go to synaptic and check to see which package is installed.  If they are both installed (KDE Display Manager and GDM) try uninstalling the one  you don't want (KDE) and reinstall GDM... just be cautious when uninstalling that it does not automatically remove core packages needed to run your programs.  Once you have sorted  stuff out in synaptic go to services (system:admin:services) and make sure GDM is checked and KDE is unchecked.... then restart....

actually... try the services thing first... then synaptic!

---

### Post by strabes on 2007-11-08
It looks like you have installed kde on top of ubuntu. A solution that is much easier than what cubeist said is to run the following in a terminal (Applications > Accessories > Terminal)```
sudo dpkg-reconfigure gdm
```

Select gdm.

---

### Post by cubeist on 2007-11-08
> **strabes said:**
> It looks like you have installed kde on top of ubuntu. A solution that is much easier than what cubeist said is to run the following in a terminal (Applications > Accessories > Terminal)```
sudo dpkg-reconfigure gdm
```

Select gdm.

Yes, yes! much easier... wish I had thought of that!  try strabes method first, then the services thing if you are still having trouble.

---

### Post by zvacet on 2007-11-08
On login screen when you see box in wich you have to type username and password on the bottom left you can choose sessions.Select GDM.

---

