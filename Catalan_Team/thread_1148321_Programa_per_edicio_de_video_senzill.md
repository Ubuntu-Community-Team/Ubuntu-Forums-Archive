---
title: "Programa per edicio de video senzill"
date: 2009-05-04
forum: Catalan Team
---

### Post by akyra on 2009-05-04
Hola a tothom

Fa temps que vaig buscant un programa per editar video que sigui senzill. Fins ara estic utitilizant el Pinnacle amb windows, però m'agradaria trobar-ne un altre que fos senzill de fer anar per linux.
El que vull fer és molt senzill, extreure pelicula de la cinta de miniDV, treure fotogrames dolents, afegir música, titols i menu de DVD i grabar en un DVD. No sembla res de l'altre dijous, però no sé quin programa utilitzar.

Vaig probar el Cinelerra, però deunido com és de complicat.

En coneixe-ho d'algun altre que permeti fer aquestes operacions?

Algú ha utilitzat Kdenlive?

Moltes gracies

---

### Post by oriolsbd on 2009-05-04
Hola, Akyra.

A SomGNU fan fer una petita [revisió d'editors de vídeo lliures]("http://www.somgnu.cat/7-editors-de-video-lliures-per-a-gnulinux/"). Potser et serveix.

Apart d'això, també van fer un [tutorial per a fer muntatges amb el Kdenlive]("http://www.somgnu.cat/tutoria-fer-un-muntatge-de-fotos-amb-musica-a-gnulinux-i/"). No és exactament el que tu demanes, però segurament et servirà per veure la simplicitat/dificultat d'ús del Kdenlive. Per les poques referències que en tinc, sembla ser que a partir de la versió 0.7 va molt bé (tot i que jo no l'he utilitzat mai directament).

Salut!

---

### Post by kukat on 2009-05-04
*"El que vull fer és molt senzill, extreure pelicula de la cinta de miniDV, treure fotogrames dolents, afegir música, titols i menu de DVD i grabar en un DVD. No sembla res de l'altre dijous, però no sé quin programa utilitzar".*

Mira:[http://www.facebook.com/v/1028256961600](http://www.facebook.com/v/1028256961600)

Aquest el vaig fer ahir amb el Kdenlive, i l'ajuda del **mencoder** per a tallar trossos del vídeo (era el partit complet!!:))  (per a instal·lar-ho "sudo apt-get install mencoder") 

Ha millorat molt el kdenlive en la última versió, i cada vegada es més complet. I no dona les errades que dona el Pinnacle (almenys a mi em donava moltes errades una vegada acabat el vídeo i volent-lo exportar)

---

### Post by akyra on 2009-05-05
Gracies per la resposta.

Jo amb el Pinnacle he tingut problemes de quedarse penjat, aquesta cap de setmana no va haver-hi manera de fer la codificació per fer un DVD.

El kdenlive fa bona pinta, però sembla que pots treure troços del video que edites. Ho has hagut de fer amb el memcoder? Què fa aquest programa que no faci el kdenlive?.

Per cert molt bo el video, li vas posar ganes :P

Bé, a veure si l'instalo i provo de extreure el video de la càmara per firewire, amb el Cinelerra, kino no vaig poder.

He mirat la llista de editors de video, i veig que també parlen del PiTiVi i no fa mala pinta. Algú l'ha utilitzat?

Gracies

---

### Post by kukat on 2009-05-05
Si, es pot retallar amb el Kdenlive perfectament el vídeo....però com el meu ordinador tampoc es cap meravella, i el vídeo durava 1 hora i 30 minuts....jejejej es fa més ràpid amb el mencoder!

es prou senzill!:

mencoder -ovc copy -oac copy -ss 5 -endpos 30 -o peli_destí.avi peli_origen.avi


---> On el 5 es el segon on comença, i 30 es la duració que tindrà a partir del segon 5. 


Salut!

EDITO: Doncs no he provat el Pitivi, però la veritat es que te molt bona pinta! Ja comentareu com funciona!

---

### Post by orestesmas on 2009-05-05
Kdenlive és realment molt bo, i millora segon a segon. recomano compilar-lo amb el [Kdenlive build wizard]("http://www.kde-apps.org/content/show.php/Kdenlive+Builder+Wizard?content=85826")

Si només voleu talar fragments de vídeo no recomano el mencoder per un usuari novell. Proveu l'avidemux.

---

### Post by kukat on 2009-05-05
> **orestesmas said:**
> Kdenlive és realment molt bo, i millora segon a segon. recomano compilar-lo amb el [Kdenlive build wizard]("http://www.kde-apps.org/content/show.php/Kdenlive+Builder+Wizard?content=85826")

Si només voleu talar fragments de vídeo no recomano el mencoder per un usuari novell. Proveu l'avidemux.


Gràcies! El provaré jo també! Per què si, de vegades val la pena fer-ho gràficament!

---

### Post by papapep on 2009-05-06
[Aquí]("http://caytec.es/ez/index.php/esl/content/download/374/2502/file/Comparativa%20Herramientas%20de%20Edici%C3%B3n%20No%20Lineal.pdf") trobareu un estudi comparatiu d'eines d'edició de vídeo no lineal i eines de conversió de formats, prou interessant i acurat (Orestes, no t'inflis, que t'hauran d'enxamplar la porta de casa... :D)

---

### Post by sianeu on 2009-05-08
> **orestesmas said:**
> Kdenlive és realment molt bo, i millora segon a segon. recomano compilar-lo amb el [Kdenlive build wizard]("http://www.kde-apps.org/content/show.php/Kdenlive+Builder+Wizard?content=85826")

Si només voleu talar fragments de vídeo no recomano el mencoder per un usuari novell. Proveu l'avidemux.


Orestes, com es fa això? No em manego gaire bé amb l'anglès.
Faig servir l'ubuntu Jaunty, així que si no m'erro he de seguir les instruccions de
[https://help.ubuntu.com/community/KdenliveSVN]("https://help.ubuntu.com/community/KdenliveSVN") 
canviant hardy per jaunty. Lo de descomentar les dues linies de backports també ho he de fer? (o només es per l'Intrepid?).

Agrairia una mica d'ajut. Crec que val la pena fer-ho per que sembla que es un salt important respecta a la versió 0.7.3 dels repositoris.

Salut

---

### Post by kukat on 2009-05-08
:confused:
Crec que el que ve a la Jaunty és la última versió (la 0.7.3 és la última! no?)
....
:)

[http://www.kdenlive.org/http://www.kdenlive.org/](http://www.kdenlive.org/http://www.kdenlive.org/)

---

### Post by oriolsbd on 2009-05-08
Sí, ve la 0.7.3.

Salut!

---

### Post by akyra on 2009-05-08
Gracies a tots per les respostes, a veure si consegueixo fer alguna cosa, realment editar video porta temps...

Bé, aveure si tinc una mica de temps i instal·lo el kdenlive, i puc dir alguna cosa més quan el provi.

Miraré si la versió és la mateixa en el Jaunty i si no la compilaré. Jo utilitzo la versió de 64 bits.

Salutacions

---

