---
title: "apt-get vs aptitude"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by crossev on 2006-02-17
Is there a difference between these two tools for installing applications?

---

### Post by aysiu on 2006-02-17
Yes.
Aptitude "remembers" what you've installed, so it's easier to uninstall things later.

See an example [here](http://www.ubuntuforums.org/showpost.php?p=659085&postcount=19).

---

### Post by mushroom on 2006-02-18
While it is better than apt-get concerning dependencies, sometimes it's too good. I tried to remove ubuntu-desktop with aptitude and it tried to remove the entire os rather than just the metafile.

---

### Post by Jucato on 2006-02-18
aptitude is a front-end package manager for apt-get, just like synaptic, adept, etc. I rarely use aptitude thought. Synaptic also has a history of its installs. However, it does not uninstall it the way Aptitude does.

I tend to use apt-get when I want/need a comman-line interface to copy/paste stuff and Synaptic for simpler installs or when I want a log of my installs. Different strokes for different folks. Use what you want/need. They practically do the same things. :D

@aysiu: I haven't tried using aptitude, but my question is this: during the installation of xubuntu metapackage, libesd0 was removed and replaced by something else. Will Aptitude remember this and reinstall libesd0 when I uninstall xubuntu?

---

### Post by aysiu on 2006-02-18
[QUOTE=Fenyx]
@aysiu: I haven't tried using aptitude, but my question is this: during the installation of xubuntu metapackage, libesd0 was removed and replaced by something else. Will Aptitude remember this and reinstall libesd0 when I uninstall xubuntu?[/QUOTE] No idea. To be truthful, I've never actually used aptitude.

---

### Post by Jucato on 2006-02-18
hehehe! neither have I. was just being curious. :D

---

