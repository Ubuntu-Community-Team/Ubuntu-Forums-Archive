---
title: "Software Updates"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Ianman on 2007-08-31
Hi all,

Unfortunately I don't totally understand how the system update works in Ubuntu but I was just wondering, is software that is installed from a DEB package also updated with the rest of the system? Or do I have to manually install newer versions?

Thanks!

---

### Post by Steve1961 on 2007-08-31
The beauty of the update system is that everything is updated when new software enters the repositories.  That said, to ensure the stability of each version of Ubuntu most updates are just security fixes and the like.  This minimizes the amount of updates that come down the line and prevents potential conflicts.  If you install a deb file that isn't in the repositories then that obviously won't get updated - unless it subsequently gets added to the repositories and that version is newer than the one you installed.

---

### Post by panther_sn on 2007-08-31
If the software is in the repositories it will be updated manually, but generally if you have installed it from a .Deb it won't be and you will need to update it manually.

Hope that helps

---

### Post by Spr0k3t on 2007-08-31
Packages that you pull from download sites such as getdeb.net will need to be updated manually.  Packages that you add to your repositories are updated automatically when connected to the net.

Make sense?

---

### Post by Ianman on 2007-08-31
Ok so anything I install with apt-get or the synaptic package manager will be updated.

Thanks for that guys!

---

