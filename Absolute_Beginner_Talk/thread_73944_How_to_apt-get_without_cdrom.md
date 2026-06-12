---
title: "How to apt-get without cdrom"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by nuvolenji on 2005-10-10
I don't have the ubuntu cdrom with me now. I nonetheless would like to install cvs. But for that particular package apt-get asks for the cdrom. Is there any way to for a netinstall of that particular package?

---

### Post by loupy on 2005-10-10
you need to edit your sources.list file

from a terminal run:

sudo gedit /etc/apt/sources.list

the first line of that file will reference the cd-rom, just put a # in front of it to comment it out, save it, and do a reload in synaptic package manager.  It will no longer look for the CD.

---

### Post by nuvolenji on 2005-10-10
thanks! it worked just fine

---

### Post by wylfing on 2005-10-10
I think it's preferable to advise people to use the graphical tools when they are available. On your main toolbar, choose System > Administration > Synaptic Package Mangager. Once Synaptic is up and running, choose Settings > Repositories. From there you can add and remove repositories as much as you like. If you don't want the CD-ROM anymore, just remove it from the list.

Edit: I see that you managed anyway. Great!

---

### Post by Kyral on 2005-10-10
Wiether or not its preferable, its a heck of a lot easier to tell people to do it the command line way. I wrote a HOWTO here for Terminal Beginners (Thread "Terminal For Beginners")

---

