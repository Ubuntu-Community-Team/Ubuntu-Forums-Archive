---
title: "botó dret a la barra de dalt"
date: 2012-04-29
forum: Catalan Team
---

### Post by josep-maria on 2012-04-29
He posat l'ubuntu 12.04, i ara no puc afegir res a la barra d'icones de dalt de tot (la que diu la data i 'aplicacions,llocs'). És a dir, quan faig clic al botó dret del ratolí damunt de la barra, no passa res. El botó dret sí que funciona a una altres llocs. Abans, amb l'ubuntu 11.10, tot anava bé.

---

### Post by wgarcia on 2012-05-01
Això que descrius és normal a la nova versió de Gnome (Gnome 3). Tant a l'escriptori per defecte de Gnome 3 (Gnome Shell) com al que porta l'Ubuntu (Unity) el plafó superior ja no permet afegir icones com es feia a la versió anterior de Gnome (Gnome 2). Hi ha algunes aplicacions que porten el que es diu "app-indicators" que afegeixen una icona al plafó superior. 

Si vols continuar tenint aquesta funcionalitat, hi ha algunes variants que mantenen l'aspecte i algunes funcionalitats de la versió anterior de Gnome. Per tenir-lo a l'Ubuntu has d'instal·lar (des del Centre de Programari, per exemple) el paquet "gnome-shell", i un cop fet això a la pantalla inicial on entres el teu usuari i clau, clicant a la icona d'Ubuntu al costat de la finestra per entrar la clau et sortirà un desplegable on pots escollir "Gnome Classic". Si no et surt aquesta pantalla inicial (és a dir el teu sistema entra directament a l'escriptori un cop que inicies l'ordinador) comenta-ho. Un cop fet aquesta elecció d'escriptori el sistema ja la "recorda", i no has de tornar a fer això a no ser que vulguis tornar a canviar d'escriptori.

Una altra opció és acostumar-se a les altres opcions que hi ha ara per substituir les dreceres directes del plafó superior. Per un cantó hi ha com deia els "app-indicators" per a moltes aplicacions. Per un altre cantó es poden afegir al llançador que hi ha a l'esquerra. I per últim estan accessibles molt ràpidament al "Dash", que s'obté clicant la tecla "Super" (la que està al costat de la tecla esquerra Alt) i entrant les dues o tres primeres lletres de l'aplicació que vols accedir.

---

### Post by Joan A. on 2012-05-03
Si vols tenir un clon clavat del gnome 2 al Centre de Software trobaràs el paquet gnome-panel. És una còpia quasi perfecta però corrent amb Gnome 3.4. A jo m'ha agradat molt i és l'entorn que estic utilitzant. Te'l recoman. Per instalar-lo ho pots fer des del Centre de Software o des del terminal:

> sudo apt-get install gnome-panel

Tendràs dues opcions: gnome clàssic i gnome clàssic (sense efectes). Per afegir programes a la barra els arrosegues des del menú aplicacions i per afegir 'applets' has de prémer els botons 'super' (Windows) + Alt + Click botó dret del ratolí.

Hi ha un petit bug que vaig penjar fa dos dies en aquest fòrum i al qual li he afegit la solució. Au! Esper que et vagi bé!

---

### Post by josep-maria on 2012-05-05
Suposo que ja havia fet això de ficar-hi el gnome-panel perquè ara ja surtia la finestretat que diu gnome classic i gnome classic sense efectes, quan s'engega el pc.

He provat d'arrossegar la calculadora a la barra de dalt i sí que s'hi queda. Potser així ja en tinc prou, encara que no funcioni el botó dret. Però no he pogut esborrar-la de la barra, ni amb el botó dret ni de cap manera. Com es fa?

---

### Post by wgarcia on 2012-05-05
No faig servir aquest escriptori, però em sembla que ara en comptes de clicar amb el botó dret del ratolí sobre el plafó superior, s'ha de primer clicar la tecla ALT i després el botó dret del ratolí.

---

### Post by Joan A. on 2012-05-05
La combinació correcta és: ALT + Botó 'super' (el botó de Windows) + clic del botó dret. Així podràs accedir als 'applets' i editar els accessos que ja tens al panel.

---

### Post by josep-maria on 2012-05-05
Ho he fet com dieu i ja funciona. Moltes gràcies.

---

