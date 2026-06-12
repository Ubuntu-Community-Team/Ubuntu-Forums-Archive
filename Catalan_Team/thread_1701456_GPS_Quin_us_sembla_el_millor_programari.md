---
title: "GPS: Quin us sembla el millor programari?"
date: 2011-03-06
forum: Catalan Team
---

### Post by joaquimrubio on 2011-03-06
Vull intentar fer funcionar el gps des d'Ubuntu, (fins ara ho he fet amb Windows i un programa de pagament), al Centre de Programari he vist diversos programes i al fòrum he comprovat que hi ha més gent que ho està fent.

Aleshores, la pregunta és:

Quin programa us sembla millor?

El meu GPS és un model per excursionisme de la casa Garmin, model Etrex Legend. Té uns quants anys si bé funciona perfecte.

EL que voldria fer és lo més normal de fer: 
1)Emmagatzemar a l'ordinador les rutes que gravo al gps quan camino. Baixar d'Internet el mapa de la zona i posar-hi la ruta.
2)Baixar rutes des d'Internet i baixar mapes des d'Interent i posar aquestes rutes als mapes i un cop fet això, passar-ho al gps.

Gràcies.

Joaquim.

---

### Post by Albert Que on 2011-03-06
a La Borrassa vam fer un curs d'això que demanes, a veure si aquí trobes el que necessites:
[http://www.slideshare.net/laborrassa/taller-gps](http://www.slideshare.net/laborrassa/taller-gps)
[http://www.slideshare.net/laborrassa/publicar-dades-google-gps](http://www.slideshare.net/laborrassa/publicar-dades-google-gps)

---

### Post by joaquimrubio on 2011-03-06
Gràcies, Albert, ara ho acabo de mirar, però no m'aclareix de tots els possibles, quin programa és més recomanable per la seva facilitat d'ús i opcions.

---

### Post by gunyoles on 2011-03-09
Jo feia servir el CompeGPS a windows i no hem queda mes remei que mantindre un portàtil vell amb Windows per fer-lo anar. No hi ha cap programa que el pugui substituir, però si no demanes gaire prova el Víking o si no el Tango.

---

### Post by endaco on 2011-03-09
Hola!

Jo tinc un Etrex Vista Hcx i utilitzo el Qlandkarte i per ara puc fer el mateix que feia amb el mapsource

Per instal·lar la ultima versió s'ha d'afegir un reposi tori

sudo add-apt-repository ppa:mms-prodeia/ppa
apt-get install glandkartegt glandkartegt-garmin garmin-forerunner-tools

he instal·lat els mapes topohispania

i tot funciona correcte

---

### Post by joaquimrubio on 2011-03-11
Gràcies, Gunyoles. Jo també tinc el CompeGPS però és el darrer programa que em queda amb Windows i m'agradaria fer-ho tot amb Ubuntu. He visitat planes web (els enllaços suggerits per l'AlbertQuè, de La Borrassa són excel·lents, en particular aquest [http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878](http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878)) i em sembla que es pot fer exactament el mateix. Però hi ha diversos programes i no sé quins s'han provat en aquest fòrum, voldria informar-me tant com pugui per reduïr el procés de prova-error fins esbrinar el que se m'adapta millor. M'apunto les teves recomanacions i revisaré el Víking i el Tango.

Gràcies, Edaco. Pel que he llegit revisant la web, a primera vista el Qlandkarte és el que em semblava millor. M'apunto el detall d'afegir aquest repositori que dius.

---

### Post by gunyoles on 2011-03-22
Hola 
joaquimrubio digues si has arribat a alguna conclusió, si has trobat algun programa que et faci el pes.

---

### Post by joaquimrubio on 2011-03-27
Hi segueixo treballant a les estones lliures, que aquests dies han sigut poques. 

Quan ho tingui tot més enllestit, comunicaré les conclusions, per limitades que siguin.

Segueixo agraint informació d'altres usuaris de gps amb Ubuntu.

---

### Post by joaquimrubio on 2011-04-03
Sento no poder donar gaire informació:
- De moment el Qlandkarte no el sé fer funcionar, ni tant sols aconsegueixo una cosa tant senzilla com descarregar trakcs des del GPS. 
- Tampoc he aconseguit que carregui mapes per a visualitzar-los. 
(Segons el meu sentit comú, fer funcionar el Qlandkarte seria **com a mínim** poder desarregar des del GPS o des d'Internet Tracks i Rutes, poder-les visualitzar sobre un mapa i poder-ho carregar tot al GPS. També, poder fer un esquema del desnivell i un càlcul del desnivell positiu i negatiu acumulat. I, finalment, poder imprimir tot aixó).

Descarregar tracks es por fer perquè el dia que l'informàtic me'l va instal·lar es van poder descarregar però després no ho he aconseguit cap més vegada. 

Els mapes, per sentit comú, penso que es deuen poder descarregar i visualitzar, però de moment, ni el dia que va venir l'informàtic ni després s'ha aconseguit res.

Agreuja el problema que el programa desconfigura una part que sé tornar a configurar, però no sé si també s'ha desconfigurat alguna altra part que ni sé com hauria de ser...

He obert un altre fil demanant un professor d'Ubuntu, fins que el trobi no crec que pugui avançar més. Deixo el fil obert per si algú hi fa alguna aportació. Quan aconsegueixi fer anar el Qlandkarte (o un altre) ho deixaré explicat en aquest fil i marcaré aquest fil com a "resolt".

---

### Post by Funk'u on 2011-04-06
Això que comenteu és per gestionar les dades de GPS des de l'Ubuntu, oi?, però puc utilitzar el netbook com a GPS? amb un mòdem USB  (o potser necessito algun altre tipus de maquinari), i algun programari adient, desconec si n'hi ha.

Per altra banda tinc una PDA amb antena GPS de fa uns anys, un Acer N35[ http://www.compsaonline.com/novetats/Hardware/n35.aspx]("http://www.compsaonline.com/novetats/Hardware/n35.aspx") , que em preguntava si li puc instal·lar alguna distribució GNU/Linux, i si és així ficar-li també un programa GPS. Encara que no sé d'on trauria els mapes.






Salut!

---

### Post by gunyoles on 2011-04-06
pots fer servir el netbook com a gps sempre que tinguis una antena per rebre el senyal dels satèl·lits, pot ser via usb o pots connectar un gps dedicat al portàtil. Com a gps dedicat hem refereixo a qualsevol dels que es fan servir en muntanya o topografia, no pda's. (Magellan, Garmin, MobileMapper, Trimble, etc...)
D'aquesta manera fas servir el netbook com si fos la pda, però amb pantalla gran i molta més memòria per posar mapes en 3D, o fins i tot conexio wifi per treballar amb mapes en temps real de l'ICC o Google.
En quan a fer servir Linux en una pda, pots trobar alguna cosa però depèn molt del maquinari de la teva Acer.
Jo hem decanto per la primera opció ja que la qualitat d'imatge amb 10" no ho trobaràs amb cap pda.

---

### Post by pserra on 2011-04-07
Em surt aquest error (la darrera linea) al engegar l'ubuntu, el darrer dia al engegar se'm va parar el portàtil al tenir la bateria a 0...hi ha alguna manera senzilla de arreglar-ho?
Merci

---

### Post by Funk'u on 2011-04-07
Gràcies gunyoles, potser que utilitzi la primera part de la primera opció, per invertir el mínim de calés, que estem en crisi, en el referent va la PDA, és per treure'n algun profit.




Salut!

---

### Post by joaquimrubio on 2011-04-13
Bon dia, Funk'u.

Contesto el poc que sé: 

El que comentem és un programa que s'instal·la a l'ordinador i permet gestionar dades que un altre aparell, el GPS, ha emmagatzemat. O a l'inreves, dades disponibles al web poder-les transmetre a l'aparell GPS. 

El netbook es deu poder utilitzar com a GPS connectant-hi una antena GPS però deu ser molt incòmode de fer servir, tant en cotxe com caminant, no hi veig massa interés. I ignoro quin programari disponible per a aquesta funció hi ha. Amb una agenda electrònica (PDA) sí és pot fer, és més viable, però et recomano un aparell específic per a aquest ús. En el cas de la teva agenda electrònica, altre cop desconec quin programari hi ha disponible. 

Els mapes de Topohispania estan disponibles a Internet. M'ha semblat entendre que sí que és poden instal·lar a l'Ubuntu , però no sé com es fa.

No et sol·luciono gran cosa, ho sento.

---

### Post by Funk'u on 2011-04-13
Hola joaquimrubio, la veritat és que m'has donat bones idees, miraré això que dius del Topohispania, i alguna "distro" lleugera.


Merci, salut!

---

### Post by joaquimrubio on 2012-06-02
Abandono l'intent de fer anar al GPS amb Ubuntu, hi he perdut un munt d'hores i no ho aconsegueixo. 

Bona sort.

---

