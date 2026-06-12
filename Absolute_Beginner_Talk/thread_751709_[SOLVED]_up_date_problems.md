---
title: "[SOLVED] up date problems"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by SteveNorman on 2008-04-10
I tried running my updates and I keep getting this:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


how do I run dpkg --configure -a'

just type it in a terminal?

---

### Post by Tatty on 2008-04-10
yes, type it in a terminal.  But you will want to preface it with sudo as it requires superuser privilages:

```
sudo dpkg --configure -a
```

---

### Post by SteveNorman on 2008-04-10
killer, that worked. It said i have a broken package on my system and to use a broken pakage filter, where is said filter?

---

### Post by Tatty on 2008-04-10
Load up synaptic.  In the bottom left it says "Custom Filters", click on that.  Then in the top left it will show a list of filters, select "Broken".

I have never encountered this myself, but i presume it will give you some options for re-installing/repairing the package.

---

### Post by Oldsoldier2003 on 2008-04-10
> **SteveNorman said:**
> killer, that worked. It said i have a broken package on my system and to use a broken pakage filter, where is said filter?

just fix it by running :
```
sudo apt-get install -f
```
though you could go into synaptic and use the broken packages filter on the left side of the gui screen, its much faster to just run the command from the terminal.

---

### Post by SteveNorman on 2008-04-10
everything worked as you guys said,, thanks a bunch

---

