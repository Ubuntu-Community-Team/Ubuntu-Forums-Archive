---
title: "Dubte a l'hora d'actualitzar ubuntu"
date: 2009-01-27
forum: Catalan Team
---

### Post by rogespierre on 2009-01-27
Bones!
Avui estava actualitzant l'ubuntu a la versio 8.10 amb el cd, i en el procés d'instal·lació m'ha assaltat un dubte en l'apartat de les particions. Tinc una pel windows, que vull mantenir totalment intacta, i una altra més petita on hi tinc instal·lat l'ubuntu i on. òbviament, vull reescriure-hi amb la nova versió.

Ja havia actualitzat ubuntu i amb cd **dues **vegades abans i sense cap mena de problema. A més, ja recodava que en el tema de particions havia d'escollir jo la 3 i que el punt de muntatge era "/". Cap problema vaja... però ara m'he trobat amb un menú i uns gràfics una mica diferents i, la veritat, em fa por escollir sense consultar a algú més expert. 

Em diu coses de redimensionar, i els colors i els %atges no em quadren... tot té la pinta que l'opció que a mi m'interessa és la **primera **però... no ho acabo de veure clar. Us poso captures de les tres opcions que em dona:

 
Aquesta és la **primera**...

Sembla que hagi de redimensionar 1 partició fent-la més gran? potser perque el 8.10 necessita més espai?

Però perquè la partició 3 (taronja) passa de 12 a 0%

i la verda de 0 a 23? si no m'equivoco és la sda3 on tinc el linux instal·lat i de cop em passa a zero...

i la blava, que és la més grossa i és on crec que tinc el windows, al gràfic diu que passa de 83 a 67 i en canvi a baix em diu que windows ocupara un 73%... i a més és de color taronja! que lliga amb la partició que passa a zero... no entenc reee:sad::sad::sad:


[IMG]http://img140.imageshack.us/img140/1499/26919290no3.jpg[/IMG]


aquesta és la **segona**, que suposo que fa neteja de tot, es carrega el windows i a sac
[IMG]http://img140.imageshack.us/img140/7842/29496457tc3.jpg[/IMG]


i aquesta és la **tercera**.. que és similar a la segona...
[IMG]http://img238.imageshack.us/img238/9259/16820377qz7.jpg[/IMG]


Com ho he de fer?!! per a que em quedi el windows intocat i que sintal·li lubuntu a la mateixa partició on el tinc ara!?

ajuda si us plau!

gràcies per avançat!!!

---

### Post by uidb4056 on 2009-01-27
Has de triar la 3ª opció, que et portará a un menu on podrás triar la particio de root "/" /dev/sda3 i la del swap /dev/sda2.

---

### Post by rogespierre on 2009-01-27
mmm... llavors amb les altres 2 q fa? bé la segona està clara... però la primera opció per a que serveix??

i fent click a la tercera... encara tindré un altre menú per triar¿?..no sq no confii però em fa por carregar-me la partició grossa

---

### Post by uidb4056 on 2009-01-27
> **rogespierre said:**
> mmm... llavors amb les altres 2 q fa? bé la segona està clara... però la primera opció per a que serveix??

i fent click a la tercera... encara tindré un altre menú per triar¿?..no sq no confii però em fa por carregar-me la partició grossa

Jo sempre he utilitzat la 3ª, si continuas endavant trobaras un punt que et demana si vols aplicar els canvis al disc ó no.

---

### Post by SiscoGarcia on 2009-01-27
> **uidb4056 said:**
> Jo sempre he utilitzat la 3ª, si continuas endavant trobaras un punt que et demana si vols aplicar els canvis al disc ó no.

Efectivament, rogespierre, tal com et comenta el uidb4056, després d'aquest pas sempre pots tornar enrere abans s'aplicar els canvis. No pateixis ;)

---

### Post by trinkus on 2009-01-27
Pero perque ho fas amb el CD de nou, si es pot saber? Si ja tens un ubuntu instalat en tens prou d'actualizar-te des d'ell mateix o fer servir un CD alternate si es que tens una connexio a internet lenta....

T'estalviaries tot plegat aixo de les particions...

---

### Post by rogespierre on 2009-01-27
iepa! he seguit però em trobo en aquesta finestra

[IMG]http://img90.imageshack.us/img90/4057/23615470gi3.jpg[/IMG]

 

no sé si cal modificar algo? ho li foto a endavant ja?

si li dono a editar la partició ext3, em dona aquestes opcions:

 [IMG]http://img90.imageshack.us/img90/5520/17137317tu9.jpg[/IMG]

cal, doncs, canviar alguna cosa, d'alguna de les particions? i què?

gràcies!

**trinkus**: doncs em van dir una vegada que és més fiable fer-ho des de CD... no és així? com ho hauria de fer sinó?

---

### Post by SiscoGarcia on 2009-01-27
Perdona rogespierre, m'havia semblat entendre que volies fer l'actualització expressament des de CD; però si l'únic que vols és actualitzar-te, com diu trinkus, només cal que facis "Alt+F2" i després hi escrius a la caixeta que se t'obrirà "update-manager -d" (sense cometes). Després d'això només cal que esperis ;)

---

### Post by rogespierre on 2009-01-27
sí, vull actualitzar des de Cd.. no és aconsellable?

i en cas de fer-ho des de la terminal, m'han dit per una altra banda una ordre diferent a la **update-manager -d** que m'has dit tu. m'han dit 

**$sudo apt-get install dist-update**

quina és la diferència i quina hauria d'usar?

---

### Post by SiscoGarcia on 2009-01-27
> **rogespierre said:**
> sí, vull actualitzar des de Cd.. no és aconsellable?

[COLOR="Red"]No sé si aconsellable és la paraula; més aviat diria que resulta més còmode actualitzar la versió que ja tens per tal de mantenir tot allò que ja tens configurat.[/COLOR]

i en cas de fer-ho des de la terminal, m'han dit per una altra banda una ordre diferent a la **update-manager -d** que m'has dit tu. m'han dit 

**$sudo apt-get install dist-update**

quina és la diferència i quina hauria d'usar?

[COLOR="Red"]Entenc que són diferents maneres d'arribar al mateix lloc, tu mateix. Jo ho vaig fer amb el que t'he dit però l'altra instrucció des de terminal és dir que t'actualitzi la distribució. No hi veig diferència.[/COLOR]

[COLOR="Red"]
Sort!
[/COLOR]

---

### Post by jmaspons on 2009-01-28
Hola,
Si vols actualitzar la versió d'ubuntu cal que utilitzis la comanda "update-manager -d" l'alternativa que deies, sudo apt-get dist-update, no existeix (prova-ho ja veuràs com et diu que no és una operació valida). Debies referir-te a dist-upgrade però tot i això només serveix per actualitzar la versió dels paquets dintre de la mateixa versió d'ubuntu. Si vols canviar la versió d'ubuntu cal canviar l'adreça dels repositoris i això es fa automàticament amb la comanda "update-manager -d".

Que vagi bé!

---

