---
title: "Creació d'un DVD de música"
date: 2007-09-24
forum: Catalan Team
---

### Post by ernestux on 2007-09-24
Hola,

Vull crear un DVD amb tots els arxius de música de la home (.mp3 , ogg ,  wav) i amb el k3b no me'n surto..... (projecte dvd dades ?) 
 Quin programa seria el millor d'usar? I com ?

Gràcies 
Ernest

---

### Post by cortsenc on 2007-09-24
Si el que vols és guardar la música per després tornar-la a reproduir en un ordinador, ho pots fer amb qualsevol programa d'edició de CD/DVD i fer un DVD de dades.

Si el que vols és guardar la música per poder ser reproduïda directament en un aparell de música, ho hauràs de fer en CDs.

---

### Post by orestesmas on 2007-09-25
Doncs amb el K3b ho fas en un obrir i tancar d'ulls. Ja tens instal·lat el suport per DVD en el sistema?

Nou projecte de DVD de dades, arrossegues els fitxers a la finestra que se't crea i prems el botó de gravar. Quina part del procés et falla?

---

### Post by CarlesOriol on 2007-09-25
Orestes:

Dubte KDEistic. 

Al gnome per enregistrar un cd (o dvd) de dades n'hi ha prou en posar el mitjà on volem escriure, tirar-hi els arxius que volem i fer clic damunt del botó "escriu al disc".

Després de llegir la teva pregunta he anat a mirar si això funcionava així en kde però d'entrada no ho he vist, es més després de posar el mitjà m'ha avisat si volia obrir el k3b.

(vull avisar que he fet les proves amb una gutsy... seguim...)

Ara amb el "poti-poti" (NO ÉS UN FLAME!!!) que hi ha entre dolphin i konqueror hi ha cap manera de fer-ho? Pot ser amb algun d'aquells plugins d'adreces (slaves?).

---

### Post by ernestux on 2007-09-25
Hola,

Avui ho he provat i ha acabat "amb èxit".
Arrossegava els fitxers i en fer clic a GRAVA s'obria la finestra "Projecte de DVD" però no s'activava el botó "Grava" . Ara dedueixo que els fitxers arrossegats ocupaven 4,6 GB i la capacitat del DVD avui he vist amb el k3b que marca 4,5 GB -tot iser de 4,7 GB- i  potser aleshores no s'activava (però tampoc avisava de res).

Gràcies

---

### Post by orestesmas on 2007-10-03
Ui! no havia vist aquest missatge...

Vejam: si que hi ha alguns kioslaves per fer el que tu dius, però segons he mirat no estan instal·lats de sèrie amb la kubuntu. I em sembla que són extraoficials. Però per exemple cercant per internet he trobat el kio_burn (una captura: [http://www.linuxsoft.cz/screenshot_img/8933-a.jpg](http://www.linuxsoft.cz/screenshot_img/8933-a.jpg)), que et permet gravar cd amb el konqueror amb la url "burn:/"

Suposo que al principi es va intentar fer així però després la gent va adoptar massivament el k3b perquè és similar als programes que la gent està acostumada a utilitzar en windows, i aleshores aquesta mena de kioslaves van perdre força.

I quant a la qüestió "dolphin", a mi em sembla que aquest està pensat únicament per gestionar fitxers, i no crec pas que suporti tots aquests kioslaves. Per això ja hi ha el konqueror.

---

### Post by manelolesa on 2007-10-03
Aqui tambe diuen que el 'burn://'  també funciona amb Gnome.

[http://es.tldp.org/Presentaciones/200304curso-glisa/gnome/curso-glisa-gnome-html/x40.html](http://es.tldp.org/Presentaciones/200304curso-glisa/gnome/curso-glisa-gnome-html/x40.html)

Salut

---

### Post by papapep on 2007-10-03
Això és documentació molt antiga Manel (2003), el qual no vol dir que sigui incorrecta, però si que s'hauria de posar en cuarentena ja que el tema pot haver canviar un munt des d'aleshores. ;-)

---

### Post by manelolesa on 2007-10-04
A mi em funcina el "burn://" amb el Gnome, el que passa es que no tinc unitat de CD i al premer gravar no mes em surt  l'opció de crear una imatge ISO.

Salut

---

