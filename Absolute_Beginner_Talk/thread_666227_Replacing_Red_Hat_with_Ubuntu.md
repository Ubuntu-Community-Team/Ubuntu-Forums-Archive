---
title: "Replacing Red Hat with Ubuntu"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Fat Turtle on 2008-01-13
Hi,

My girlfriend has just got a computer from her college, which is currently dual-booted with Windows XP and Red Hat 5. We are having serious trouble with getting Red Hat do to anything (it can't see all the partitions, and just booting takes 40 minutes!) - I suspect this is becuase it was installed from an image by the college computer guys, and is probably meant to be for network use only.

While I'm sure there is some way to configure Red Hat to work as we want it, neither of us have the expertise or patience to do so at the moment - as I've been sucessfully installing and using Ubuntu 7.10 for the last few months we would much rather replace the current Red Hat version with Ubuntu and have a fresh start.

Now to my question: If I start the Ubuntu installer from the CD, is there any way to write over the Red Hat installation to in effect replace it with Ubuntu on that partition? Or would i have to manually remove / uninstall Red Hat, and then install Ubuntu?

She has three partitions, one Windows XP, one Red Hat and one for data storage (NTFS I think).

Thanks in advance!

---

### Post by Xavieran on 2008-01-13
[QUOTE=Fat Turtle]Now to my question: If I start the Ubuntu installer from the CD, is there any way to write over the Red Hat installation to in effect replace it with Ubuntu on that partition? Or would i have to manually remove / uninstall Red Hat, and then install Ubuntu?[/QUOTE]

Just start the Installer and select the Red Hat partition as / (root) and also make sure you have swap as well...you could use gparted before you start the install just to format red hat's partition and create swap space (if you don't have it)

---

