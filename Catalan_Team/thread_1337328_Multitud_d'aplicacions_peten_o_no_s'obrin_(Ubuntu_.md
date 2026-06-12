---
title: "Multitud d'aplicacions peten o no s'obrin (Ubuntu 9.10)"
date: 2009-11-25
forum: Catalan Team
---

### Post by carevolta on 2009-11-25
Bona vesprada. Després de resoldre els inconvenients amb el so, torne a tenir entrebancs, i ben grossos, per treballar amb el Karmic Koala. Ignore si té relació, però tot ve d'anit, després de fer una actualització un munt d'aplicacions peten (adjunte imatges de Totem, Pidgin, Empathy) i altres ni tan sols s'engeguen (Centre de programari, Rhythmbox, aMSN). No sé a què respon, perquè hi ha aplicacions pròpies de Gnome/Ubuntu i altres que no ho són i se m'escapa si hi ha alguna vinculació entre elles. Lamente no poder ser més precís i oferir més informació per ara.
Tinc un processador AMD Sempron(tm) 2600+ i 256 RAM (bastant rudimentari, per tant)
Gràcies per l'atenció

---

### Post by carevolta on 2009-11-25
Bona nit. Ja sé que el meu missatge sonava estrany, però la solució ho és més encara per a mi. Googlejant he trobat consultes d'alguns usuaris  recordant que els havia ocorregut després d'instal·lar l'editor de vídeo Kdenlive, just el que havia fet jo. He provat i, en efecte, després d'eliminar qualsevol rastre, és a dir, ordenant "purge" i també "sudo apt-get autoremove lives" totes les aplicacions han tornat a funcionar de meravella. 
Qüestió resolta. Bo, si algú té temps i coneixements per explicar quina influència té el maleït editor en la resta d'aplicacions ho agrairia.
Gràcies de nou!

---

### Post by sordoman on 2009-11-26
Increible!!! funciona!! 
```
sudo aptitude purge kdenlive
```

i tot solucionat.

algu sap perquè, a mi fins i tot el centre de programari s'apagava sol!!

moltes gracies !!):P

---

### Post by orestesmas on 2009-11-26
Per treure'n l'entrellat, podríeu si us plau copiar aquí el resultat de l'ordre:
```

apt-cache show kdenlive

```

També pot ser útil saber si esteu fent servir repositoris no oficials. El Kdenlive, com la majoria d'editors de vídeo, depèn de multitud de llibreries multimèdia (mlt, libavformat...) que també utilitzen altres aplicacions. Si heu usat repositoris no oficials que han instal·lat versions més noves d'aquestes llibreries, podria ser que la resta de programes tinguessin problemes per això.

---

### Post by sordoman on 2009-11-26
Esclar que si, aqui el tens
```

desktop:~$ apt-cache show kdenlive
Package: kdenlive
Priority: optional
Section: universe/graphics
Installed-Size: 2780
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Patrick Matthäi <pmatthaei@debian.org>
Architecture: i386
Version: 0.7.5-1ubuntu1
Replaces: kdenlive-data (<< 0.7)
Depends: kdebase-runtime (>= 4:4.2.96), kdelibs5 (>= 4:4.2.96), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libmlt++2, libmlt1, libqt4-dbus (>= 4.5.1), libqt4-network (>= 4.5.1), libqt4-svg (>= 4.5.1), libqt4-xml (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libstdc++6 (>= 4.1.1), kdenlive-data (= 0.7.5-1ubuntu1), melt, ffmpeg
Recommends: swh-plugins, dvgrab, frei0r-plugins, recordmydesktop, dvdauthor, genisoimage
Filename: pool/universe/k/kdenlive/kdenlive_0.7.5-1ubuntu1_i386.deb
Size: 1024944
MD5sum: 04a6795d61d177486d457f434e62b54e
SHA1: 24517e86d3fe4d0fe0884ecddce70a0f749efade
SHA256: 84a569ccdc251255ec87f8cbc25ea696009dee2f2dd80c4341c1c934da6341af
Description: a non-linear video editor
 Kdenlive is a non-linear video editing suite, which supports DV, HDC and much
 more formats.
 It main features are:
  Guides and marker for organizing timelines
  Copy and paste support for clips, effects and transitions
  Real time changes
  Firewire and Video4Linux capture
  Screen grabbing
  Exporting to any by FFMPEG supported format
Homepage: http://www.kdenlive.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu


```

A veure si en treiem l'entrellat.

Moltes gràcies):P

---

