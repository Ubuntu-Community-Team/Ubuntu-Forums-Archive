---
title: "Desar correus electrònics"
date: 2007-10-12
forum: Catalan Team
---

### Post by bratac on 2007-10-12
Bones,

tinc un parell d'adreces de correu pop saturades i en voldria desar els correus en un cd, com ho he de fer, com he de desar els correus amb l'evolution per a que després ho pugui posar en un cd?

gràcies,

---

### Post by papapep on 2007-10-12
L'Evolution té una opció de còpia de seguretat que et crea un fitxer tar comprimit i el pots gravar a un cd o on et plagui.

Ves a Fitxer > Backup Settings (com a mínim a Gutsy amb l'Evolution 2.12.0 ho tinc..).

---

### Post by bratac on 2007-10-13
Gràcies,

jo tinc ubuntu 7.04, m'esperaré a la setmana vinent per actualitzar el sistema a veure si així ho puc desar.  Un cop hagi fet el fitxer .tar, com el podré llegir si mai necessito recuperar un correu? A través de l'Evolution?

fins ara,

---

### Post by CarlesOriol on 2007-10-13
Eps fent una copia i comprimir-la de  /home/usuari/.evolution/mail també fa el fet. (o  /home/usuari/.evolution si també volem les agendes i llibretes adreces)

---

### Post by papapep on 2007-10-13
Tal i com diu el mestre CarlesOriol, fas el mateix amb l'opció que t'he dit jo que fent:

```
tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```

Tot i això, pels usuaris no massa destres amb el terminal, s'agraeix la comanda dins l'Evolution, oi?

Respecte la recuperació dels correus, doncs pensa que estàs fent una instantània del teu correu en aquell moment. Quan recuperis els correus, no te'ls "afegirà" als que tinguis, sinó que els substituïrà. Aleshores et farà falta fer una nova còpia de seguretat dels actuals, abans de restaurar els antics i un cop estiguis de consultar-los tornar a restaurar els actuals matxacant els antics....

M'he sapigut explicar??? :-D

---

### Post by CarlesOriol on 2007-10-13
Eps que també es pot fer amb el nautilus i no és gens dificil!

---

### Post by Ferri on 2007-10-13
Per fer el mateix a Thunderbird, s'ha d'anar al contingut de la carpeta /home/usuari/.thunderbird/????????.default/Mail/
El nom de ????????.default varia d'un ordinador a l'altre (no m'he entretingut a veure de què depèn).

---

### Post by CarlesOriol on 2007-10-13
> **Ferri said:**
> Per fer el mateix a Thunderbird, s'ha d'anar al contingut de la carpeta /home/usuari/.thunderbird/????????.default/Mail/
El nom de ????????.default varia d'un ordinador a l'altre (no m'he entretingut a veure de què depèn).

Amb la insta&#320;lació dels repositoris jo ho tinc a : /home/usuari/.**mozilla-**thunderbird/????????.default/Mail/

---

### Post by Ferri on 2007-10-13
> **CarlesOriol said:**
> Amb la insta&#320;lació dels repositoris jo ho tinc a : /home/usuari/.**mozilla-**thunderbird/????????.default/Mail/
Tal com has deduït, el thunderbird que faig servir jo és el paquet oficial de mozilla. No sabia que el paquet de les fonts fes servir una carpeta diferent.

---

### Post by albert-I on 2007-10-17
Hi ha algun programa que faci una exportació en un fixer pla? on no calgui importar a un programa de correu? amb el thunderbird surt el format mbox i amb el kontact o el kmail, diria que no es pot fer.
Ho dic pq ho trobo una mica estupid tindre que importar milers de missatges per un de sol.
En windows recordo que hi havia un programet que t'ls exportava en text pla i deixaba els correus i individualitzats.

---

### Post by papapep on 2007-10-17
De fet no cal exportar a text pla ja que els fitxers que contenen el correu (parlo de l'Evolution ara) ja són en aquest format. Són una mica pal de consultar ja que el format del missatge es barreja amb el text, però consultar-se es pot consultar.

---

