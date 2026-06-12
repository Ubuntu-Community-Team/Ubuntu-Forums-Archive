---
title: "How can I make a Debian package to install my theme?"
date: 2009-11-05
forum: Art &amp; Design
---

### Post by Zachs Kappler on 2009-11-05
I know it sounds weird, but I would like to know what I have to do to build a Debian package for installing a theme for Gnome. I've seen it done in the repos but have no idea how to dissect them and learn. The only tutorials on package building require a source program for it to work from but I'm not repackaging a tarball!

I've been here: [http://www.debian-administration.org/article/Rolling_your_own_Debian_packages_part_1]("http://www.debian-administration.org/article/Rolling_your_own_Debian_packages_part_1")

and here: [http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)

Any help or templates for this kind of package would be greatly appreciated.

---

### Post by unamanic on 2009-11-05
perhaps you could:
apt-get source gnome-theme-gilouche

then poke around the metatheme-gilouche directory that it produces.  See if you can modify it to suit your needs.

---

### Post by JBAlaska on 2009-11-05
Maybe [this](http://ubuntuforums.org/showthread.php?t=51003) will help.

---

### Post by Zachs Kappler on 2009-11-06
Thanks for your help, I found a program called Debian Package Builder that will handle most of it, only problem is what I should have for the scripts. I want to install a sound set to /usr/share/sounds/gladix, images to /usr/share/pixmaps/gladix, and some GDM themes to usr/share/gdm/themes. How should I go about writing them or would they even be needed?


Off Topic-ish: About the sound theme, I know in Ubuntu there is a drop down menu to choose themes from, but I want to know the naming scheme for the lists it pulls from. Anybody know where to look that up?

---

