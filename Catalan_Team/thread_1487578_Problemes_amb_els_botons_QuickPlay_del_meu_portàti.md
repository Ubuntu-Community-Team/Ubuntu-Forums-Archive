---
title: "Problemes amb els botons QuickPlay del meu portàtil HP"
date: 2010-05-19
forum: Catalan Team
---

### Post by albertdelleida on 2010-05-19
Hola a tots i totes,

us escric aquest missatge perquè tinc uns petits problemes amb els botons QuickPlay del meu portàtil HP. 

Tinc un HP Pavilion dv5 i justament damunt del teclat hi ha uns botons QuickPlay per controlar el volum i encendre o apagar el WiFi (entre d'altres). Aquests botons estan il·luminats per una llum blanca (i el botó del WiFi blava) que a l'apagar-los es tornen vermells. 

El tema és que des de que vaig instal·lar l'Ubuntu 10.04 aquesta el canvi de colors no em funciona, si bé es cert que els botons si que funcionen ja que puc controlar el volum. En principi no hauria de ser cap inconvenient, però justament el botó WiFi, il·luminat de color blau va fent constant-ment pampallugues amb color vermell i arriba un cert punt que molesta a la vista (quan estic reproduint pel·lícules a l'ordenador és força molest). Quan tenia l'Ubuntu 9.10 aquest problema no em passava, els botonets funcionaven correctament. 

A algú més l'hi ha passat? Algú em pot donar un cop de mà?

Altre cop, moltes gràcies per tot! :)

---

### Post by lluisalguero on 2010-05-20
Jo tinc el mateix portàtil i el botó del wifi no em fa pampallugues, però quan el toques per activar/desactivar, de tant en tant fa el burro...igual que el del touchpad

---

### Post by albertdelleida on 2010-05-20
Si, a mi també em fa tonteries el botó del touchpad... en fi... espero que sigui qüestió d'actualitzar algun paquet :P

---

### Post by pelai21 on 2010-05-22
Jo tinc un hp dm3. He tingut molts problemes amb el botó del touchpad, que era impossible desactivar. Utilitzo un processador de textos i la hiper-sensibilitat del botó m'impedia treballar amb comoditat. D'altra banda, el Lucid em va desactivar la barra lateral que permet desplaçar-se verticalment per les finestres. 

El problema de la sensibilitat l'he resolt amb un scrip que em desactiva el touchpad quan em fa falta. I el de la barra lateral afegint a les fonts de programari el pre-proposed kernel packages. Igual, això us pot servir per vosaltres.

---

### Post by albertdelleida on 2010-05-22
El botó del touchpad també m'està donant bastants problemes. Després de desactivar-lo i tornar-lo a activar no em funciona la resta del teclat. Provaré en instal·lar el pre-posed kernel packages i us diré que tal. 

Per cert, a algú se li ha acudit una solució pel que fa als problemes amb els botons QuickPLay? Merci.

---

### Post by albertdelleida on 2010-05-22
Perdona per la meua ignorància però, com ho faig per a instal·lar pre-proposed kernel packages?

---

