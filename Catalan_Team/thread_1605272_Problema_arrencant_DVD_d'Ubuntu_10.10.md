---
title: "Problema arrencant DVD d'Ubuntu 10.10"
date: 2010-10-25
forum: Catalan Team
---

### Post by Domènec on 2010-10-25
[FONT=Verdana]Hola, bon dia a tothom!

Tenim un portàtil amb el win7 i ens dóna molts problemes, amb el que he volgut provar l'Ubuntu.[/FONT] [FONT=Verdana]

He reiniciat amb el DVD de l'Ubuntu i tot sembla funcionar bé.[/FONT] [FONT=Verdana]
Trio l'idioma  *Català*  i després a  "*prova l'Ubuntu sense fer canvis a l'ordinador*"


M'apareix una pantalla amb un logotip Ubuntu i cinc puntets a sota.
Es van encenent un per un i, quan només queda el cinquè per encendre, m'apareix a la pantalla el missatge:[/FONT][FONT=Verdana]

> [B]BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: No such device[/B][B]
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs[/B]
També m'apareix pràcticament el mateix missatge si trio  "*Comprova el DVD per errors*"...


[/FONT][FONT=Verdana]Com que no hi entenc gens de la línia de comandes no he aconseguit fer res més...[/FONT]   [FONT=Verdana]


[/FONT][FONT=Verdana]Si trio "*Instal.la l'Ubuntu*" m'apareix també el mateix.
En canvi si agafo "*Instal·la l'Ubuntu en mode text*"  tot sembla funcionar bé, em comprova el DVD, carrega components addicionals, cerca la xarxa (però no la troba), em demana l'hora,...

No he volgut continuar perquè m'ha fet por veient com funciona la resta...

[/FONT][FONT=Verdana]




Però com que no me me'n sortia amb les altres opcions he provat el  "*test de memòria*" i... m'he trobat amb això: [/FONT]     [FONT=Verdana]:(

[IMG]http://img829.imageshack.us/img829/8923/20101022erroramemria.jpg[/IMG][/FONT]  [FONT=Verdana]



Em temo que puc tenir la RAM espatllada a algun lloc però no sé com interpretar-ho. [/FONT]   [FONT=Verdana]:confused:

Algú em pot donar un cop de mà amb tot plegat?[/FONT]

---

### Post by kukat on 2010-10-26
Doncs sí que sembla que tens la RAM espatllada.....
Pot ser que no et done errors amb la insta&#320;lació en mode text perquè no carrega tantes dades a la RAM i no arriba a donar error.....
Pots provar a baixar altra distro més lleugera (Knoppix per exemple) per a assegurar-nos que no és el DVD que té algun defecte....però tot fa indicar que és la RAM. 

Per cert, benvingut al Catalan Loco Team!!!

No oblides presentar-te al nostre [Fil de Benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") i de llegir les [Normes del Fòrum]("http://ubuntuforums.org/showthread.php?t=599965").

---

### Post by wgarcia on 2010-10-26
Una altra possibilitat més tonta és que el DVD en qüestió estigui danyat. Podries provar de gravar un CD amb l'última versió d'Ubuntu y veure si així sí que t'arrenca la sessió de prova.

---

### Post by kukat on 2010-10-26
> Una altra possibilitat més tonta és que el DVD en qüestió estigui danyat. Podries provar de gravar un CD amb l'última versió d'Ubuntu y veure si així sí que t'arrenca la sessió de prova.

També val, però el Knoppix és més ràpid des del meu punt de vista....Sobretot si és per provar que és el DVD que falla....
:P

---

### Post by Domènec on 2010-11-17
Hola a tots i mercès per les vostres respostes :)
[SIZE=2]Perdoneu el retard, però ara mateix tinc molts "fronts oberts" i haig d'anar diversificant el temps...[/SIZE]


[SIZE=4]_He estat fent un munt de comprovacions i no he aconseguit esbrinar gaire res_.[/SIZE]

**- He provat el DVD a un altre ordinador i també falla igual**
Probablement el DVD estigui malmès, a l'hora de gravar-lo el Nero em va dir que la mida dels sectors no era l'estàndard i si volia fer-ho com deia la imatge ISO o com l'estàndard.
Pensant que era una cosa del Linux li vaig dir que respectés la de l'ISO. Pot ser que per això no funcioni...

**- He provat el mòduls de memòria per separat i cap em dóna error**
Tinc dos mòduls de 2GB i dos 'slots'.
He provat ambdós mòduls per separat a ambdós forats entre 30' i hora i mitja i no m'han donat cap error

**- També he provat amb el test de memòria dels Ubuntu 9.4 i 9.10 i no troben cap error**
Per casa tenia dues versions RC dels ubuntus antics i he provat els seus test de memòria (em sembla que són la versió 2.1).

Malgrat provar els dos mòduls de cop no han trobat errors...



Ara estic tornant a baixar la ISO del 10.10 a veure si la cremo bé i puc treure'n una mica l'entrellat.

No crec que el fet de que el DVD contingui errors afecti les proves de memòria, però això de que un mòdul no falli i els dos sí em té força fregit... :(



[SIZE=4]*Em podrieu fer una pinzellada de les diferències entre KDE, Gnome i XFCE?*[/SIZE]
[SIZE=1](m'interessa una versió d'ús amigable i que s'assembli al windows, perquè és per una persona poc avesada a la informàtica...)[/SIZE]

Per cert, hi ha algun avantatge en descarregar la ISO del DVD d'*ubuntu.com* respecte a descarregar la ISO del CD a *ubuntu.cat*?
Vull dir si el DVD només porta més idiomes o porta algun afegit extra?

---

### Post by kimet on 2010-11-17
>Em podrieu fer una pinzellada de les diferències entre KDE, Gnome i XFCE?

Hi ha una muntanya enorme de informació a la xarxa sobre aquests escriptoris, i de discusions sobre quin es millor també...

>Vull dir si el DVD només porta més idiomes o porta algun afegit extra? 

Òbviament porta mes programes, pero cap que no puguis instal.lar posterioment.(si es que el vols instal.lar al disc dur)

Salut.

---

