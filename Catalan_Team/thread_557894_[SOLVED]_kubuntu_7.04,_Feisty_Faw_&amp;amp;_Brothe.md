---
title: "[SOLVED] kubuntu 7.04, Feisty Faw &amp;amp; Brother DCP-330C"
date: 2007-09-23
forum: Catalan Team
---

### Post by farigola on 2007-09-23
Hola,
Vaig decidir comprar una impressora de la marca Brother per la política d'aquesta companya doncs tots els seus models disposen dels drives per Linux i per diferents sistemes. Ara tinc la impressora DCP-330C amb el controlador instal·lat per la kubuntu 7.04, Feisty Faw i no hi ha manera de que aquesta surti com a impressora. El sistema la detecta, però no surt el controlador tot i que vaig fer l'instal·lació. Actualmet el meu equip reconeix la Epson Stylus CX3200 i funciona perfectament, però no puc gaudir del l'altre per no sortir com a impressora configurada.

Sabeu que podria fer? Segurament això forma part de la meva poca experiència amb Linux, perdoneu per el temps que he de fer-vos perdre.

Atentament

Jordi (Amer) Girona.

---

### Post by pserra on 2007-09-23
Jo tinc una multifuncio MFC 210-C, i tampoc no tenia  manera de trobar els controladors, i un company de la UOC em va passar una adreça on va ser molt 
fàcil instal·lar-la, l'únic que crec que guardo l'adreça als favorits de l'explorer...
Si ningú et dona solució te'l passaré.  Però encara tinc el problema que va a intermitències i lent, provocant múltiples errors d'encallades de paper.
A reveure..

---

### Post by farigola on 2007-09-23
Gràcies per la teva resposta. Jo vaig trobar al mateix Web de Brother els controladors per Debian, però no hi ha manera de que un cop feta la seva instal·lació quedi la maleïda impressora configurada. He fet un piló de proves i res de res. No tinc idea de si Cups està relacionat amb el problema. 
Jo marrà que marrà tornaré a provar-ho.

Jordi

---

### Post by papapep on 2007-09-23
Crec que seria bo que ens expliquèssis detall  com has instal·lat el controlador i d'on l'has tret. Sinó no tenim referències per valorar si el que has fet és correcte o no, i que cal fer a continuació. 

També hi ha un video que explica com instal·lar impressores que no sé si l'has vist.
Tot i que és en anglès, és bastant entenedor:

[http://video.google.co.uk/videoplay?docid=-3883768294162360774](http://video.google.co.uk/videoplay?docid=-3883768294162360774)

---

### Post by farigola on 2007-09-27
Gràcies per el teu comentari, del vídeo. Crec que he seguit les indicacions perfectament. De totes maneres, estic pensant que potser el tema està en haver  instal·lat un driver privatiu de brother des de :

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html)

Vaig fer la baixada del controlador i per la meva poca experiència no vaig fer la instal·lació previa del driver  (( # Install the LPR driver.(i.e)For Debian Users:
dpkg -i --force-all mfc240clpr-1.0.0-9.i386.deb  ))

Ara el tema esta en que no puc aplicar el driver LPR doncs el sistema retorna l'error. El paquet dcp330ccupswrapper necessita ser reinstal·lat, però no se li pot trobar un arxiu. Si executo l'ordre (( dpkg -i --force-all mfc240clpr-1.0.0.9.ie86.deb )) el sistema diu el següent: L'operació requereix accés de lectura i escriptura a l'àrea d'estat de dpkg.

Crec que he fet alguna cosa que ha deixat això fora de servei.

---

### Post by pespin on 2007-09-27
```
L'operació requereix accés de lectura i escriptura a l'àrea d'estat de dpkg.
```

Errors d'aquest tipus solen donar-se quan ja tens una altra "sessió" del dpkg funcionant. (pere xemple tens un sudo aptitude install X funcionant o el synaptic obert)

---

### Post by papapep on 2007-09-27
Una altra possibilitat ,a més de la que t'ha dit en Pespin, és que et calgui posar "sudo" davant l'ordre. O sigui, dins el directori on tens el paquet mfc240clpr-1.0.0.9.ie86.deb fes:

```
sudo dpkg -i --force-all mfc240clpr-1.0.0.9.ie86.deb
```

Recorda posar el "sudo" davant de totes les ordres que impliquin drets d'administrador, com per exemple gestionar paquets de programari.
Et demanarà la teva contrassenya d'usuari i farà el que li demanes.

---

### Post by farigola on 2007-09-27
Gràcies per els vostres comentaris, he fet sudo dpkg -i --force-all mfc330clpr-1.0.0.9.ie86.deb  i res de res, però he tallat el fitxer i aquest després s'ha copiat a l'escriptori des d'aquest punt el mateix instal·lador de Ubuntu no ha donat error i el lpr ha quedat instal·lat. Seguidament he volgut instal·lar el driver cups i ha donat error hi ha una copia de pantalla annexa al comentari.
Crec que s'intenta crear un directori i no hi ha drets per fer-ho

