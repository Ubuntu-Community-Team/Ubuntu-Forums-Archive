---
title: "[SOLVED] Impressora SAMSUNG CLP-600N"
date: 2007-08-20
forum: Catalan Team
---

### Post by muleta on 2007-08-20
Ja fa estona que busco però no trobo la manera d'instal·lar l'impressora a UBUNTU. 

El sistema la detecta i reconeix però no m'accepta el controlador.

Algú em pot ajudar?.

Gràcies.

---

### Post by papapep on 2007-08-20
Segons el que diu aquí t'hauria de funcionar gairebé correctament.:

[http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-600n](http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-600n)

En tot cas per a poder-te ajudar explica què has fet i què t'ha contestat l'ordinador.

---

### Post by muleta on 2007-08-21
He cercat el fitxer foo2qpdl que em recomana la pàgina i l'he descarregat a l'escriptori.

He connectat l'impressora.

He anat a Synaptic i li he fet buscar foo2qpdl.

Quan m'ha aparegut en la columna de l'esquerra, l'he marcat i he activat l'única opció que em permet synaptic, que és Refrescar.

Ja no sé què més he de fer, però l'impressora no va.

Tant fàcil com era amb els instal·ladors de Windows...:(

---

### Post by papapep on 2007-08-21
Bé, no acabo d'entendre ben bé què has intentat fer, però és igual.
Mira, abans que res t'has d'oblidar completament dels procediments habituals al món Windows. Això és, i per sort, un món totalment diferent.

A la pàgina dels desenvolupadors del controlador: [http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/) hi ha un procediment molt concret i clar de com instal·lar-lo. Jo ho he provat al meu ordinador, tot i que no tinc cap Samsung, i s'instal·la correctament.
També aconsellen fervorosament, com ja veuràs remarcat en vermell, no fer servir les versions del controlador que són als repositoris de les distribucions, en el nostre cas Ubuntu.

Torna a començar de cero: fes-li un cop d'ull al document, i si tens dubtes planteja'ls. 
Veuràs com te'n sortiràs.

---

### Post by muleta on 2007-08-21
És que no entenc res de res.

Jo no sóc informàtica i la única cosa que he tret en clar de la guía ubuntu és que els programes s'han d'instalar a través de Synaptic o d'afegir/eliminar.

Cap de les dues opcions no em funciona en aquest cas, ni per a instal·lar JAVA, o Flash...

He esborrat el foo2qpdl que tenia descarregat en l'escriptori i l'he tornat a descarregar de l'enllaç que tu em dones. Tant si el descarrego per Administrador d'arxius com si el deso en el disc em queda a l'escriptori.

Una vegada allà, em diu el manual d'instal·lació que l'he de "compilar". Què vol dir això?. Ja no sé continoar perque les instruccions, a part de ser en anglès, semblen donades per a programadors o per a treballar desde la BIOS i jo estava molt ben acostumada als executables automàtics. Cap Ajuda de Ubunto no m'explica com s'ha de *compilar* a través de Synaptic no m'apareix com a opció dins del programa.

Si calen tants coneixements de programació, descobreixo que potser Linux no és per a mi. De moment, tot són obstacles. Em sap greu però l'havia de conèixer...:(

En fí, tú no en tens la culpa. Gràcies per intentar ajudar-me.

---

### Post by papapep on 2007-08-21
No t'atabalis, que t'ho diu pas per pas! :-D
Entenc la desorientació, però veuràs que no és tant, ni de bon tros, com sembla.

Tot això que hem de fer, no passaria si la teva impressora fos un pèl més "comuna" (no t'estic culpant, és una constatació d'un fet), ja que el controlador ja seria "dins" linux.

Mira, comença teclejant a un terminal (bé, de fet et serà més pràctic copiar i enganxar, així no cometràs errors tipogràfics):

```
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
```

---

### Post by muleta on 2007-08-21
Després del text que hi apareix?. Bé, ja està. I ara?.

De fet, el driver de l'impressora ja porta l'instal·lació per a Linux, però s'ha de fer a través del root i em fa molta por, no sé ni què és ben bé això.

---

### Post by papapep on 2007-08-21
Res, no pateixis. No sé d'on has tret les instruccions que comentes, però oblida-les.

Ara toca descomprimir el fitxer que has descarregat i entrar dins el directori per, com tu bé has dit abans, compilar el controlador:

```
tar zxf foo2zjs.tar.gz
```

Això t'haurà creat un directori de nom foo2zjs amb tots els fitxers ja descomprimits.

Ara hi entres:

```
cd foo2zjs
```

Ara toca compilar :-) (si aquest següent pas et falla, no pateixis, és que et falten un parell de paquets per a poder compilar, ara ho arreglarem. Si pots, perfecte).

