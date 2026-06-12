---
title: "Trouble with repositories and installing from 'Add Applications menu'"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by discofro on 2005-11-13
Hi Everyone,

I am having some trouble installing some software from the Add Applications menu, and as per the instructions for codecs on ubuntuguide.org

I uncommented the lines about the repositories in the sources list, and the add applications menu said I was able to install programs from there, but when attempted to install VLC player, and Real player (as per my testing) I got the following error messages

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I have this working on another machine so I am not sure what I am forgetting to do. Any help is appreciate,

-Fro

---

### Post by matthewv on 2005-11-13
You will need to comment out the lines about the backports in your /etc/apt/sources.list , as the breezy backports do not yet exist.

---

