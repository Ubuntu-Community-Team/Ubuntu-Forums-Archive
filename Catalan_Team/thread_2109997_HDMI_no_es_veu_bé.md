---
title: "HDMI no es veu bé"
date: 2013-01-29
forum: Catalan Team
---

### Post by akyra on 2013-01-29
Bé, per continuar amb els HDMI, ara tinc el problema amb un altre ordinador.

Amb aquest ordinador el só va perfecte sense haver de fer res, be seleccionar-lo, però al que respecte la imatge quan es connecto es veu l'escriptori, però no es veu si es estic reproduint una pel·licula o l'explorador, etc., sembla que funcioni no garie estable.

En versions anteriors del kernel simplement es quedava la pantalla amb negre, com a mínim ara hi ha imatge.

Les característiques de l'ordinador són:

ACER ASPIRE AS3410-723G25n
Intel Celeron 723 1.2 GHz Single Core Processor
Grafica: Intel GMA 4500MHD 
Chipset series 	45GS 

A veure si algú té alguna idea.

Gracies

---

### Post by alpc360 on 2013-02-01
Hola akyra,

Prova a posar els drivers de Intel del PPA escoltat que els del repositori d'ubuntu donaven problemes.

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

Exemple:
**sudo apt-add-repository ppa:glasen/intel-driver**

despres fes un sudo apt-get update && sudo apt-get dist-upgrade

Si no fa rés el upgrade instal·lal

sudo apt-get install                 xserver-xorg-video-intel                                               

Reinicia i ens contes com a anat.

---

### Post by akyra on 2013-02-04
Hola alpc360,

He fet això que proposes i no és, però he seguit fent proves i crec que he vist que pasa el que no sé és com solucinar-ho, m'explico:

[INDENT]Quan comento el HDMI, automàticament veig el fons d'escriptori, però és com si em convertis el meu escriptori en una pantalla gegant del tamany de la resolució del meu portatil 1366x728 (ho algu així) + la de la tele 1920x1080.
Es per això que quan obro un programa o el veig a l'espai de la pantalla de l'ordinador o a l'espai de la pantalla de la tele, però simplement reproduir el que surt de l'ordinador es vegi a la tele no ho he aconseguit, o sigui tenir una única pantalla.
Amb això tinc l'inconvenient que si al obrir per exemple el Nautilus, s'obre a la tele, el ratolí no arriba a la tele, però si s'obre a l'ordinador si que el puc moure cap a la tele, no sé si m'explico.

No se com haig de configurar les diferents opcions de la configuració de monitors, segurament deu ser això el problema, però amb l'altre portatil no vaig haver de tocar res.[/INDENT]

Salut

---

### Post by akyra on 2013-02-04
Bé, segueixo descobrint.

El que vull és que es vegi el mateix que hi ha en el portatil que en la tele, per poder veure una pelicula a la tele, i si pot ser a tamany més gran.

Si vull utilitzar els monitors com un de sol agafo "espejar monitores" i el problema que hi ha és que la resolució que dóna és de 1024x768 en lloc dels 1366x728 que tinc en el portatil.

Si no els agafo com mirall a les hores puc posar a cadascuna la seva resolució, per exemple a la tele 1920x1080, però no sé com executar un programa a la tele o al portatil.

És normal aquest comportament al tenir dues pantalles?

Gracies

---

### Post by akyra on 2013-02-12
Bé, em sembla que no haig de solucionar fes, ja que sembla el comportament normal, així que tanco el fil.

Salutacions

---

