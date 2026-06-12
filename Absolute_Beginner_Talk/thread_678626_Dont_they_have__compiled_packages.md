---
title: "Dont they have  compiled packages"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bibas on 2008-01-26
I had to install NDSWRAPPER for my wireless card and obviously, cant do it through synaptics.
Downloading the package and all its hell of dependencies of dependencies in my another windows computer is a pain.
Dont they have a single downloadable file which contains all the dependencies along with the program?

---

### Post by LukeCarrier on 2008-01-26
You're wrong in saying you have to download all the components seperately. Ubuntu has this neat tool called a package manager that keeps all the programs you install through it up to date. It also makes managing dependencies easier, since it installs all required prorams for you.

To install NDIS Wrapper, a nice visuallo application to manage the drivers you install with it and all the dependencies, just open a Terminal, and type in this line of code, and press enter:
```
sudo aptitude install ndisgtk
```
When prompted, enter you user account password and press enter, then follow the on-screen prompts.

---

### Post by bibas on 2008-01-26
thanks for the quick reply,

 i dont have internet connection in my ubuntu machine...does the program NDISwrapper come within the ubuntu CD or do i have to download it separately?

If i have to download it separately, is there any single file with all the dependencies included?

---

### Post by bibas on 2008-01-27
anybody ?? any idea on downloadable packages with dependencies included?

---

### Post by LaRoza on 2008-01-27
> **bishworaj Bastakoti said:**
> anybody ?? any idea on downloadable packages with dependencies included?

[http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk)

You can get the repositories on disk.

---

