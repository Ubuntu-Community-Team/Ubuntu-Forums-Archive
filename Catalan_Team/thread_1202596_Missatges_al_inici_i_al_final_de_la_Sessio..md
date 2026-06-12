---
title: "Missatges al inici i al final de la Sessio."
date: 2009-07-02
forum: Catalan Team
---

### Post by MiquelBLL on 2009-07-02
Hola tinc una serie de missatges que em surten des de fa un temps i no se com es que surten. Tinc el 9.04 convertit a Ext4, AMD64 nVidia 6100. L´ordinador funciona be, nomes s´em penja de tant en tant al esborrar fitxers, es queda el ratoli fixe i no respon cap tecla tinc que apagar amb el boto pero per lo altre em funciona be.

Els missatges son aquestos:

Mentre s´inicia em diu:

[I]WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc. It will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat. It will be ignored in a future release.


grep: /usr/lib/kde4/etc/kde4/kdm/kdmrc:  No such file or directory
Not starting K Display Manager (kdm-kde4): it not the default dispaly manager.
[/I]
Al tancar em diu:

[I]Warning:Screen isn´t composited. Please run compiz (-fusion) or another compositing manager
[/I]

Gracies per endavant.

---

### Post by akyra on 2009-07-03
Els missatges de Nvidia i les oss entenc que estan relacionats amb els drivers, però només són advertencies, el de compiz a mi també em surt al tancar l'ordinador, no he trobat que hi hagi cap problema, inclus té com la pestanya perquè no torni a sortir, però no dona temps a seleccionar-la.

Has fet un upgrade de versió o una instal·lació neta. Si és un upgrade poder queden fitxers de configuració que no s'utilitzen.

Per altre banda suposo que tens instal·lat el compiz.

Salut

---

### Post by CarlesOriol on 2009-07-04
El del kdm es degut a una insta&#322;lacio de kde que no s'usa de forma predeterminada (uses gdm o no uses kde). I son sols avisos.

I el darrer un missatge de l'avant-window-navigator. (pots canviar a mode de video sense efectes en una sessio activa i desactivar aquest missatge)

---

### Post by MiquelBLL on 2009-07-04
Ok son advertencies, pero m´agradaria arreglar-ho no se quins fitxers poden haver quedat. Si, he fet una actualitzacio de la 8.10.
Aixo del KDM m´agradaria desactivar-ho tambe.
Sobre lo del avis al tancar l´ordinador si, al treurer el efectes surt el missatge i pus fer que no es mostri de nou pero el que no entenc es el perque surt.
A vegades suposo que fen una instal.lacio des de 0 pot anar be, pero no tinc el HOME en una particio a banda i a mes tinc molts programes instal.lats i seria una feinada tornar-ho a tenir tot igual a part de per exemple tinc correu pop i avans tambe tindria que fer un backup, de fet de la musica fotos etc ja tinc copia  i a mes vaig fer una copia amb el clonezilla. L´ordinador es bastan nou, te poc mes de 2 anys i em va be de moment.
Gracies.

---

### Post by PatrickVogeli on 2009-07-04
els d'nvidia i oss-compat els pots arreglar fent el que diu l'avis, que es canviar el nom afegint-hi la extensió .conf

salut

---

### Post by MiquelBLL on 2009-07-05
Ok, vui canviar el nom dels arxius ´nvidia-kernel-nkc´ i ´oss-compat´ i afegir l´extensio ´.conf´ el que passa es que no tinc permisos, no domino aixo dels permisos, ho  he inentat amb ´rename oss-compat oss-compat.conf´ pero no em funciona. Com puc reanomenar aquets 2 fitxers?

---

### Post by papapep on 2009-07-05
[https://wiki.ubuntu.com/CatalanTeam/Recursos/IntèrpretComandes](https://wiki.ubuntu.com/CatalanTeam/Recursos/IntèrpretComandes)

Més concretament:

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Manipulant%20fitxers](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Manipulant%20fitxers)

i

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Permisos](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Permisos)

---

### Post by sianeu on 2009-07-05
Pots iniciar el nautilus com administrador

> sudo nautilus

Navega fins els fitxers i els canvies el nom.

Salut

---

### Post by papapep on 2009-07-05
No és recomanable, de fet és perillós, executar aplicacions gràfiques amb el *sudo*. Cal fer-ho amb el **gksudo**, invocant-lo des de la finestra d'execució que surt en fer Alt+F2.


```
gksudo nautilus
```

---

### Post by sianeu on 2009-07-05
Gracies papapep, me l'apunto ;)

Salut

---

### Post by MiquelBLL on 2009-07-09
Hola, gracies per l´ajuda, vaig canviar el nom seguin les indicacions que diu a wiki i posan un root temporal amb un ´su´ vaig canviar el nom amb ´mv´. Ara he vist que fen sudo nautilus o gksudo nautilus es mes facil, el fet es que els misatges d´advertencia al inici ja no em surten, em surt nomes lo del referen al KDE que no se com treureu. 
Gracies de nou per l´ajuda.
Miquel.

---

