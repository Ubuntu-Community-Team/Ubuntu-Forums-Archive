---
title: "Impressora desapareix?"
date: 2010-08-11
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2010-08-11
Bones.
De tant en tant, i no sé per quin motiu. A *Sistema - Administració - Impressió*, no hi trobo les impressores insta&#320;lades. Aleshores, tampoc em funciona aquest web [http://localhost:631](http://localhost:631) que serveix per gestionar les impressores insta&#320;lades.
Més tard, en reiniciar el pc, ja torno a tindre les impressores instal·lades i funcionant sense problemes.

Sembla com si, eventualment, em faltes "quelcom" o "algun servei d'impressió". Pot ser dic rucades?

Però, no ser què mirar?

Gracies.

---

### Post by kimet on 2010-08-11
Es possible que no es carregui d'inici el dimoni de cups.

Quant et passi el pots iniciar manualment amb la comanda: ```
sudo cupsd
```

Salut.

---

### Post by Miquel Ubuntero on 2010-08-11
L'has encertat de ple, Kimet. Gracies.
Just ho acabo de fer.
el tema ara és, per què eventualment no s'inicia. Tot i què, de moment, ja se com iniciar-ho.
Gracies de nou.
Salut!

---

### Post by kimet on 2010-08-11
Pot ser un problema en la carrega d'scripts d'inici, organització dels mateixos o l'arrencada de serveis en paral.lel (concurrency).

Per reorganitzar l'arrencada de processos pots llegir sobre insserv i usar amb seny i sota la teva responsabilitat. ;)

Si estas usant un processador d'un sol nucli pot ser que es sol.lucioni deshabilitant la concurrencia, canviant a /etc/init.d/rc CONCURRENCY=makefile (o lo que hi hagi) per CONCURRENCY=none

Salut.

---

### Post by Miquel Ubuntero on 2010-08-11
Hola Kimet.
Lo del CONCURRENCY ja ho tenia a "none".
Lo del insserv, preereixo no arriscar.
Ja m'apanyo amb sudo cupsd
gracies.

---

### Post by kimet on 2010-08-14
Per casualitat he vist aquest fil...
[http://ubuntuforums.org/showthread.php?t=1552359](http://ubuntuforums.org/showthread.php?t=1552359)

La sol.lució que ofereix en Morbius1 podría servir-te.

Salut.

---

### Post by Miquel Ubuntero on 2010-08-20
Gracies Kimet.
M'ha funcionat.
SOLVED!):P

---

