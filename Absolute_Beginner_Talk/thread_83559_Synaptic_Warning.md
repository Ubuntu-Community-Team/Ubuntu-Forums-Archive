---
title: "Synaptic Warning?"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Donnut on 2005-10-29
I am currently trying to install ATI drivers on my comp, and when I use command line, or synaptic, i get the following errors:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Are these why I'm having trouble installing the drivers?

---

### Post by Donnut on 2005-10-29
k, now I find out I can not install some other packages too.  Any thoughts?

---

### Post by audax321 on 2005-10-29
I'm pretty sure that [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) should be:

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

---

### Post by Remmelas on 2005-10-29
i'm not sure there are many backports yet, but, these apt.sources lines seem ok, it's a mirror of backports




deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

---

