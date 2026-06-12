---
title: "Creating A Ubuntu DVD For Myself"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2008-01-02
I want a DVD with Xubuntu, Ubuntu, and Kubuntu on it. I just want it to run like an alternate cd.

So I was thinking all I need is a minimal cd and the .deb of xubuntu-desktop, ubuntu-desktop, and kubuntu-desktop.

maybe that would work?

What's the easiest way to do this?

It would be even better if it was all on a CD.

---

### Post by JoshuaRL on 2008-01-02
Check this out:

[http://ubuntuforums.org/showthread.php?t=655781](http://ubuntuforums.org/showthread.php?t=655781)

If you used that it might work.

---

### Post by SOULRiDER on 2008-01-02
How about APTonCD? You could save *buntu-desktop and their dependencies but you would need to have a disk to install the abse system, maybe a server install and then install the other packages over it.

---

### Post by tdrusk on 2008-01-02
I think I'm going to use aptoncd.

Will it recognize metapackages such as xubuntu-desktop?

---

### Post by cecure on 2008-01-02
Using APTonCD is a good idea, if I understand your request correctly though you are looking for a DVD that boots into an Alternative Ubuntu installer and then has the binaries on the same DVD to install Xfce and KDE (so that they are installed after the main system).  

Perhaps you could mount both images and integrate them into one bootable image with mkisofs.  For an example of the mount and mkisofs commands see their man pages and take a look at this [site]("http://pcquest.ciol.com/content/enterprise/2005/105070101.asp"), it provides an example of how to integrate several live cds into one.

---

### Post by Techwiz on 2008-01-02
I like the idea! Could you give a detailed post on how you did it when you succeed? Because I would like to try something like that!

---

