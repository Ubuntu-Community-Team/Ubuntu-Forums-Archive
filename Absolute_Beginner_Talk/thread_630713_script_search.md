---
title: "script search"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by simocusi on 2007-12-03
i want to take the script of gmail notifier and the one of tomboy notes and put them in the booting folder. However I don't know where to find them.. Any tool to do this or just the folder i can find them?

Thanks

---

### Post by madamore on 2007-12-03
the easiest way to know what and where have been installed by a package for a "windows use to" is going to synaptic:
$ sudo synaptic
or
System->Synaptic Package Manager

press search with the name of the package or any other search criteria available.
then right click on it, go to properties, and finally to installed files.


An alternative is by shell:
$ sudo dpkg -L *package_name*


Hope this help you!

---

### Post by simocusi on 2007-12-03
yes!

thanks

---