### Post by pelai21 on 2010-05-22
[https://launchpad.net/~kernel-ppa/+archive/pre-proposed?field.series_filter=]("https://launchpad.net/%7Ekernel-ppa/+archive/pre-proposed?field.series_filter=")

Aquí hi trobaràs instruccions sobre com fer-ho.

---

### Post by albertdelleida on 2010-05-24
Merci! Tan aviat com pugui m'hi poso i us explico el què! :)

---

### Post by albertdelleida on 2010-05-24
Ho he intentat instal·lar seguit els passos i no ho aconsegueixo. Segons he entès he d'escriure al terminal: 

[I]deb [http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu](http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu](http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu) lucid main [/I]

Però em surt això:

[I]albert@lordinadordelalbert:~$ deb [http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu](http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu) lucid main 
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found[/I]

Alguna idea? :confused:

---

### Post by wgarcia on 2010-05-25
Aquestes línies són per afegir aquests fonts de programari al teu sistema, no per a donar-les a la línia de comandes. El procediment recomanat és entrar el següent a la terminal:

sudo add-apt-repository ppa:kernel-ppa/pre-proposed

Després actualitzes i et baixes l'actualització proposada per aquest equip:

sudo apt-get update

Ara bé, si vols després treure aquesta font i tornar a les actualitzacions normals del nucli, hauràs de deshabilitar aquesta font des de Sistemam -> Font de programari -> Altre programari o editant /etc/apt/sources.lst i esborrant les línies que vas posar en el teu article anterior.

---

### Post by albertdelleida on 2010-05-25
Gràcies per la informació! Ja us vaig comentar que sóc un novell i encara hi ha coses que no domino gaire. He afegit les noves fonts de programari al meu sistema i m'he baixat les actualitzacions que m'oferia però, res de res. El teclat continua desactivant-se un cop després de desactivar i tornar a activar el botó del touchpad, així que he tornat a desactivar les fonts de programari.

Algú té alguna idea de com poder solucionar aquest petit però molest problema?

Em recomaneu que mantingui aquesta nova font de programari 
[I]deb [http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu](http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu)  lucid main 
[/I]o pel contrari creieu que val més la pena mantindre-la desactivada?

Merci a tots un altre cop!

---

### Post by wgarcia on 2010-05-25
Si no t'ho ha arreglat de moment potser és millor tenir-la desactivada, perquè es tracta d'una actualització del nucli que està treballant l'equip de nucli però que encara no es considera que s'hagi d'oferir a les actualitzacions, per tant pot tenir encara alguna inestabilitat que ho desaconselli.

---

### Post by albertdelleida on 2010-05-25
D'acord! Ja l'he desactivada. Creus que pot passar alguna cosa greu a l'haver-me baixat les actualitzacions que m'aconsellava o puc estar tranquil? 

A més, des de Sistema -> Font de programari -> Altre programari, al desactivar la font i tancar la finestra em demanava actualitzar, m'ha sortit un error de no s'ha trobat el servidor (que ara no recordo quin era perquè ja ho he tancat). Amb tot, quan he tornat a obrir font de programari ja m'ha sortit desactivat. Deu estar bé, no?

Merci per tot! :P

---

### Post by wgarcia on 2010-05-25
La pregunta és si t'ha acabat d'instal·lar el nucli del PPA o no. Per veure quin nucli tens instal·lat pots donar la següent instrucció:

uname -a

i posar la línia d'informació que et surt. El nucli actual de Lucid és:

2.6.32-22-generic #33-Ubuntu 

mentre que el que t'instal·la el ppa és:

2.6.32-22.34~pre201005061001 

En cas que encara et surti aquest es tractaria simplement de desintal·lar-lo des del synaptic (tot assegurant-se és clar que tens el de dalt instal·lat).

---

### Post by albertdelleida on 2010-05-25
Ho acabo de comprovar i tinc la 2.6.32-22.34~pre201005061001 

Em podries indicar com desinstal·lar-ho? Moltes gràcies per la vostra paciència, encara sóc molt novell però de mica en mica en vaig aprenent :)

---

### Post by albertdelleida on 2010-05-25
Ja està! Ja he desinstal·lat la versió ppa. Ho he fet remenant synaptic. En tot cas, la pregunta inicial continua oberta: algú sap com puc sol·lucionar els problemes amb els botons Quickplay i Touchpad del meu portàtil?

Merci a tots :)

---

### Post by wgarcia on 2010-05-26
Sembla que és un error conegut per a aquest model de HP i per als últims nuclis. 

Per al touchpad prova el següent. Esborra un arxiu des de la consola:

rm ~/.gconf/desktop/gnome/peripherals/touchpad/%gconf.xml

i surt de la sessió i torna a entrar. Mira si ara funciona el touchpad.

---

### Post by albertdelleida on 2010-05-26
Ho acabo de provar i tampoc funciona. És una llàstima. Creus que sortirà alguna actualització que solucioni el problema? El que és curiós és que amb l'Ubuntu 9.10 aquests problemes no em passaven :confused: per això m'estranya tant...

---

### Post by albertdelleida on 2010-05-26
Remenant pel Synaptic he trobat un paquet en l'apartat de Dispositius incrustats anomenat libts-bin que no tinc instal·lat (només tinc instal·lat el paquet tsconf) Creieu que puc trobar aquí la solució als meus problemes?

---

### Post by wgarcia on 2010-05-26
Una pregunta tonta: des d'un CD Life de Lucid Lynx (és a dir el CD d'instal·lació d'Ubuntu) tampoc et funciona?

