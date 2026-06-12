---
title: "autoconf version problem"
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by rattusdatorum on 2005-09-01
Hi!

I need autoconf version >= 2.53 for an installation.
Well so far so good, I have autoconf installed, but only version 2.50 (well I thought so, but looking at autoconf* commandos (shell tab)),
damn. apt-get says I have the actual version.
So I installed a debian package with dpkg -i package259.deb
well didn't worked.

autoconf --version says I am using 2.13?
but avaiable autoconf commands are the following
autoconf      autoconf2.13  autoconf2.50

questions:
1) why the deb installation didn't worked (what should I do)
2) why autoconf2.13 is used and not 2.50
3) why is autoconf2.13 not "unistalled" (dependency?)

thx in advance

---

### Post by hod139 on 2005-09-08
First, the current version of autoconf in hoary is 2.59.  They also include version 2.13 for some backwards compatibility.  The problem is that if you have both versions installed, ubuntu makes the default 2.13 (who knows why).

The easiest solution then would be to remove autoconf 2.13, the debian 2.59, and reinstall ubuntu's 2.59.

I'm guessing the debian package did work (meaning it installed autoconf 2.59) but again just didn't make it the default.

If you can't unistall it, then you will have to manually make autoconf point to autoconf2.5.  Delete the autoconf link, and make your own pointing to the newer version.

Hope this helps.

---

