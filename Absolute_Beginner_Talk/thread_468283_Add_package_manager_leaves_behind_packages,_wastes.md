---
title: "Add package manager leaves behind packages, wastes disk space..."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-08
Has anyone noticed that if you install a package, then remove it, it leaves behind:
-settings in your home folder (and who knows where else)
-the package to install from
-and probably other stuff that slows it down over time

I'm wondering if there is some kind of trustworthy program that will detect what programs are not installed anymore, and remove their files from the system?  Does anyone else notice this or have a solution...

---

### Post by Najand on 2007-06-08
use:
```

sudo apt-get remove --purge PACKAGENAME

```
Or Remove comletely option in Syanptic to remove settings, etc.

---

### Post by ryanVickers on 2007-06-08
But how would I know what's still installed without looking through all the ".folders", and if it's already been "uninstalled", it won't allow the complete remove or even regual remove option I think.  And even when you do, it seems to leave some stuff behind!
> sudo apt-get remove --purge PACKAGENAME
But that's an idea...

---

### Post by Shazaam on 2007-06-08
Look here--
[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)
Good stuff.

---

### Post by ryanVickers on 2007-06-08
Ok, thanks!  I think that pretty much covers everything!  This helped me and I think lots of people will use this...

---

