---
title: "How do I uninstall programs?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ettienne on 2007-06-25
I installed Google Earth and want to uninstall it x2.
There are 2 copies installed (why is another question?), but all I want to do is get rid of it, as well as Envy and some other bits and pieces.
These programs do not appear on the Add/Remove list, nor on Synaptic Package Manager or Automatix.

---

### Post by w4ett on 2007-06-25
If you installed Google Earth via Automatix, then click on the uninstall tab in AX and it will be there in the Office Tab.  Best that you ask for further automatix help in their forum.

---

### Post by p_quarles on 2007-06-25
Open a terminal and type ```
~/google-earth/uninstall
```

FYI, I got this information in the README.linux file in the google-earth directory. If you look at that, it will give you some other techniques for removing the program. Generally speaking, though, anything that was installed in Wine or compiled from source can just be deleted straight up.

---

### Post by kevdog on 2007-06-25
Just a general uninstall procedure

If you are not sure of the exact name of the package or if it has a hyphen in the name, etc.

First
sudo aptitude search part_of_package_name (For example if not sure of full name of ndiswrapper, you could use ndis)

The result will be of the name of packages that are close to the part_of_package_name

After discovering correct name or syntax of package name from above command

sudo aptitude purge package_name

That's about it.

---

### Post by ettienne on 2007-06-25
Thank you kindly sirs,

Me: 2 vs Google Earth: 0

---

### Post by p_quarles on 2007-06-25
> **kevdog said:**
> Just a general uninstall procedure

If you are not sure of the exact name of the package or if it has a hyphen in the name, etc.

First
sudo aptitude search part_of_package_name (For example if not sure of full name of ndiswrapper, you could use ndis)

The result will be of the name of packages that are close to the part_of_package_name

After discovering correct name or syntax of package name from above command

sudo aptitude purge package_name

That's about it.
For packages, that will work. Google Earth, however, is just the Windows version wrapped in Wine (with an auto-install application), so it doesn't show up in aptitude.

---

