---
title: "Aplicacio Java que no es veu amb efectes"
date: 2009-01-07
forum: Catalan Team
---

### Post by trinkus on 2009-01-07
Hola,

Tinc una aplicacio instalada que crec que s'executa amb Java. Si tinc els efectes d'escriptori activats no es veu el contingut (apareix el requadre per fer-la anar pero no s'hi veu res, en blanc), en canvi sense els efectes hi treballo perfectament. Hi ha alguna manera d'evitar-ho? No se... desactivar els efectes per a les finestres d'aquesta aplixcacio o alguna cosa aixi...

Merci

---

### Post by guillemsola on 2009-01-09
Hola, 

jo també m'he trobat amb aquest problema amb una aplicació de càlcul matemàtic que es diu Wiris Desktop. La veritat és que no he trobat una altra forma de fer-lo rutllar que deshabilitant els efectes d'escriptori. De fet ho he provat també en una altra distro amb el mateix resultat.

De fet pensava enviar un mail als que han fet aquest programa. Faig servir altres aplicacions amb java i això no m'havia passat abans. No sé si serà un problema força comú o si serà un bug d'aquest programa o del compiz.

Jo personalment sospito del "set look and feel" de java per simular aplicacions GTK+, ja que també faig sevir un editor UML (ArgoUML) que un cop arrencat es pot configurar amb l'aparença de programa java i que si està amb aparença estàndard tot va bé però si intenta simular l'aparença del sistema fa coses rares.

salutacions,

---

### Post by open-pitu on 2009-01-12
Bones!

A la universitat aquest quadri hem fet una assignatura que és un projecte de programació en java. Aplicavem arquitectura en tres capes i per tant hem fet l'interfície gràfica per al programa en SWING (llibreria visual per a Java).

A mesura que anàvem fent proves amb la nostra interfície a vegades ens passava això que dieu aquí. Buscant per foros d'internet (no recordo quin en concret, però la cerca a Sr. Google va ser semblan a: java swing pantalla gris) i vam trobar aviat que hi ha una incompatibilitat entre Java Swing i els efectes d'escriptori.

Pot ser possible que vagin per aquí els tiros. Personalment també m'hi vaig trobaar amb el NetBeans 6.5, que també funciona amb java.

No sé si algo sap alguna cosa més d'això...

---

### Post by guillemsola on 2009-01-14
Bingo!

he fet la cerca que has comentat al google i ja no és molt difícil trobar la resposta. L'opció que m'ha funcionat a mi consisteix en editar l'arxiu /etc/environment i afegir el següent:

AWT_TOOLKIT=MToolkit

També sembla que es pot fer afegint al .bashrc del teu usuari fent:

export AWT_TOOLKIT=MToolkit 

Ho he provat en Arch Linux i funciona perfecte, a l'ubuntu ha de ser el mateix ja que bàsicament és un problema del compiz.

Salutacions

---

