---
title: "Problemilles amb ati 9250"
date: 2007-04-25
forum: Catalan Team
---

### Post by Fang5 on 2007-04-25
Hola!

Fa temps que vaig desistir d'activar l'acceleració 3d, però l'altre dia vaig trobar una guia que explicava com instalar el driver lliure, em sembla que era el AIXGL, o algo així: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Bé, la questió es que amb el meu precari anglès he seguit les instruccions que he entés, i finalment he vist que posava que amb les targetes Radeon 9250 amb el RV280 de chip hi havia un bug en el Xorg.
[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)

El problema es que quan li dono a :
$ sudo apt-get build-dep xserver-xorg-driver-ati

em surt un error que no se que vol dir:

carles@laura-desktop:~$ sudo apt-get build-dep xserver-xorg-driver-ati
Password:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: No es pot trobar un paquet de fonts per a xserver-xorg-driver-ati
carles@laura-desktop:~$ 

He prova de descarregar-me des d'una pagina el paquet i de passar al pas següent però tampoc funciona.


Per cert, per aprofitar el post, hi ha algun lloc on facin cursillos d'obuntu o linux, i si pot ser gratis millor?

Gràcies per adelantat

---

