---
title: "How to install Snort"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by Rollo Tamasi on 2006-02-21
Hi guys, i have just downloaded a tar.gz file onto my desktop from snort.org, how do i go about installing it? Thanks

---

### Post by o_fortuna on 2006-02-21
[QUOTE=Rollo Tamasi]Hi guys, i have just downloaded a tar.gz file onto my desktop from snort.org, how do i go about installing it? Thanks[/QUOTE]
Is snort not in the repositories? It's always easier to get it from synaptic or on the command line, Applications-->Accessories-->Terminal and type:
```
sudo apt-get install snort
```
But, if you want to install .tar.gz files, there are generally install procedures on the page you got it from. I personally don't use them, although I've heard that alien (find it in synaptic) can install it like this from the command line (if the .tar.gz is on the desktop):
```
cd Desktop
sudo alien FILE_NAME.tar.gz
```
Although, it may or may not work. A .deb package is always better.

---

### Post by tadashi on 2006-02-21
It might be best to ask that question at the Snort forums:
[http://www.snort.org/reg-bin/forums.cgi](http://www.snort.org/reg-bin/forums.cgi)

They had some install manuals on their web site also.

---

### Post by Rollo Tamasi on 2006-02-21
hi
i tried sudo apt-get install snort but i got an error stating :
could not find package snort

so i tried the cd Desktop / sudo alien FILE_NAME.tar.gz method and it generated a .deb file on my desktop with an orange padlock on it
any ideas?

---

### Post by celloandy on 2006-02-21
As someone else already said, your best bet is to use the Ubuntu repositories to do your installations. Installing using alien and the downloaded package may work, depending on whether or not the package you downloaded is a binary package or a source package, but it's not the recommended method. Snort is, indeed, available for Ubuntu, but it's in the "Universe" repository (so it's a community-maintained package), and you'll need to enable that repository before you can install it using apt.

Take a look at [https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto") for more information on adding repositories, and at [https://wiki.ubuntu.com/SynapticHowto]("https://wiki.ubuntu.com/SynapticHowto") for instructions on using a graphical package management utility to actually install your program once you've enabled Universe.

Andrw

---

