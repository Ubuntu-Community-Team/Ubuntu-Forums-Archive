---
title: "Update Manager error"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2007-05-28
I am experiencing this problem with update manager..... How do I fix it?
Thanks
Loyaleagle

ERROR:

'E:Problem parsing dependency Depends, E:Error occurred while processing thekompany-support (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by aktiwers on 2007-05-28
Try removing the Automatix links in your source file:
```
gksudo gedit /etc/apt/sources.list
```

And save the file. 

Then run:
```
sudo apt-get update
```

---

### Post by arnieboy on 2007-05-28
> **aktiwers said:**
> Try removing the Automatix links in your source file:
```
gksudo gedit /etc/apt/sources.list
```

And save the file. 

Then run:
```
sudo apt-get update
```

Removal of the AX repo is not required. The erring package has long been fixed and a simple
```
sudo apt-get update
``` will fix this issue

---

### Post by aktiwers on 2007-05-28
Heh ok.. didnt know that. 
What happend to your beans Arnie?

---

### Post by arnieboy on 2007-05-28
> **aktiwers said:**
> Heh ok.. didnt know that. 
What happend to your beans Arnie?
aktiwers:
I baked them real good and now they are history.
-Arnie

---

