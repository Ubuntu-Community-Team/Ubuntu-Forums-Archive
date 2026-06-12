---
title: "Question on dependencies"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-19
Hi,

I just installed GParted in Ubuntu but since I understood that I cannot use it while in Ubuntu I have removed it. For both install and uninstall I have used Synaptics but I thing bothers me: when I installed GParted, some dependant packages were installed with it. Now I'm uninstalling GParted and those depencies are not uninstalled as well. I understand that there might exist shared dependencies that shouldn't be uninstalled but in this particular case, no other program needs these package because they were first installed with GParted....and now they're left. Not a big deal but does it means that overtime the system gets clogged by "unused" packages? Is this what's called orphaned packages??? I remember having seen an GUI orphan package remover but it was supposed to be risky to use since it could delete gstream packages......that are used by installed programs (why then are gstream package considered orphan...?).

---

### Post by raul_ on 2006-12-19
The other day i read that if you install every single package in synaptic's list, that would take 5 gb of your space. Anyway, did u try the "remove completely" option? Try installing again and the remove it with that option. If that doesn't work, try reinstalling with aptitude, and then remove it again with aptitude, since it seems to do a better job handling dependencies

---

### Post by raul_ on 2006-12-19
And you should check this

[http://www.arsgeek.com/?p=708&print=1]("http://www.arsgeek.com/?p=708&print=1")

EDIT: Just in case, there is a gui for this, called GTKorphan

---

### Post by kilou on 2006-12-19
> **raul_ said:**
> The other day i read that if you install every single package in synaptic's list, that would take 5 gb of your space. Anyway, did u try the "remove completely" option? Try installing again and the remove it with that option. If that doesn't work, try reinstalling with aptitude, and then remove it again with aptitude, since it seems to do a better job handling dependencies

I did remove Gparted with "remove completely" option but it only removed Gparted itself. Installing with aptitude and uninstalling with aptitude again give the same results (probably because the dependencies were yet installed before running aptitude install...)

Is there a way to make synaptics use aptitude instead of apt-get?????

I've looked again at that GTKorphan tool but I don't really like it because it seems to list some important audio and video codecs that are definitely not orphan packages and also I can't find the packages that were installed along Gparted (I don't remember the names but Synaptics installed at least 3 or 4 dependencies to Gparted and GTKorphan list only one package if omitting multimedia codecs and gstreams)

All this is not really important but I like keeping things clean when it comes to OS.

---

### Post by macogw on 2006-12-19
> **kilou said:**
> I did remove Gparted with "remove completely" option but it only removed Gparted itself. Installing with aptitude and uninstalling with aptitude again give the same results (probably because the dependencies were yet installed before running aptitude install...)

Is there a way to make synaptics use aptitude instead of apt-get?????

I've looked again at that GTKorphan tool but I don't really like it because it seems to list some important audio and video codecs that are definitely not orphan packages and also I can't find the packages that were installed along Gparted (I don't remember the names but Synaptics installed at least 3 or 4 dependencies to Gparted and GTKorphan list only one package if omitting multimedia codecs and gstreams)

All this is not really important but I like keeping things clean when it comes to OS.

They could be cross dependencies.  You said no other program needed them when you installed it, but perhaps one of the ones you installed since them is using it.

---

### Post by jvc26 on 2006-12-19
Does sudo apt-get autoremove remove packages which are no longer used? Another approach would be the one here which tells you how to clean up your ubuntu system:
[http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)
The #2 and #5 sections of this may well apply to what you're trying to do.
Enjoy!
Il

---

### Post by kilou on 2006-12-20
> **macogw said:**
> They could be cross dependencies.  You said no other program needed them when you installed it, but perhaps one of the ones you installed since them is using it.

I didn't install anything since Gparted so the installed dependencies are not required for another program since they were not used before.

Thanks for the link Illuviator. However none of the methods seem to remove the dependencies left behind at least in the case of Gparted. A good thing would probably to make Synaptics use aptitude instead of apt-get but I don't know if this is possible and how to do it.

---

### Post by raul_ on 2006-12-20
aptitude, apt-get, Synaptic, Add/Remove Programs...they all do the same thing differently.  did you try "deborphan" instead of GTKOrphan?  I normally use deborphan because gtkorphan seems to list packages that i don't believe to be orphaned

---

