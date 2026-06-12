---
title: "System Error"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-08-07
I was installing virtualbox, and it froze in mid install (using a .deb file) so i restarted. Now when i try to access my Synapic Package Manager i get this

 A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'


please walk me through fixing this problem

---

### Post by benanzo on 2007-08-07
I think you'll just need to reconfigure it with **dpkg**.
Open a terminal and type:
```
sudo dpkg-reconfigure virtualbox
```
That should run through a reconfigure/reinstallation of the package.

---

