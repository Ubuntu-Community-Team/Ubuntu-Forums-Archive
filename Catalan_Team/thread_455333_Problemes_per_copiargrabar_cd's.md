---
title: "Problemes per copiar/grabar cd's"
date: 2007-05-26
forum: Catalan Team
---

### Post by utep on 2007-05-26
Nes a a tothom!

Soc nou am això d'Ubuntu i tinc problemes en la grabació de cds/dvs alhora de copiar/gravar un cd avere si algu de per aki em pot ajudar. Això es el que he fet:

1. Com he llegit en altres posts, he provat de fer-ho de la manera que sembla més facil, o sigui:
Llocs -->ordinador --> seleccionar el cd que vull grabar amb el botó de la dreta --> "copia el disc" --> selecciono la unitat on està el cd verge --> selecciono "escriu" --> i un cop aqui m'apareix el següent missatge com si anés a començar:
***
S'esta copiabt el disc:
S'està copiant el disc seleccionat a un cd o dvd. Aquesta opercació pot trigar molt temps depenent de la mida de les dades i de la velocitat d'escriptura del dispositiu.
<<barra de procés>>
S'està creant una imatge del disc
***
Però en realitat cap de les unitats de cd les llegeix i el missatge anterior desapareix en aproximadament 5 segons sense mostrar cap altre missatge d'error ni similar ni sense haver escrit ni llegit res.

2. En comptes de fer un copia he intentat crear un cd de dades arrastrant les dades del disc d'origen al disc verge també desde Llocs --> ordinador i se'm penja la finestra al més pur estil windows havent-la d'apagar forçant-ne la sortida. Provo de repetir el proces però en comptes d'arrastrar, faic un copiar-enganxar i la penjada es repeteix.

3. Insta-lo el programa xfburn i segueixo les instruccions per fer la copia i m'apareix l'error: "Cannot setup source device /dev/sr"

Moltes gràcies per adelantat.
utep

---

### Post by pisuke on 2007-05-26
Hola, no se si fas servir gnome o kde com a gestor de finestres.

En el primer cas et recomano que per gravar cd's i dvds dins gnome facis servir el gnomebaker.

sudo aptitude install gnomebaker

Et guiarà facilment pels passos de crear un cd de dades, d'audio, el que faci falta.

Si fas servir KDE, et recomano el k3b, un dels millors programes per gravar cds.

sudo aptitude install k3b


Espero que et serveixin!!

---

### Post by CarlesOriol on 2007-05-26
Els processos 1 i 2 haurien de funcionar. De fet son el mètode més senzill en gnome..

Quan dius que es penja la finestra podries donar més pistes per veure que pot passar.

També he llegit que llegeixes d'un aparell disc i escrius en un altre. Prova de llegir i (després) escriure al mateix dispositiu a veure si també passa.

---

### Post by utep on 2007-05-26
Ho sento pero no se si estic fent servir gnome o kde, defet, en realitat no se molt be ni què és... 
Soc molt novato amb el tema i per ara només m'he instalat el ubuntu 7.04 tal i com va amb el liveCD i prou...
Pel que fa  a les penjades de la finestres, doncs mira: acabo de provar-ho un parell de cops més i aquests han estat els resultats:

1. He seleccionat tots els arxius del cd a copiar i els he enganxat al cd verge (algun dels quals s'han enganzxat amb un simbol de un candau que encara no se molt be que vol dir...) i després he apretat el boto "escriure cd" i la pantalla se m'ha quedat així:

[IMG]http://img91.imageshack.us/img91/8716/capturanr0.png[/IMG]

2. Selecciono tots els arxius del cd a copiar i els arrastro al cd verge. Aparentment a primera vista no passa res... l'icona ni s'inmuta (no es posa en situació de pensar) i tot queda igual fins que decideixo anar al cd verge a vere si s'han quedat gravats i és quan la finestra se'm queda així (amb el cursor en situació de pensar):

[IMG]http://img152.imageshack.us/img152/4092/captura1tb7.png[/IMG]

En ambdós casos haig de tancar bruscament les finestres perquè per més temps que passi no fa res i l'osrdinador es queda igual.
Potser també sigui important destacar que en cap dels dos casos s'aqrriba a encendre la llum de cap dels lectors de cd/dvd i en l'estona que està "penjat" tampoc s'encén la llum del disc dur (la vermella tipica de les torres vull dir...)

Pel que fa a lo que em deies carles oriol de provar de llegir i copiar en una mateixa unitat, doncs tampoc reacciona, i tant sols apareix, com havia comentat abans el misatge en qüestió durant uns 5 segons i desapareix automàticament sense fer res. T'adjunto foto perquè ho veigis més clar (aquest es el misatge que dura 5 segons):

[IMG]http://img501.imageshack.us/img501/660/captura2le1.png[/IMG]

---

### Post by pisuke on 2007-05-27
Pel que veig tens moltes unitats de cd-rom (fins a 5?). En la primera pantalla que has adjuntat has tingut la opció de seleccionar la unitat amb què s'escriurà el disc? És allà on posa Escriu el disc a: DVDRAM GSA-H42N.

Jo continuo proposant que provis de gravar utilitzant el gnomebaker que et deixarà escollir la unitat de cd adecuada.

---

### Post by utep on 2007-05-27
Defet pisuke, el tema de les unitats es una altre cosa que no entenc; t'explico... jo tinc:
- Lector de DVD
- Gravadora Cd's
- Gravadora DVD's
...al moment d'instalar el ubuntu m'apareixen 3 unitats: "CD-ROM 1", "CD-ROM 2" i "CD-ROM 3" però, en canvi, al moment que poso un cd/dvd a qualsevol de les unitats, m'apareix una altre unitat amb el cd que realment he posat com si les tre unitats anteriors no servisin per res... i, en realitat, si li donc a qualsevol de les 3 unitats de CD-ROM, m'apareix l'error: "no s'ha pogut muntar la unitat seleccionada.

..Ah! i efectivament, el DVDRAM que figura, era realment on havia de gravar...


No se que coi està passant... :(

---

### Post by pisuke on 2007-05-29
Estic una mica perdut.

Pots provar d'instalar el gnomebaker (sudo aptitude install gnomebaker) i veure si així pots gravar sense problemes? És per descartar coses.

Sort!

---

### Post by utep on 2007-05-31
Merci pisuke! m'he aconseguit instalar el gnomebaker i he aconseguit grabar el primer cd amb ubuntu... Moltes Gràcies..

De totes maneres, em continua treient el son el perquè no podia com he explicat anteriorment així com tb el nou dubte que m'ha sorgit que perquè em surten tantes unitats de Cd "aparentment fantasmes"...

En fi, continuaré buscant!
utep

---

