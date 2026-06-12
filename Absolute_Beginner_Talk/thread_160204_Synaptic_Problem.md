---
title: "Synaptic Problem"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Lex-Man on 2006-04-14
When ever I load up Synaptic Package Manager I get this long list of problems 

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

What can I do to fix them?

---

### Post by cilynx on 2006-04-14
I believe the button on Synaptic is 'Reload'.  This will update your sources and create the files that it's looking for.

---

### Post by xyz on 2006-04-14
Hi,
I think you have to go into Synaptic>Repository>Add your [Http://gb...and](Http://gb...and) so on.

---