```
make
```

Continuarà... ;-)

---

### Post by muleta on 2007-08-21
Què he de fer amb tots aquests codis que em dones?, escriure'ls en el mateix terminal d'abans?.

I sobre les teves indicacions intercalades amb els codis, hi tenen relació?. Perque jo no veig que estiguin parlant de la mateixa cosa.

Ja he après que compilar és convertir un codi font en fitxer executable. Quines ganes de complicar-nos la vida!. No li trobo el sentit.

M'agradava més que m'ho donéssin tot fet i només haver de pulsar una tecla.

Respecto que els informàtics, analistes i programadors trobeu gust a jugar-hi però no és la meva feina i dubto que trobi tot el temps que em caldria per fer-ho, quan se'm acabin les vacances.

Hi ha d'haver alguna manera més fàcil de poder instal·lar controladors i aplicacions...

Entenc que el pc hauria de ser una eina per agilitar processos, no un entreteniment.

De veritat que em cal aprendre a treballar amb codis font si vull continoar a Ubuntu?.

---

### Post by papapep on 2007-08-21
Noia, no se. Planteja-t'ho. 

La qüestió radica en que et sentis a gust. Si no t'hi sents, el qual reiteres als teus comentaris, fes el que creguis adient.

Els comentaris que faig entre les ordres de terminal són per explicar-te què estem fent, a fi de que entenguis una mica el procés. Res més. Si vols m'ho estalvio i punt.

I si, les ordres les has d'anar enganxant al terminal (d'un en un) i prement intro per a executar-les.

Però insisteixo, ningú t'obliga a res. Si segueixes amb l'Ubuntu estarem molt contents (la comunitat, vull dir) i estic segur que en un temps relativament curt, quan vegis que funciona, és estable i moltes coses més, t'hi sentiràs bé. Però queda-t'hi per que vols, no per cap altra cosa.

Apa, ja diràs el que vols fer, seguim? :-)


PD Respecte la teva última pregunta sobre el codi font: només en casos excepcionals. I això que estem fent són 5 ordres que si no fossis tan novella en menys de 3 minuts tindries acabades, t'ho asseguro.

---

### Post by muleta on 2007-08-21
Sí, sí... A veure... És que és tot tan nou i diferent...

Això de l'estabilitat és molt important, a més de la seguretat i la despesa de recursos. Potser cal que ho segueixi intentant, mentre trobi mestres amb la teva paciència.

Torne-m'hi!

Ara ja ho he entès, és que sóc una mica ase.

Fet tot el que m'indicaves, em surt això:

make: *** [all-test] Error 1
xxxxxxxxx:~/foo2zjs$

Crec que he arribat al punt que havies previst. Què més he de fer?.

---

### Post by papapep on 2007-08-21
Però un cop has executat el "make" han començat a aparèixer paraules en arameu i xinés (és broma, em refereixo a un porró de frases en ang&#314;ès) per la pantalla? O et surt directament el que m'has posat?

Talla la resposta del terminal i enganxa-la aquí (és igual que sigui llarga).

---

### Post by papapep on 2007-08-21
Escolta una cosa, com que estem treballant, diguem-ne, "en directe", potser seria adient que ens connectessim per IRC a fi d'agilitzar el tema. Saps connectar-te a un canal de xat?? (no t'ofenguis, no se el que saps i el que no)

A ubuntu.cat, tens indicacions de com connectar-te al canal dels ubuntaires en català (ubuntu-cat).

