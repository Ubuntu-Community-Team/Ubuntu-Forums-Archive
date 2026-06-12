---
title: "[SOLVED] No puc entrar a Ubuntu"
date: 2007-06-30
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2007-06-30
Hola amics.
Tinc Ubuntu 7.04 amb 3 usuaris. De cop i volta ara no puc logar cap dels usuaris, tampoc root.
Surt el següent missatge:
"GMD no ha pogut escriure en el vostre fitxer autorització. Aixó vol dir que us heu quedat sense espai al disc o que el vostre directori d'usuari no s'ha pogut obrir per a escriptura."

Amb un Live CD he verificat que el disc està tan sols a la meitat de la seva capacitat.

Cap idea?
Moltes gracies.

---

### Post by CarlesOriol on 2007-07-01
Prova si pots entrar per lina de comandes. (ctr+alt+f1)

Un cop allà fes

sudo chown nomdelusuari:nomdelusuari -R /home/nomdelusuari

a veure si s'arregla.

---

### Post by Miquel Ubuntero on 2007-07-04
LLàstima Carles. No m'ha funcionat. Moltes gracies pel teu interés.
Cap idea més?

---

### Post by crazyserver on 2007-07-04
Bona tarda!

Has pogut entrar per linia de comandes per això?
En cas afirmatiu, ens seria de gran ajuda la sortida que dona si fas "mount"

A mi ja m'havia passat i el meu problema era que el disc es remuntava com a només lectura per errors en el bus de dades.

Sort!

---

### Post by Miquel Ubuntero on 2007-07-05
Si que puc entrar a linea de comandes.
Fent un "mount" hem diu:
/dev/hdc1 on/type ext3 (rw, errors=remount -ro)
/dev/hdc3 on/media/hdc3 type ext3 (rw)

Espero sigui útil aquesta informació.

Moltes gracies.

---

### Post by patrickfromspain on 2007-07-05
proba a fer un sudo apt-get clean.. igual es falta d'espai a la particio

---

### Post by Miquel Ubuntero on 2007-07-07
SOLUCIONAT! 
Gracies patrickfromspain.
A anat be el aptg-get clean, tot i que només tinc en us un 57% del H.D.
Be, l'important és que ja funciona i estic molt agraït.

Gracies a tots. ;)

---

