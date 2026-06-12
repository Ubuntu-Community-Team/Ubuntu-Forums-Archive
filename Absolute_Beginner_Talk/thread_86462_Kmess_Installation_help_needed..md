---
title: "Kmess Installation help needed."
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by clix on 2005-11-05
Hi guyz,

The next thing occurs, ive downloaded Kmess, cause i dont like the other IM deliverd whit synpackage-manager.

Ive downloaded from this site [http://kmess.sourceforge.net/](http://kmess.sourceforge.net/)
the ubuntu package which is called kmess_1.4.1-1_i386ubuntu5.deb

when i extract the package, ive got 3 files, control.tar.gz and data.tar.gz and debian-binary, my next question is, how do i install this app ? :confused:

btw i using UBUNTU whit GNOME.

---

### Post by Ampersand on 2005-11-05
files ending with .deb are installed using dpkg.

Open a terminal, and change directory to the directory you downloaded it to (using the 'cd' command), then run
```
sudo dpkg -i kmess_1.4.1-1_i386ubuntu5.deb
```

Kmess should be available in Synaptic, though... You'll need to enable the universe repository, instructions for this are here: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) .

---

