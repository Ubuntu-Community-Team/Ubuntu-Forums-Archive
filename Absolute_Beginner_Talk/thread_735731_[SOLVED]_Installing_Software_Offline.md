---
title: "[SOLVED] Installing Software Offline"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-25
Hi!:)

I was wondering if there's a way to install software on a PC which does not have an internet connection. I made an apt-on CD but when I try to install from it,(by clicking .deb files) it tells me that some more packages have to be installed for this package to work and so we need an internet connection.:confused:

Any other method to install software offline will be appreciated.

Thanks:popcorn:

---

### Post by WarMonkey on 2008-03-25
You need to install its dependancies first. If you can't find them on the Ubuntu Cd, then yes,  you do need an internet connection.

---

### Post by c-ron on 2008-03-25
Hi,
You had the right idea of putting the deb files on CD, the problem is that apt will usually require dependencies to be met before installing a package. Check [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to see what dependencies are needed with any of the packages you want to install, and burn those as well.

You can also use (K,X,U)buntu LiveCDs to pull some packages from with the command: 
```
sudo apt-cdrom add
```

---

