---
title: "Inici de sessio en kde"
date: 2007-03-14
forum: Catalan Team
---

### Post by CarlesOriol on 2007-03-14
Sabeu quin és l'equivalent en kde del gestor de sessions en gnome? o un arxiu de seqüencies que s'executi a l'iniciar la sessió d'usuari?

---

### Post by orestesmas on 2007-03-14
> **CarlesOriol said:**
> Sabeu quin és l'equivalent en kde del gestor de sessions en gnome? o un arxiu de seqüencies que s'executi a l'iniciar la sessió d'usuari?

Gestor de sessions? No deus voler dir el KDM, oi? No... el KDM només és el gestor d'accés.

Al centre de control del KDE hi ha una part que s'anomena "gestor de la sessió", però em sembla que tampoc cerques això.

Crec que ho trobaràs remenant per /etc/kde3/kdm/

Orestes.

---

### Post by CarlesOriol on 2007-03-14
no, no gràcies Oreste ... de fet sols em calia saber on posar els programes per autoexecutar en l'entrada d'usuari dins de kde.

En gnome hi ha un gestor que s'anomena gnome-session-properties  .

La resposta al meu dubte era:

En kde cal referenciar o crear seqüencies a la carpeta:

/home/nomusuari/.kde/Autostart

Gracies en qualsevol cas

---