T'ho dic perquè seria molt més fàcil de fer-ho tot plegat.

Sinó cap problema, seguim així.

---

### Post by muleta on 2007-08-21
No tinguis por d'ofendre'm, sé com és això de no saber amb qui es parla. A més, és veritat que no en sé res de xats. Com que a Windows són tan insegurs, no hi havia entrar. Només al d'Skype.

Però em puc informar. Mentre busco i ho preparo, t'enganxo la resposta del terminal:

--18:44:20--  [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
           => `foo2zjs.tar.gz'
Resolent foo2zjs.rkkda.com... 74.208.41.246
S'està connectant a foo2zjs.rkkda.com|74.208.41.246|:80... conectat.
HTTP: Petició enviada, esperant resposta... 200 OK
Longitud: 1,456,909 (1.4M) [application/x-tar]

100%[====================================>] 1,456,909     13.51K/s    ETA 00:00

18:44:39 (74.89 KB/s) - s'ha desat «foo2zjs.tar.gz» [1456909/1456909]

xxxxxxxxxxxxxxxxxxx:~$ tar zxf foo2zjs.tar.gz
xxxxxxxxxxxxxxxxxxx:~$ cd foo2zjs
xxxxxxxxxxxxxxxxxxx:~/foo2zjs$ make
#
# Dependencies...
#
      ***
      *** Error: /usr/include/stdio.h is not installed!
      ***
      *** Install Software Development (gcc) package
      ***
make: *** [all-test] Error 1
xxxxxxxxxxxxxxxxxxx:~/foo2zjs$ 


Nota: Ja deus haver deduït que les xxxxxx substitueixen el meu identificatiu.

---

### Post by papapep on 2007-08-21
Perfecte, ja sé on som:

Ara toca instal·lar els paquets per a poder compila,r que no tens instal·lats:

> sudo aptitude install gcc build-essential

(Et demanarà la teva contrassenya personal per a poder instal·lar-los.)

Per accedir al canal ubuntu.cat, no sé si et funcionarà clicant damunt aquest enllaç:

irc://irc.freenode.org/ubuntu-cat (prova a copiar-lo a una finestra nova del navegador)

a mi em funciona, però no sé si tindràs l'equip configurat per que t'ho faci.

---

### Post by muleta on 2007-08-21
No, no m'ho permet. Em surt el mateix avís que quan ho he intentat desde la pàgina d'ubuntaires.

Tinc per norma deixar fora totes les opcions relatives a xats, quan instalo o configuro coses. Ara que sóc a Linux, m'ho replantejaré.

Després d'un llarg treball descarregant 98 Mg, tinc el terminal aturat a: :~/foo2zjs$.

He connectat l'impressora, per si la vol instal·lar...

Què més vé?.

---

### Post by papapep on 2007-08-21
Ah! Però només és un avís :-D Si li dius que si, segur que t'obrirà el gaim (el programa de xat).

Au, prova-ho, que hi som uns quants.

Per cert, jo m'esperaria a connectar la impressora a haver acabat el procés.

---

### Post by papapep on 2007-08-21
Mentrestant, torna a provar a fer el :

```
make
```

a veure si ara funciona. No t'espantis si està una estoneta treient coses rares per la terminal.

---

### Post by muleta on 2007-08-21
Va fent.

No, no m'instala res. Però ja he instal·lat el Kopete que, si trobo la ruta per a obrir-lo, dec haver de configurar...

---

### Post by papapep on 2007-08-21
> No, no m'instala res

És que encara no estem!! Això de fer de servei tècnic per fòrum és inacabable!

> Però ja he instal·lat el Kopete que, si trobo la ruta per a obrir-lo, dec haver de configurar...

Tens instruccions per a configurar-lo aquí: [https://wiki.ubuntu.com/CatalanTeam/InstruccionsXatKopete](https://wiki.ubuntu.com/CatalanTeam/InstruccionsXatKopete)

---

### Post by papapep on 2007-08-21
Tema solventat a l'irc seguint estrictament les passes que indiquen a: [http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

---