---

### Post by albertdelleida on 2010-05-26
Doncs no ho sé... Després ho provo i et comento a veure :)

---

### Post by albertdelleida on 2010-05-27
Encara no ho he pogut provar. Tinc el CD d'instal·lació a Lleida i ara mateix estic a Barcelona. El que sí que he provat és d'entrar a la partició del Windows Vista i, curiosament, allà funciona perfectament tant els botons QuickPlay i el TouchPad. Encara més estrany... per tant he arribat a pensar que no sigui tema drivers d'HP que no estiguin instal·lats a l'Ubuntu 10.04, és possible?

---

### Post by pelai21 on 2010-05-27
Albert, jo també sóc novell, però si no m'equivoco, l'Ubuntu no fa servir drivers. Si el SO no et reconeix el maquinari, o ets un expert, o hauràs d'esperar a una pròxima actualització del nucli. Ja et vaig comentar que, en el meu cas, amb el pre-proposed kernel havia aconseguit solucionar alguns problemes. Et donaré dos consells més:

1. Prova d'instal·lar el programa gsynaptics. És un programa que trobaràs al synaptic que serveix per controlar el touchpad. Potser amb aquest programa obtens algun resultat. Ja t'aviso que, en el meu cas, no em va funcionar, però sé que d'altres que han tingut més sort.

2. Segona solució: si dius que l'Ubuntu 9.10 t'anava millor, per què t'encaparres amb la 10.04? Torna a la 9.10 i espera que la 10.04 estigui prou millorada com per reconèixer tot el teu maquinari. No cal anar a l'última. Del que es tracta és de tenir un SO de codi lliure que faci el que ha de fer. Jo mateix també vaig tenir problemes amb la 10.04 amb un ordinador fix que tinc. Al final no m'hi vaig trencar més les banyes i vaig fer marxa enrere. Problema solucionat!

De totes maneres, estigues tranquil, perquè el model d'ordinador que tens és força popular de manera que segur que hi ha gent treballant-hi. Tard o d'hora, de segur que se soluciona el problema. :)

---

### Post by papapep on 2010-05-27
Petita correcció, Pelai21: com tu bé dius, GNU/Linux té moltes coses incorporades com a mòdul al nucli del sistema, per a les quals no li calen controladors externs, però és clar que sí que hi ha controladors per a tot el que no és dins el nucli. Bé, no per a tot, què més voldríem, però si per a bastantes coses. "Només" cal que el fabricant o algun voluntari amb coneixements i ganes hi posi el cervell i el temps ;)

Salut.

---

### Post by albertdelleida on 2010-05-28
Provaré d'instal·lar-me el programa gsynaptics, a veure si tinc sort. En tot cas, no crec que em torni a passar al 9.10 Sí bé és cert que en aquest tema (touchpad i botons quickplay no em donava problemes) la versió 10.04 -a nivell general- em funciona molt i molt millor. 

També és cert amb el que tu comentes, segurament m'haig d'esperar a alguna actualització i ja està. A més, si bé és un tema que em pot arribar a emprenyar en alguns moments puc treballar perfectament sense aquestes dues "aplicacions", tot i que a l'estar acostumat a tenir-les se'm fa estrany no poder-les utilitzar correctament! 

Merci a tots! :)

---

### Post by albertdelleida on 2010-05-29
Hola de nou. Acabo d'instal·lar-me el gsynaptics i continua sense funcionar. Res, a esperar a que surti alguna actualització. Merci a tots i si algú se n'assabenta de com solucionar el problema li agrairia molt que m'ho digues! Salut!

---

### Post by wgarcia on 2010-05-29
Una cosa que pots explorar és si la BIOS està actualitzada. Pots mirar si HP ha publicat una actualització de la BIOS i que la teva sigui més antiga. Normalment els programes d'actualització de la BIOS sols corren des del sistema operatiu de Microsoft, i en tot cas has d'anar amb compte d'instal·lar l'actualització que li toqui exactament al teu model.

---

### Post by albertdelleida on 2010-05-30
Merci per la resposta wgarcia, però crec que encara no em veig amb cor de posar-me a remenar la BIOS. Les vegades que he hagut de remenar la BIOS d'altres ordenadors estava molt perdut i sempre tinc por a fer algun disbarat :P però merci igualment pel consell :)

---

