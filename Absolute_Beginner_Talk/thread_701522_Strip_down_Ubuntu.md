---
title: "Strip down Ubuntu"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-02-19
Hello I want to get rid of a lot of the applications that are pre-installed on Ubuntu (such as CD player, Serpentine etc.) but every time I decide to do it I stop when I says that genome-utils and ubuntu-desktop will be removed. What will happen if I remove those packages and how do I keep them but remove the applications that depend on them.

PS Is there a way I can restore my Linux main files to original state I mean sort of reset Linux or something?

---

### Post by kryth on 2008-02-19
this may be of some help
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Paqman on 2008-02-19
ubuntu-desktop can definitely be safely removed. 

It isn't an actual application. it's just a meta-package that exists to create dependencies. Installing it will cause all the packages that depend on it to be installed.

You can find out info about packages online, for example:
[gnome-utils](http://packages.ubuntu.com/gutsy/gnome/gnome-utils)
[ubuntu-desktop](http://packages.ubuntu.com/gutsy/metapackages/ubuntu-desktop)

You might also want to check out deborphan if you want to clean up your system. It finds and uninstalls orphaned packages.

---

### Post by notwen on 2008-02-19
Are you wanting it stripped down to the point you have no GUI or are you after a simple, clean GNOME desktop?

As for those packages mentioned, they are just meta-packages.  Removing them should not hurt your system.

---

### Post by northern lights on 2008-02-19
If you simply want a clean desktop, this might be too much for your case, yet if you wanna strip your system cause your machine is slow/old, you might want to try [Fluxbuntu]("http://fluxbuntu.org/js.html").

---

