---
title: "No carrega Kubuntu"
date: 2012-02-21
forum: Catalan Team
---

### Post by socderafel on 2012-02-21
Hola de nou a tots!
M'he decidit a tornar al mon de Linux, i em trobe que al instal.lar l'ultima versió de Kubuntu, no m'inica com cal. 
Es queda a una pantalla amb missatges (la majoria l'ok), i no arriva a carregar l'entorn gràfic. Si faig un ctrl + alt + F6, em demana usuari i contrasenya, però en mode "consola".
No em dona cap tipus de problema durant l'instal.lació, per el que no sé que pot ser. El Live CD el carrega perfectament i puc utilitzar-lo sense problemes, però si instale, res de res...

---

### Post by wgarcia on 2012-02-21
Sembla un problema de manca de controlador per a la targeta gràfica. Segons el que expliques s'ha instal·lat bé, però a l'hora d'arrencar el sistema no acaba d'iniciar-se bé. 

Per poder saber exactament què està passant es necessitaria més informació, per exemple quina targeta gràfica té l'ordinador. 

Però una cosa que pots fer és entrar en "mode segur" (no me'n recordo ara com ho posa a la pantalla inicial), i veure si t'ofereix alguna opció per instal·lar alguna cosa més relacionada amb l'entorn gràfic.

---

### Post by socderafel on 2012-02-21
> **wgarcia said:**
> Sembla un problema de manca de controlador per a la targeta gràfica. Segons el que expliques s'ha instal·lat bé, però a l'hora d'arrencar el sistema no acaba d'iniciar-se bé. 

Per poder saber exactament què està passant es necessitaria més informació, per exemple quina targeta gràfica té l'ordinador. 

Però una cosa que pots fer és entrar en "mode segur" (no me'n recordo ara com ho posa a la pantalla inicial), i veure si t'ofereix alguna opció per instal·lar alguna cosa més relacionada amb l'entorn gràfic.

La targeta es una Nvidia 5600, i no he tingut mai cap problema amb cap distribució de Linux... pero jo també havia pensat que eixe fos el problema. 
Entonces la solució que m'indiques es instal.lar en mode segur, o una volta instalat, premer alguna tecla per a entrar en mode segur, a l'estil Windows?

---

### Post by wgarcia on 2012-02-21
El que passa és que encara no està clar en quina etapa estàs. Se ha instal·lat i no arrenca l'entorn gràfic, o no s'ha arribat a instal·lar i queda penjat en algun lloc de la instal·lació?

---

### Post by socderafel on 2012-02-21
Perdó, no ho havia dit...
He acabat d'instalar ja (i segons el missatge, correctament).
Per cert, ho he provat 2 voltes. La primera marcant les actualitzacions i els paquets de tercers, la segona sense marcar res.

---

### Post by wgarcia on 2012-02-22
En aquest cas, reps una pantalla inicial per iniciar l'Ubuntu o no? (aquesta pantalla inicial es diu Grub)

---

### Post by socderafel on 2012-02-22
No, no m'apareix el grub... 
Ja he utilitzat Linux altres voltes, aixi que més o menys sé per on vaig, igual a l'instalació no seleccione la partició correcta per al grub?
tinc 2 discs durs, un de 500 Gb on tinc les dades personals, i un altre de 150 Gb, amb una partició de 6 GB (swap), i la resta per a kubuntu. A l'instalació seleccione aquest disc dur per a que instale el grub, sense especificar cap partició.

---

### Post by wgarcia on 2012-02-22
Pel que expliques sols tens instal·lat el Kubuntu, no tens cap altra sistema operatiu, això explicaria que no es mostri la pantalla inicial del Grub.

Doncs el que has de fer és prémer la tecla Majúscules (Shift) just després d'iniciar l'ordinador, i això et mostrarà aquesta pantalla inicial. Hauries de veure aquí una opció per entrar al Kubuntu en "mode segur" o alguna cosa així. Selecciona aquesta opció i mira si pots instal·lar el controlador propietari de Nvidia amb les opcions de sistema del Kubuntu, potser t'ofereixi abans d'entrar a l'escriptori opcions per reconfigurar la gràfica, també pots provar això.

---

### Post by socderafel on 2012-02-22
Ara estic escrivint ja desde Kubuntu, entrant segons m'has explicat... pero ara com puc solucionar el tema de la targeta gràfica?

---

### Post by wgarcia on 2012-02-22
Ara necessitaríem algun usuari de Kubuntu que ens donés una mà, però bàsicament al menú Sistema, ha d'haver-hi per algun lloc una opció que digui "Controladors addicionals" o alguna cosa així. Aquí hauries de mirar si el sistema t'ofereix habilitar algun controlador addicional per a la targeta NVIDIA.

---

### Post by jmaspons on 2012-02-29
El programa que comenta en wgarcia és a Sistema > Controladors addicionals.

Em sembla que en els primers passos de la instal·lació hi ha una opció per triar si instal·lar programari de tercers que activa els repositoris multiverse. Aquesta opció em sembla que instal·la drivers privatius i paquets per llegir formats restrictius (mp3, flash, etc). Quan carrega el liveCD deu utilitzar tot el què té disponible però si no ho especifíques només instal·la programari lliure.

Salut!

---

