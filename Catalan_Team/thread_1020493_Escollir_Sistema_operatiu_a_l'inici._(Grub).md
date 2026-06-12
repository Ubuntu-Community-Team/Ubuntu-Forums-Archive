---
title: "Escollir Sistema operatiu a l'inici. (Grub)"
date: 2008-12-24
forum: Catalan Team
---

### Post by Hecturt on 2008-12-24
Hola de nou!
He aconseguit tenir un portàtil amb l'Ubuntu i el Windows funcionant correctament. Ara però, tinc un nou dubte.
El cas es que quan inicio l'ordinador em surt una pantalla en negre per tal que esculli el SO amb el que vull treballar. Aquesta pantalla, si no ho tinc mal entès pertany a l'aplicació Xclient de Linux. Aquí, a part de poder escollir entre un SO o l'altre em surten altres opcions que mai voldré utilitzar (diferents versions del nucli, crec). Les meves preguntes son:
- Algú sap si existeix l'Xclient en entorn gràfic?
- Es pot configurar l'Xclient per tal que només mostri les opcions de Windows i Ubuntu?

Gracies per endavant !

---

### Post by oriolsbd on 2008-12-24
Hola. El menú de què parles està gestionat pel gestor d'arranc. Normalment és el grub (i serà així si has fet la instal·lació "normal"). Aquestes opcions es gestionen des del fitxer /boot/grub/menu.lst. De tota manera, millor no tocar-lo de manera directa si no saps ben bé què fa cada opció.

Hi ha diversos programes que et permeten gestionar aquest fitxer des d'un entorn gràfic. Per exemple, "startupmanager" o "kgrubeditor" (tots ells instal·lables des de Synaptic). Qualsevol dels dos està molt bé, i et permetrà fer el que demanes.

Salut!

---

### Post by tanreb20 on 2008-12-24
el que tu dius no es el xclient, es una cosa anomenada grub.

Aquest programa s'instala apart del linux, en el lloc que primer es llegeix del disc dur (MBR o MBA no ho se).

Per poder fer que només es mostrin le sopcions de windows y linux has de fer el seguent.

1- editar l'arxiu /boot/grub/menu.lst -> opcions de carrega.

per fer aixo necessites fer-ho com a sudo, pero primer per seguretat crea un backup.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

sudo gedit /boot/grub/menu.lst

alla veuras al final de l'arxiu les diferents coses que t'apareixen al arrencar. modifica el que vulguis pero jo deixaria la opcio recovery, no esta de més per si mai et falla alguna cosa.

Pel qeu fa al gestor grub grafic si que existeix, es diu gfxgrub, u pots buscar al google.

---

### Post by indiosincracia on 2008-12-24
com indiquen els companys és el grub.

>em surten altres opcions que mai voldré utilitzar (diferents versions del nucli, crec)

no cridis al mal temps, no crec que sigui una bona idea deixar el grub només amb aquestes dos opcions, efectivament son diferents versions del nucli (kernel), es pot donar el cas de que en una nova actualització del kernel alguns controladors deixin de funcionar, i hagis d'iniciar l'ordinador amb la versió anterior del kernel, 

si edites aquest fitxer /boot/grub/menu.lst
en aquest apartat pots modificar el temps en el que es mostra el grub

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

els colors etc, però no tocaria els diferents kernels i els recovery's

per entrar al grub ja saps que has de premer la tecla Esc just després de que carregui la bios.
Salut.

---

### Post by Hecturt on 2008-12-24
Ja t'entenc però es que resulta que l'ordinador en quëstió no es meu sino de la meva sogra i em fa por que arrenqui la maquina amb alguna opció no desitjada. L'ideal seria que el grub tingues un aspecte gràfic (com el d'escollir usuari del Windows) i que només deixes triar entre Windows o Ubuntu. Es per això que busco alguna aplicació que em doni aquesta possibilitat. L'aplicació hauria de ser configurable un cop entrat al sistema com a usuari administrador o tenir alguna opció extra per visualtzar els tipus d'arrencada poc habituals. 
S'ha de tenir en compte que la gent que no en sap massa d'informàtica els hi fa molt respecte una pantalla negre amb text blanc tipus consola!

---

### Post by CarlesOriol on 2008-12-25
Existeix un gfx grub ([http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/](http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/)). Però tindras un munt de problemes a l'hora d'actualitzar i sobretot als canvis de versió.

Les opcions que t'han dit els companys son bonissimes i el teu usuari no haurà de veure cap pantalla de text. (modificant el menu.lst)

Però en el pitjor dels casos el comentari del respecte a una pantalla negra és una apreciació que crec que pot estar equivocada. (Posa un l-user davant una pantalla de grub amb un teclat davant d'un que és nou amb el ratolí o amb el comandament de la wii i veuras quina opció entenen més ràpidament). (A més sempre pots canviar els colors al menu.lst)

---

