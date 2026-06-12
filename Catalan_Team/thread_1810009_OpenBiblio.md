---
title: "OpenBiblio"
date: 2011-07-22
forum: Catalan Team
---

### Post by jinglada on 2011-07-22
Hola,
Vull instal·lar OpenBiblio ([http://sourceforge.net/projects/obiblio/files/OpenBiblio/0.6.1/openbiblio-0.6.1.tar.bz2/download](http://sourceforge.net/projects/obiblio/files/OpenBiblio/0.6.1/openbiblio-0.6.1.tar.bz2/download)). 

He seguit les instruccions del paquet que també són a: ([http://www.iuta.uniovi.es/biblioteca/install_instructions.html](http://www.iuta.uniovi.es/biblioteca/install_instructions.html)) i he arribat fins on diu: ***Copy the openbiblio directory and all of its contents into your web server's htdocs root or any subdirectory within the htdocs root.***

En l'Ubuntu 10.04 no he vist "web server's htdocs root" i el document d'instal·lació diu que correspon a Operating System: Ubuntu 6.06.1

Què hauria de fer per a instal·lar-ho en el 10.04?

Gràcies a la bestreta.

---

### Post by wgarcia on 2011-07-22
No sé exactament com funciona aquesta aplicació ni que fa, però la instrucció que poses sembla suggerir que necessites tenir un servidor web apache corrent al teu ordinador, i el "document root" seria el directori arrel que aquest servidor web serveix a Internet.

---

### Post by jinglada on 2011-07-22
> **wgarcia said:**
> No sé exactament com funciona aquesta aplicació ni que fa, però la instrucció que poses sembla suggerir que necessites tenir un servidor web apache corrent al teu ordinador, i el "document root" seria el directori arrel que aquest servidor web serveix a Internet.

Gràcies wgarcia! Em sembla que ja ho he trobat. Estic fent la documentació i quan la tingui polida la penjaré.

---

### Post by wgarcia on 2011-07-23
Sols afegir que aquest directory pot ser per exemple /var/www/html

---

### Post by jinglada on 2011-07-23
> **wgarcia said:**
> Sols afegir que aquest directory pot ser per exemple /var/www/html

Bé, ho he resolt d'una altra manera, però fent: 
file:///var/www/index.html, dóna:
--------------------------
It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.
--------------------------
igual que fent: [http://localhost/](http://localhost/)

En prenc nota per si em fes falta en algun moment.

Gràcies!

---

### Post by jinglada on 2011-07-26
> **jinglada said:**
> Gràcies wgarcia! Em sembla que ja ho he trobat. Estic fent la documentació i quan la tingui polida la penjaré.

Aquí teniu la documentació de la instal·lació de l'OpenBiblio que he necessitat.

---

