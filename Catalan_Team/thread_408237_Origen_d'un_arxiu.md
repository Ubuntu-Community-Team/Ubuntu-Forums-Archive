---
title: "Origen d'un arxiu"
date: 2007-04-13
forum: Catalan Team
---

### Post by CarlesOriol on 2007-04-13
Com podem saber quin paquet ha instal·lat un arxiu?

---

### Post by marcoil on 2007-04-13
```
$ dpkg-query --search *ruta completa de l'arxiu*
```

Hi ha molts d'arxius que no donen cap resultat, però: Configuracions, alternatives...

---

### Post by CarlesOriol on 2007-04-13
Si hi ha dues formes més que m'han dit l'IRC:

arualavi: dpkg -S

toniher: apt-file search (Encara que aquesta darrera no he aconseguit que em funciones.)

---

### Post by patrickfromspain on 2007-04-15
amb synaptic, si poses propietas d'una paquet instalat, veuras que t'ha instalat i a on.

EDIT: no he dit res.. ja he vist que habia entés malament la pregunta, perdona.

---

