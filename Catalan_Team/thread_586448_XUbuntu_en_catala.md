---
title: "XUbuntu en catala"
date: 2007-10-22
forum: Catalan Team
---

### Post by narcisgarcia on 2007-10-22
Donat que els ordinadors antics, i en poblacions poc connectades, solen ser els més necessitats d'un CD-ROM d'instal·lació amb els paquets de català ja aplicats, seria molt útil comptar amb el CD d'instal·lació de XUbuntu catalanitzat.

Algú podria publicar una mica de recepta de com descarregar el material necessari i generar una XUbuntu-cat equivalent a les Ubuntu i KUbuntu actualment publicades?

---

### Post by papapep on 2007-10-22
N'Orestes Mas va fer fa una mica una mena de tutorial de com fer-ho. El busco i t'ho passo.

---

### Post by papapep on 2007-10-22
Bé, sembla que anava confós i no hi ha cap tutorial en català. De tota manera l'Orestes m'ha comentat que es fa amb el packet **uck** :

[http://uck.sourceforge.net/download?DokuWiki=5d1486981cd6bd1aef83cd541db14d47#latest-stable-release](http://uck.sourceforge.net/download?DokuWiki=5d1486981cd6bd1aef83cd541db14d47#latest-stable-release)

---

### Post by orestesmas on 2007-10-23
La idea és:

1) Descarrega't una imatge de la Xubuntu-desktop en anglès.

2) Baixa't l'UCK (directament el paquet .deb)
[http://downloads.sourceforge.net/uck/uck_2.0.0-beta5_all.deb?modtime=1190974009&big_mirror=0](http://downloads.sourceforge.net/uck/uck_2.0.0-beta5_all.deb?modtime=1190974009&big_mirror=0)

3) Instal·la't l'UCK amb sudo dpkg -i <nom del pquet>

4) Executa uck-gui i segueix els passos

5) Lamentablement l'eina només deu estar automatitzada per Gnome i KDE. Hi ha una opció "altres" que segurament servirà per xubuntu però el més probable és que s'aturi en algun punt del procés de catalanització i et passi a "control manual" per tal que tu decideixis quins paquets poses i treus. En acabat, ell continuarà el procés.

6) Lamentablement, no puc ser més precís. No ho he fet mai per una xubuntu. Si no te'n surts miraré de fer-ho jo, però no serà immediatament, perquè estic força embolicat darrerament.

7) Advertència: l'eina UCK és bastant perepunyetes. Necessita poder crear   en el directori /home de l'usuari un subdirectori anomenat "tmp" (si ja existeix peta), i li cal força espai al disc i un processador potent per l'etapa de recompressió del sistema de fitxers amb squashfs.

Espero que et serveixi.

---

### Post by narcisgarcia on 2007-11-13
He provat tot això i m'ha anat bé.
El Live-CD de la XUbuntu es deixa traduïr, encara que no tot el XFCE està ben traduït i tant coherent i entenedor com el Gnome.

De tota manera em trobo amb el problema de què la XUbuntu 7.04 (Feisty) en instal·lar-se no deixava enllaços dels programes, i la XUbuntu 7.10 dóna molts problemes amb els controladors gràfics i les resolucions de pantalla.

Estic preparant una altra (nova) metadistribució.
Ja donaré notícies quan estigui practicable.

---

