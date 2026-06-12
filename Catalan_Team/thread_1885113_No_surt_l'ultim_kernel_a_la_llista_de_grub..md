---
title: "No surt l'ultim kernel a la llista de grub."
date: 2011-11-22
forum: Catalan Team
---

### Post by fvilaubi on 2011-11-22
Amb la darrera actualització del 11.10, va arribar el kernel 3.0.0-13.
En el moment d'actualitzar em va fer una pregunta capciosa: "vol el fitxer d'inici modificat per vostè, o prefereix el nou de la versió?" vaig clicar sobre el selector que deia "mostra'm les diferències" (jo no soc conscient d'haver modificat això), i "endavant".
Va continuar l'actualització sense cap missatge i sense ensenyar-me les diferències.

Ara el que observo es que amb synaptics veig que tinc el kernel x-13 instal·lat, però no surt a la llista d'inici del gurb.

He fet des d'una terminal grub-update i m'ha deixat el "menu.lst" igual.

Com puc actualitzar la llista per que reculli el kernel 3.0.0-13 ?

---

### Post by orestesmas on 2011-11-24
Prova de fer un "sudo update-grub". Explora tots els nuclis i refà la llista.

---

### Post by wgarcia on 2011-11-24
A no ser que tinguis una instal·lació molt antiga, el menú.lst no s'utilitza ja més per al grub. Quina versió es veu quan inicies l'ordinador a dalt del tot de la llista de nuclis?

---

### Post by fvilaubi on 2011-11-24
Ja ho he fet hi em deixa el menu.lst igual. Veig que ha treballat per que la data del fitxer menu.lst s'actualitza.

---

### Post by fvilaubi on 2011-11-24
El 3.0.0-12. Fins aqui sempre ha actualitzat correctament. Cert es que vinc actualitzant les versions pot ser des de la 9.10 sense fer en cap cas una instal·lació des de zero.
Tinc el nucli 3.0.0-13 baixat i instal·lat segons Synaptic però no em surt a la llista de nuclis.
Crec que va ser per la pregunta de si volia el meu fitxer (segons deia modificat encara que jo no en soc conscient) o l'estàndard de la versió 3.0.0-13.
Vaig clicar sobre el radio buton de "mostram diferències" i només em va semblar veure el botó "d'endavant" actiu i el vaig clicar. 
En cap moment em va ensenyar les diferències, i va acabr l'actualització sense errors.
Ha estat al tornar a engegar que m'he fixat que era el nucli anterior (12) i que el nou (13) no estava a la llista.

---

### Post by fvilaubi on 2011-11-24
Perdoneu,
al clicar sobre "quick reply" de l'entrada m'ha semblat que quedaria ordenat!.
La meva primera resposta es a Orestes (He fet el grub-update), i la segona es a wgarcia El nucli 12 i no el 13.

---

### Post by wgarcia on 2011-11-26
El que volia dir és la versió del grub, no del nucli, i pel que expliques tens encara la versió 1, no la versió 2 que és la que s'utilitza ara. 

Jo crec que seria recomanable actualitzar a la versió 2, sempre fent primer una còpia de totes les teves dades per si un cas.

---

### Post by fvilaubi on 2011-11-28
> **wgarcia said:**
> ... seria recomanable actualitzar a la versió 2.... 

Ja he trobat un document a Ubuntu de com migrar de grub a grub2... però si al menu.lst no surt el nucli 13, el trobarà el grub2?

---

### Post by wgarcia on 2011-11-29
En principi sí, la instrucció "update-grub" troba tots els nuclis i prepara els fitxers perquè surtin al menú inicial,

Walter

---

