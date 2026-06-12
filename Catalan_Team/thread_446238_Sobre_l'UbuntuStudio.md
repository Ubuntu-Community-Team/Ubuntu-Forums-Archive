---
title: "Sobre l'UbuntuStudio"
date: 2007-05-16
forum: Catalan Team
---

### Post by FloiT on 2007-05-16
Hola senyors/es, 
sóc un novell en això de l'ubuntu, però fa setmanes que em vaig instal·lar el Feisty Fawn i tot bé. L'altre dia vaig veure que existeix aquesta versió "multimèdia" que es diu UbuntuStudio... el recomaneu? O amb el "normal" i instal·lant certs paquets ja n'hi ha prou?
Per cert, si volgués instal·lar l'UbuntuStudio hauria de desinstalar el que tinc (el "normal") i instalar l'Studio?

gràcies

---

### Post by CarlesOriol on 2007-05-17
Per instal·lar tot el que porta l'ubuntu studio sols cal que afegeixis als repositoris:

deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

Per executar programes de tractament d'audio en temps real et caldrà insta&#320;lar el nucli lowlatency (linux-lowlatency) que ja tens en els repositoris actuals.

Pel tema de les reinsta&#320;lacions jo et recomano una bona copia de la carpeta /home/ i allà tens totes les teves dades i configuracions dels programes. És aconsellable també de tenir separada aquesta carpeta en una altra partició així qualsevol canvi de sistema o de versió no t'afecta.

---

