---
title: "Problems with Azureus, Limewire, and Java Runtime"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by rj686 on 2005-09-15
I've been following the UbuntuGuide ([http://www.ubuntuguide.org](http://www.ubuntuguide.org)) but i've had problems installing azureus limewire and Java runtime on the breezy badger preview. I did an sudo apt-get update, and what the guide says to add repositories  but it cant find the azureus package or the j2l package? i dont knwo what to do from here guys.

---

### Post by rj686 on 2005-09-15
i found out why the repository sources that the guide lists are different cuz i have breezy preview. Should i add the hoary sources er what should i do?

---

### Post by mlomker on 2005-09-15
Have you tried just changing the name in the repository line to breezy and seeing what happens?  It'd probably work.

You could download j2re direct from Sun and Azureus from sourceforge/freshmeat but having a .deb file makes life simpler.

---

### Post by rj686 on 2005-09-15
[QUOTE=mlomker]Have you tried just changing the name in the repository line to breezy and seeing what happens?  It'd probably work.

You could download j2re direct from Sun and Azureus from sourceforge/freshmeat but having a .deb file makes life simpler.[/QUOTE]
 i think u meant hoary right cuz the sources are set to Breezy restricted rather than Hoary universe.

Another problem.good luck playing multimedia on breezy preview cuz the repositories available dont have have the codecs needed to play media.

---

### Post by rj686 on 2005-09-15
should i change all the repositories to hoary...is it safe to do that?(im using breezy)

---

### Post by Emerzen on 2005-09-16
I have Breezy Preview installed w/ all the Breezy repo's.  I also added Hoary Backport repo's for the multimedia stuff.  I load those repositories, grab what I need,and then turn them off (i.e. I don't upgrade anything w/ them on).  So far I've had no problem adding jre1.5, libdvdcss2, etc...  Azureus works but the autoupdater is borked, so I'm trying to figure out how to fix this.

---

### Post by aysiu on 2005-09-16
I'm using the Hoary backports on the Breezy preview, and... it's going. There are some bumps along the way--some delayed audio, for example, but it works.

---

### Post by rj686 on 2005-09-16
[QUOTE=aysiu]I'm using the Hoary backports on the Breezy preview, and... it's going. There are some bumps along the way--some delayed audio, for example, but it works.[/QUOTE]
 have you had success setting up limewire, i have it installed but nothing happens when i click on the icon, or what about java for like online games? i have jre1.5 but i still cant play the games

---

