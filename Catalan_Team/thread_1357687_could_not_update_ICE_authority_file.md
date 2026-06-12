---
title: "could not update ICE authority file"
date: 2009-12-17
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-12-17
Hola.
Tinc Ubuntu 9.10 de fa poc. En posar nom d'usuari i password, abans d'entrar a Ubuntu hem surt aquest missatge: could not update ICE authority file /home/miquel/.ICEauthority

Premo ok i puc entrar i utilitzar Ubuntu. 
No tinc ni idea de que va i si és greu???
Algú en sap res?

Una cosa. Al quadre superior de gnome m'ha desaparegut la icona de conexió de xarxa, de tal manera que no puc triar xarxes wifis. Per sort, la conexió amb cable si hem funciona.

Salutacions, Miquel.

---

### Post by papapep on 2009-12-17
> Hola.
Tinc Ubuntu 9.10 de fa poc. En posar nom d'usuari i password, abans d'entrar a Ubuntu hem surt aquest missatge: could not update ICE authority file /home/miquel/.ICEauthority

Premo ok i puc entrar i utilitzar Ubuntu.
No tinc ni idea de que va i si és greu???
Algú en sap res?

Això és un problema de permisos a la teva /home o específicament amb el fitxer .ICEauthority. Revisa-ho tot plegat. Has de tenir un 755 a /home i un 600 per l'.ICEauthority. Ambdós han de ser del teu usuari i grup.

> Una cosa. Al quadre superior de gnome m'ha desaparegut la icona de conexió de xarxa, de tal manera que no puc triar xarxes wifis. Per sort, la conexió amb cable si hem funciona.


Crec que [tu mateix]("http://ubuntuforums.org/showpost.php?p=8020532&postcount=7") tens la solució.

---

### Post by Miquel Ubuntero on 2009-12-18
Gracies papapep,
ja he solventat lo dels permisos.
També ja "veig" les wifis utilitzant nm-applet.

Només una coseta. Tot hi tindre nm-applet afegit a les aplicacions d'inici, aquest no s'inicia. De tal manera que l'he d'iniciar manualment cada cop que arrenco Ubuntu. No es greu, però hem toca una mica la pera.

En qualsevol cas, moltes gracies.
salut!

---

### Post by papapep on 2009-12-18
Sistema > Preferències > Aplicacions d'inici

---

### Post by Miquel Ubuntero on 2009-12-18
Sí, papapep, tal com havia dit, ja tinc nm-applet a les aplicacions d'inici.
Però no s'inicia.
Ho he de fer manualment, des de terminal.

P.D.: Una cosa més, per si és informació útil: Tampoc tinc el control de volumen i l'indicador de carga de bateria al quadre on també hem falta el gestor de xarxa. Pot ser dic ara una tonteria. Serviria d'alguna cosa reinsta&#320;lar gnome?

---

### Post by papapep on 2009-12-18
Botó de la dreta del ratolí damunt del quadre superior > Afegeix al quadre i hi poses l'applet que més et vingui de gust.

Recordes allò de "un tema, un fil"? :)

---

### Post by Miquel Ubuntero on 2009-12-18
> **papapep said:**
> Botó de la dreta del ratolí damunt del quadre superior > Afegeix al quadre i hi poses l'applet que més et vingui de gust.

Si, gracies, ha ho veig.

Recordes allò de "un tema, un fil"? :)

Ups, tens raó, ho tindré en compte.
Gracies per tot.

---

