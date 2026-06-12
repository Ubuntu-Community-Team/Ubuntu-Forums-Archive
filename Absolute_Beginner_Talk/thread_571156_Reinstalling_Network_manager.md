---
title: "Reinstalling Network manager"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2007-10-09
Hi guys i think my network manager keeps crashing>..
How do I reinstall my network manager and what command do i need? PS I DO NOT HAVE INTERNET BECAUSE my ubuntu os can't detect my ethernet card

Pls list the steps out. Will i be needing the Ubuntu install cd?

---

### Post by kevdog on 2007-10-09
Network Manager isnt going to help if the OS truly cant identify your network card.

Type 
lshw -C network
at command prompt.  Is your ethernet card listed??? Does it have a driver listed???

---

