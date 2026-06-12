---
title: "Installing flex problems!"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Slyth99 on 2005-10-08
Is there a web site where i can download flex. I am trying to install wine and it says that i don't have flex. I have tried the sudo apt-get install flex and I don't have the file on my system.
Thanks....

Also how do i access my second hard drive from my ubuntu system it doesn't have ubuntu installed on it but it was formatted when i installed ubuntu???

:(

---

### Post by mlomker on 2005-10-09
There must be something wrong with your repository configuration--flex is one of the core packages and is in the main Ubuntu repositories.

[Double-check]("http://www.ubuntuguide.org/sample/sources.list_extrarepositories") your /etc/apt/sources.list.  If you are using Breezy then the names will be a bit different and skip the mirrormax lines--that repository is empty now.

---

