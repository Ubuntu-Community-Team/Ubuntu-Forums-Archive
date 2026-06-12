---
title: "how do i uninstall things?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by ren wins on 2005-11-27
specifically
i downloaded gtkwifi from the gtkwifi project forum

it's a .deb file, i installed it and started using it (i think) and then restarted my computer

now i cant connect to the internet

hopefully uninstalling it will fix things

---

### Post by sjh on 2005-11-27
I don't know if it will fix your internet problem but to remove a package

```
sudo dpkg -r PackageName
```

should do the trick.

Hope this helps,
SJH

---

### Post by aysiu on 2005-11-27
Open up System > Administration > Synaptic Package Manager, find gtkwifi, right-click it, and mark it for complete removal. Then click Apply.

---

### Post by ren wins on 2005-11-27
either of these will do the job?

---

### Post by aysiu on 2005-11-27
[QUOTE=ren wins]either of these will do the job?[/QUOTE] Theoretically, yes. The difference between "mark for removal" and "mark for complete removal" is the latter removing not only the application but all of its configuration files as well.

---

### Post by ren wins on 2005-11-27
double post

---

### Post by sjh on 2005-11-27
Yes.  Synaptics is a graphical front end to apt-get.  Synaptics and apt-get are the preferred methods of installing Ubuntu packages and resolves dependences for the install.  Dpkg is used to install Debian packages and does not resolve dependencies.  Either will remove a package after it is installed.

SJH

---

### Post by ren wins on 2005-11-28
will dpkg tell me there are dependency problems if i try to install with it?

---

### Post by aysiu on 2005-11-28
[QUOTE=ren wins]will dpkg tell me there are dependency problems if i try to install with it?[/QUOTE] Yes, but it won't automatically resolve them. dpkg will just tell you what's missing. Synaptic / apt-get will find what's missing and install the dependencies.

---

### Post by patrick295767 on 2005-11-28
sudo dpkg -r PackageName

or  apt-get remove name_prg_installed
  
or use synaptic; it's easier !:)

---

