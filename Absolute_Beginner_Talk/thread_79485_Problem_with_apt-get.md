---
title: "Problem with apt-get"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by daoc on 2005-10-20
hey guys, i been trying to install some things on ubuntu - as ove said before im a noob with linux, naywho... i get this message alot:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

i tired apt-get update but it still didnt work

can some one help?

---

### Post by LHZ on 2005-10-20
The Hoary backports have been disabled, and the Breezy bakports aren't up yet. It's best to remove the 'backports' repository for a while. (You can do this by commenting it out in sources.list).

---

### Post by daoc on 2005-10-20
why have the horay ones been disabled?

---

