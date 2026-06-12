---
title: "Scripts and prorams executed at startup"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by smithwk2 on 2008-01-29
Where can I find all the scripts and program that are executed at startup?  Thanks in advance for the help.

Wayne

---

### Post by emarkd on 2008-01-29
Your startups are listed in Preferences > Sessions.  The entire OS's startups can be managed from System > Bootup Manager.

That last one may not be installed by default.  Search Synaptic and you'll find it there.

---

### Post by corney91 on 2008-01-29
The Bootup Manager is called startupmanager:
```
sudo apt-get install startupmanager
```

---

### Post by smithwk2 on 2008-01-29
Thanks for the help.  I installed startupmanager, but I cannot find it under System.  Should I be looking somewhere else?  Thanks again.

Wayne

---

### Post by emarkd on 2008-01-29
The menu item is called Bootup Manager.  It should be under system.  If you can't find it, you can run it from the terminal by running:

```
sudo bum
```

---

### Post by philinux on 2008-01-29
> **smithwk2 said:**
> Thanks for the help.  I installed startupmanager, but I cannot find it under System.  Should I be looking somewhere else?  Thanks again.

Wayne

System>Admin

---

### Post by philinux on 2008-01-29
> **emarkd said:**
> The menu item is called Bootup Manager.  It should be under system.  If you can't find it, you can run it from the terminal by running:

```
sudo bum
```

bum is not installed by default. Either install via apt-get or synaptic if you wish.

graphical runlevel editor
Boot-Up Manager is a graphical tool to allow easy configuration
of init services in user and system runlevels, as far as changing
Start/Stop services priority.
Homepage: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by polmir on 2008-01-29
Red this post
[http://ubuntuforums.org/showpost.php?p=487138&postcount=1]("http://ubuntuforums.org/showpost.php?p=487138&postcount=1")
and this
[http://qref.sourceforge.net/Debian/reference/ch-system.en.html#s-boot]("http://qref.sourceforge.net/Debian/reference/ch-system.en.html#s-boot")

---

### Post by smithwk2 on 2008-01-29
Thanks for all the help!!!  I am in good shape on this matter now.  Thanks again.

Wayne

---

