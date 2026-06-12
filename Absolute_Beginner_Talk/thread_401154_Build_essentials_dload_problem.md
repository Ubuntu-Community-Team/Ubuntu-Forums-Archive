---
title: "Build essentials dload problem"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by n0n@m3 on 2007-04-04
Hello,
I need some information on downloading the basic build essential packages for Ubuntu 6.10. I want to manually download them because i need them to install my modem driver. I really don't know where to find them, every tutorial that i found makes reference to the package manager, but it is obvious that i can't use it here as i don't have access to the internet.
I suppose i'm looking for a .deb package.
I would appreciate any help here.
Thanks for your time...

---

### Post by Maestro23 on 2007-04-04
Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Good luck.

---

### Post by taurus on 2007-04-04
Build-essential package is on the install CD so if you have that CD, insert it into a drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