---

### Post by farigola on 2007-09-28
Hola,
Gràcies un altre cop per els vostres comentaris.
He vist que a l'hora treure l'aplicació des de Adept el sistema intenta treure una informació que no existeix. No tic permisos per crear aquestes carpetes i no hi ha manera de tornar a instal·lar el el driver.

---

### Post by papapep on 2007-09-28
Ostres Farigola, la meitat de coses que dius no t'entenc. Has de pensar que no som davant del teu ordinador veient què fas i cal que siguis el màxim de descriptiu per a que t'entenguem.

> He vist que a l'hora treure l'aplicació des de Adept el sistema intenta treure una informació que no existeix

Què vol dir això?? Que intentes **desinstal·lar** un programa amb l'Adept i et surt un error?
Mostra'ns l'error en concret, si us plau.

> No tic permisos per crear aquestes carpetes 
De quines carpetes parles?? Recorda que no som davant la teva pantalla.
Tu tens tots els permisos que et facin falta, una altra cosa és que sàpigues com fer-ho o no ;-)

> i no hi ha manera de tornar a instal·lar el el driver.
Si ja el tens instal·lat, perquè el vols tornar a instal·lar?

---

### Post by farigola on 2007-09-28
Hola,

He de comunicar-vos que després de diferents proves he aconseguit imprimir amb la Brother DCP-330C. Per tant problema solucionat.

Que he fet: Al utilitzar només gràfic no podia canviar permisos a les carpetes, però al utilitzar kdesu konqueror he aconseguit crear un carpeta que segons l'instal·ador del driver no existia concretament /var/lib/dpkg/tmp.ci He creat la carpeta i tal com diu el sistema he executat l'instal·lador del driver i automàticament  cups ha inserit una nova impressora al meu ordinador. He fet una prova i funciona.

Gràcies per les vostres aportacions i per la paciència. Ara toca estudiar una mica més d'aquest Linux.

---

### Post by orestesmas on 2007-09-28
Home, felicitats Jordi. Veig que els meus consells offline t'han resultat útils. Això del GNU/Linux no és pas tan complicat...

---

### Post by farigola on 2007-09-29
No hi ha com tenir coneixements del sistema. Ets un crak!

Per cert, avui m'he firat! Després de moltes penitències i de fer a la dona contenta aquesta m'ha dit que tenia via lliure per firar-me un ordinador. Després de la verema  matinal  amb les petites de casa (foto annexa) una bona rentada de peus i comprada d'ordinador. La cosa fot per veure que aquesta c.p.u incorpora de serie Finestres a la Vista. Aquest no tindrà ni un trist arranc. Doncs el penso liquidar en pocs minuts. Per cert al comprar l'ordinador m'han regalat una impressora multifuncional Lexmark x2450. La tornarem a liar!

Bé demà toca anar a la Catalunya nord doncs hi ha trobada de gegants a Argelers http:\\[www.vila-amer.net/gegants](www.vila-amer.net/gegants) La bicicleta descansa fins la propera setmana http:\\[www.bttamer.org](www.bttamer.org)

---

### Post by pserra on 2007-10-02
Hola farigola,
 jo també tinc problemes amb una brother (MFC 210C), en Ubuntu.
Fa  6 mesos vaig començar en Ubuntu i em va costar moltíssim instal·lar controladors per la meva Brother,  gràcies a Cubells des de la Uoc desprès de molts missatges  vaig aconseguir que funcionés, encara no recordo com... Com que torno a tenir problemes, ahir vaig instal·lar els controladors de la meva impressora (que des de la Cups no els trobava) des de la mateixa pàgina que tu i no em va costar gens.Vaig descarregar els 2 arxius   per debian, quan vaig anar per obrir-los   em va obrir una finestreta   anomenada 'instal·lador de  paquets' vaig instal·lar els 2 paquets...
i ja va estar!!  desprès el Cups em va trobar el controlador....
El problema encara el tinc.... en windows també em peta... se'm queda netejant capçals....quina m******!  ... l'any passat el vaig tenir que portar al servei tècnic per el mateix...i ara ja ha passat la garantia...
No se si el meu missatge et serveix d'ajuda...
A reveure...

---

### Post by pserra on 2007-10-02
Disculpeu,
no m'he adonat que el problema estava solventat...
A reveure...

---

### Post by farigola on 2007-10-03
Gràcies PSERRA per el comentari. La veritat, jo sóc nou amb Linux i he de dir que li tinc moltes ganes. Gràcies al Forum i al personal que col·labora normalment i evidentment amb una mica d'esforç vaig configurant els meus equips domèstics.

Jordi.

---

### Post by Usuari on 2007-10-05
Hola pserra,

mira el wiki de [www.somgnu.cat](www.somgnu.cat) on s'explica com instal·lar una Brother MFC410CN; potser et servirà...

---

