---
title: "Problemilla amb la configuració de les X"
date: 2007-06-25
forum: Catalan Team
---

### Post by Fang5 on 2007-06-25
Hola a totom!

Fa un parell de dies em van "regalar" un PIII 800Mhz amb 64 Ram. Vaig pensar que era el moment de baixar-me totes les pelis que no m'havia pogut baixar encara per falta d'ordinador.

Vaig decidir-me, donat que té molt poca ram, posar una xubuntu, amb el alternate desktop. Tot va anar com una seda fins que configurava un paquet anomenat "anthy", quan es quedava penjat. Després vaig descobrir que es veu que utilitza un procés que ocupa el 75% de la cpu i que no es pot instal·lar. 

Com que això llavors no ho sabia vaig instal·lar una línia de comandes (o com es digui en català) i instalar el paquet xubuntu-desktop. Mel vaig baixar i quan va arribar al anthy vaig pulsar ctrl+c i es va saltar. Li vaig vaig reiniciar i s'em quedava la pantalla en negre (ja no m'enrecordo gaire bé. vaig provar d'instalar les x de forma manual. Mai havia fet servir tant la linia de comandes o sigui que la vaig liar molt, però al final, mirant per internet, em sembla que em vaig baixar els paquets correctes, o sigui un paquet gran que es deia xorg, però no se perque no em deixava instalar les fonts. Quan li vaig donar al startx em va sortir tot de linies verticarls de colors, i al canviar la profunditat de color va canviar a color gris.

Després vaig instalar una debian, que tampoc va resultar, perque no se que em vaig carregar del Apt, i finalment m'he instalat un DSL però no em funciona l'acces a internet (dhcp) 

M'agradaria instalar el xubuntu. Que faig, poso una linia de comandes o instalo amb l'instalador i em salto lo del anthy?

He vist que el dsl utilitza el kerner 2.4, en que es diferencia del 2.6, seria adequat canviar-me'l?

Merci per tot

---

### Post by papapep on 2007-06-27
Mare de Deu dels ratolins inalàmbrics...quantes preguntes de cop.

Per començar, no ho tindràs fàcil amb una màquina amb tan poca RAM.

Segon, no hi ha cap raó objectiva per què el paquet "anthy" et causi aquest problema de "penjament", bé si, la manca de RAM. T'ha passat només un cop, o ho has provat més d'un?

Entenc que quan dius que vas instal·lar una "línia de comandes" deus voler dir que vas instal·lar l'Ubuntu sense entorn gràfic, oi?
Respecte els paquets, si fas servir "aptitude" per a instal·lar els paquets, ja et controlarà les dependències i t'ho farà tot solet. Com a molt, és possible que hagis d'instal·lar el paquet xdm, o gdm segons vulguis, per a entrar a l'entorn gràfic.

Respecte el que dius de línies verticals i demés en executar "startx", pinta que no tinguis ben configurada la placa gràfica (la parametrització del fitxer /etc/xorg.conf). És possible que al fitxer Xorg.0.log hi quedi rastre de l'error.

Respecte què instal·lar, podries tornar a instal·lar Ubuntu sense entorn gràfic i, posteriorment, instal·lar el XFCE4 i l'XDM. Tot i això, considerant la precarietat de recursos de la màquina, seria bo instal·lar un entorn gràfic que es diu Fluxbox, el qual és molt espartà en consum de recursos però, per la mateixa raó, no és gaire fàcil pels usuaris novells.

Possibilitats en tens moltes, però la tria és teva. Tu t'hi hauràs de barallar.

El que si que t'aconsello és que ens expliquis els teus dubtes abans de fer-ho, ja que un cop has fet el que sigui, i t'ha petat tot, és més complicat d'entendre el perquè. 

Ah! I respecte el kernel, quan més nou més maquinari sap gestionar i, en teoria, més depurat està i menys problemes ha de tenir.

Millor preguntar abans. ;-)

---

