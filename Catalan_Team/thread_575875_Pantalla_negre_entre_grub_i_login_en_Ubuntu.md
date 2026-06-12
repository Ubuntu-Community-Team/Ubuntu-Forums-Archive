---
title: "Pantalla negre entre grub i login en Ubuntu"
date: 2007-10-14
forum: Catalan Team
---

### Post by Usuari on 2007-10-14
Hola, tinc instal·lat Kubuntu en una partició i Ubuntu en una altra del mateix disc dur i entro amb el grub.

El cas és que una vegada escullo l'opció del grub, el Kubuntu s'inicia normalment, mentre que l'Ubuntu em deixa la pantalla sense res (negre) fins que acaba de carregar l'aplicació i llavors em surt directament la pàgina de login:confused:...  A partir de llavors tot funciona amb normalitat (fins i tot el Kompiz)...

Algú em pot orientar per saber què passa? No surt res, ni el logo, ni les lletres ni res des que selecciono l'opció amb el grub fins a la pantalla de login...¿?

---

### Post by CarlesOriol on 2007-10-16
El kubuntu i l'ubuntu son el mateix sistema amb un paquet de programes i escriptori diferents.

Pots insta&#320;lar tot el software necessari de l'un i l'altre fent : 

sudo apt-get install kubuntu-desktop
o
sudo apt-get install ubuntu-desktop

I pots triar el tipus d'escriptori a l'iniciar sessió.

Tenir dues particions és perdre el temps i l'espai del disc.

Altres configuracions que pots trobar: xcfe-desktop i en gutsy mythbuntu-desktop i gobuntu així com versions específiques com ubuntu-studio (per aquesta et calen uns repositoris afegits).

Sobre l'error que comentes edita el menu.lst a /boot/grub i al sistema que veus negre elimina el text: quiet splash

---

### Post by Usuari on 2007-10-17
La veritat és que tinc instal·lades dues actualitzacions diferents de l'Ubuntu, una en Kubuntu i l'altra en Ubuntu; per això tinc instal·lat un sistema duplicat. Demà quan es publiqui la 7.10 la 7.04 volarà del meu disc dur...

Gràcies per la resposta.:)

---

