---
title: "Reinstall of Crossover"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by kevinmro on 2007-04-13
Hey. Installed Crossover, decided to repartition and reinstall edgy.  Fresh install of edgy now...crosser wont install get an error from Package Manager "Error:Conflicts with the installed package 'crossover-pro'.  How can this be?..I reformatted!..at a loss.  Any help?

---

### Post by ajmorris on 2007-04-14
> **kevinmro said:**
> Hey. Installed Crossover, decided to repartition and reinstall edgy.  Fresh install of edgy now...crosser wont install get an error from Package Manager "Error:Conflicts with the installed package 'crossover-pro'.  How can this be?..I reformatted!..at a loss.  Any help?

Just checking.... In synaptic (System >> Administration >> Synaptic Package Manager) is that package installed? also from a terminal (Applications >> Accessories >> Terminal) if you type ```
sudo apt-get remove crossover-pro
```
what does that do?

---

### Post by kevinmro on 2007-04-28
OK, i was able to get a complete uninstall procedure from the Crossover Website, which included the instructions u gave me and a few more lines of terminal commands.  Thanks for your help.:popcorn:

---

