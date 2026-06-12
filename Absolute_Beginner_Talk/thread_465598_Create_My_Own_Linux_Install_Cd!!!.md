---
title: "Create My Own Linux Install Cd!!!"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-06-05
I was wontering if it is easy (or possible) to create an installation cd...
every time i reformat my computer (once or twice a week). i always re install the same programs, files, and bookmarks... EVERY TIME! is there a whay i can install everything, then make an installation cd out of that for whenever i need to reformat...
ANY HELP!!! PLEASE!!!

---

### Post by Nekiruhs on 2007-06-05
[Reconstructor]("http://reconstructor.aperantis.com/") may be just what you need.
BTW, If I may ask, what are you doing that requires you to reformat so quickly?

---

### Post by Cappy on 2007-06-05
You should just keep make a separate HOME directory so that when you reinstall Linux you won't lose your bookmarks/files. It won't keep installed programs but you could make a simple shell script to reinstall them all, either by using apt-get or downloading the debian files to your home directory and using just a "dpkg -i *.deb"

---

### Post by kevin11951 on 2007-06-05
i reformat alot, because i mess with xorg.conf, resolution settings, i install new software for no reason, and all those thing just kill it kinda fast.

---

### Post by kevin11951 on 2007-06-05
any other software i can use to do what i wanted, reconstructer (or whatever) didnt work. it didnt even install right.

---

### Post by SgtDude on 2007-06-06
aptoncd will build a CD or DVD with all the programs you've downloaded through apt-get or Synaptic or the "Add/Remove" button in the Applications menu.  Maybe that's what you're looking for.  Or, if you just want to back up your system periodically so you can go back if you mess up, try [Ghost For Linux]("http://sourceforge.net/projects/g4l").

---

