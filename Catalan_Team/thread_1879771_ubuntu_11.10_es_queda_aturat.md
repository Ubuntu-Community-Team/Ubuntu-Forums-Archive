---
title: "ubuntu 11.10 es queda aturat"
date: 2011-11-12
forum: Catalan Team
---

### Post by josep-maria on 2011-11-12
D'ençà que he insta&#320;lat l'ubuntu 11.10 que cada cop que faig servir el firefox es queda tot aturat poc temps després de començar. A la pantalla hi ha la mateixa imatge quieta i no funcionen ni el teclat ni el ratolí. Haig de tornar a engegar el pc i llavors va bé fins que torno a entrar al firefox. Em passa sempre que entro a internet, això vol dir molts cops al dia.

---

### Post by wgarcia on 2011-11-13
Sembla un problema de l'entorn gràfic. Amb quin escriptori estàs entrant? L'escriptori per defecte (el que posa "Ubuntu" a la pantalla d'entrada, o sigui Unity) o algun altre?

---

### Post by akyra on 2011-11-14
A mi em pasa una cosa semblant però jo no utilitzu Firefox, i em pasa de tant en tant, potser un cop a la setmana.

També em surt la llumeta de "BLOQ MAJUS" en intermitent.

Haig de reiniciar i tot funciona bé.

Jo faig servir el "lightDM"

Sembla algun problema de la tarja gràfica.

Salutacions

---

### Post by josep-maria on 2011-11-15
L'escriptori és el nou, el de l'ubuntu 11.10. Amb l'ubuntu 11.04 tot anava bé.

---

### Post by wgarcia on 2011-11-15
Prova d'entrar amb l'escriptori que posa "Ubuntu 2D" i mira si també es produeix el problema, per descartar que sigui un problema d'entorn gràfic.

---

### Post by merril on 2011-11-17
A mi em pasa una cosa semblant, no només amb firefox, també amb el GIMP (el punter va varis segons més tard que el cursor) l'Amule (s'apaga sol) i d'altres, però es un problema amb el gnome3 ja que si entro amb unity (2D o 3D) no em passa...
Snif, :-( gràficament m'agrada molt més GNOME3 i m'hi he acostumat molt més ràpid que amb unity...

---

### Post by wgarcia on 2011-11-18
Pel problema del Merril, no ha de ser un problema de Gnome 3 perquè Unity és 95% Gnome 3. La diferència és que els efectes gràfics a Unity es fan amb "Compiz" i amb Gnome Shell (que no Gnome 3) es fan amb "Mutter", que són dos aplicacions d'efectes gràfics diferents. Potser és això és que et passa, "Mutter" no funciona amb algunes targetes gràfiques, especialment de la marca "ATI".

---

### Post by josep-maria on 2011-11-18
I com es fa això de canviar l'escriptori?:

Prova d'entrar amb l'escriptori que posa "Ubuntu 2D" i mira si també es produeix el problema, per descartar que sigui un problema d'entorn gràfic.

---

### Post by wgarcia on 2011-11-18
Tens configurat d'entrar amb usuari i clau? Si és així a la finestra d'entrar usuari hauries de tenir opcions de diversos escriptoris, uns dels quals és "Ubuntu 2D". 

Si el sistema entra directament a l'escriptori, vés al menú "Paràmetres del sistema", a la secció "Sistema" clica sobre "Comptes d'usuari", i al teu compte deshabilita "Entrada automàtica". Això et permetrà veure aquesta pantalla inicial (després de sortir de l'escriptori).

---

### Post by josep-maria on 2011-11-18
He desbloquejat l'entrada automàtica, i al final he pogut trobar on cal fer clic per veure els escriptoris disponibles. Si trio l'escriptori ubuntu 2D, veig el mateix escriptori que veia abans. Si trio el gnome classic, veig l'escriptori de sempre, però no hi ha el menú 'sistema' a dalt de tot, no pots configurar res. A mi em sembla molt millor el gnome classic, és el que he vist sempre i ha anat bé. Si puc veure el menú 'sistema' el deixaré posat. Què haig de fer per veure'l?

---

### Post by wgarcia on 2011-11-19
Jo no estic usant l'escriptori "Gnome Clàssic" d'aquesta nova versió, potser si hi ha algú per aquí fent-lo servir pugui ajudar, però em sembla que per afegir coses al plafó s'ha de fer ALT - botó dret del ratolí per veure les opcions.

---

### Post by josep-maria on 2011-11-19
Ja he provat això de alt+botó dret, surt una llista de coses per afegir, però 'sistema' no hi és.

Tinc més pcs que encara tenen l'ubuntu 11.04. No els passaré pas al 11.10.

---

### Post by wgarcia on 2011-11-19
No està ara aquest menú "Sistema" a "Aplicacions -> Paràmetres del sistema"?

Mira també aquesta pregunta sobre com afegir llançadors al plafó superior:

[http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic)

---

### Post by josep-maria on 2011-11-24
Després de moltes voltes, he pogut descarregar el Tweak i afegir-lo a les icones 'aplicacions, llocs'. El Tweak és molt pitjor que abans (quan el gnome classic tenia el menú 'sistema'), però és molt millor que l'escriptori de l'ubuntu 11.10 (em sembla que es diu unity 3D).

Només fa uns dies, però ja no s'atura cada cop que entro a internet, i ja no cal re-engegar el pc. De moment només s'ha aturat una parell de cops. Durant un temps va ser horrorós. Seguiré amb el gnome, que a més a més és molt més fàcil de fer anar que el unity.

Moltes gràcies.

---

### Post by wgarcia on 2011-11-25
Per aclarir termes tot és Gnome 3, l'Unity és simplement un plugin de Compiz que corre sobre Gnome 3, és un àrea de treball de les possibles sobre Gnome 3, juntament amb Gnome-shell (que és la que tu dius Gnome), el gnome-fallback (que s'assembla al clàssic) i hi ha d'altres, com per exemple:

[http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html](http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html)

---

