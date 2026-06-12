---
title: "How to uninstall..?"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by cvogel on 2005-06-23
Hi all --

Quick question.  How do I uninstall programs that I've installed without apt-get? For example, say, something I compiled from source or a .deb package?

Thanks,

Cory

---

### Post by frodon on 2005-06-23
with .deb file, dpkg -r yourdebfile.deb (remove), if you want more information dpkg --help.
If you have compiled software from source, i hope you keep the repertory where you did a make install, if yes i think a make uninstall in this repertory will remove the program.
But don't forget to have a look in synaptic, if you find your program it will be easier to remove it.

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=cvogel]Hi all --

Quick question.  How do I uninstall programs that I've installed without apt-get? For example, say, something I compiled from source or a .deb package?

Thanks,

Cory[/QUOTE]


You can uninstall debs in synaptic really easily.

---

