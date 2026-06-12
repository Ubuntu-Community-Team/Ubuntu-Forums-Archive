---
title: "install .deb in *ubuntu"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-07-02
Is it possible to install a .deb file in *ubuntu?

---

### Post by buzzmandt on 2007-07-02
.deb is ubuntu format, download it, right click and install

---

### Post by Genecks on 2007-07-02
It's debian, but ok.

---

### Post by buzzmandt on 2007-07-02
right, ubuntu is a debian based distro

---

### Post by Sef on 2007-07-02
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by BoneSaw on 2007-07-02
i think feisty has a built in package installer for .deb packages 

if that doesnt work you can sudo dpkg -i *package name*

---

### Post by eternalsword on 2007-07-02
it's not typically a good idea to install just any .debs since there's no dependency checking done, it could bork your system.  make sure first that you have all dependencies for it and that it is compatible with your version of ubuntu

---

### Post by Golyadkin on 2007-07-02
Well, in essence aptitutude and apt-get also simply install .debs. The only difference is dependency checking and compatibility, perhaps automatic architecture selection. x86 / 64bits.

---

### Post by regomodo on 2007-07-03
> **eternalsword said:**
> it's not typically a good idea to install just any .debs since there's no dependency checking done, it could bork your system.  make sure first that you have all dependencies for it and that it is compatible with your version of ubuntu

eh? if you do *$ dpkg -i package_name.deb*   it'll tell you if you are missing something and won't continue till they are there.


If you have done a server install the gui app is *gdebi-gtk *i believe. you have to install *gdeb*i and then for the .deb file set it to run with *gdebi-gtk*

---

