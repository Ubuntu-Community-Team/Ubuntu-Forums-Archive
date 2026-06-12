---
title: "Eines de programació"
date: 2010-02-01
forum: Catalan Team
---

### Post by akyra on 2010-02-01
Volia preguntar quines eïnes es poden fer servir en linux per fer petites aplicacions, sobre tot formularis per BBDD, o "GUI".

Jo en aplicacions de feina he fet servir el .NET, però hi ha alguna alternativa lliure que tingui entorn amigable per començar a fer petites aplicaions i poder familiaritzar-me.

He sentit parlar de MONO, però les critiques d'alguns usuaris no eran molt bones, encara que no coneixo ningú que l'hagi utilitzat.

Moltes gracies.

---

### Post by pserra on 2010-02-01
> **akyra said:**
> Volia preguntar quines eïnes es poden fer servir en linux per fer petites aplicacions, sobre tot formularis per BBDD, o "GUI".

Jo en aplicacions de feina he fet servir el .NET, però hi ha alguna alternativa lliure que tingui entorn amigable per començar a fer petites aplicaions i poder familiaritzar-me.

He sentit parlar de MONO, però les critiques d'alguns usuaris no eran molt bones, encara que no coneixo ningú que l'hagi utilitzat.

Moltes gracies.
a mi també m'agradaria conèixer-ho, jo he tocat .net i a linux no he trobat rés tan senzill.... en un curs de oracle... vaig treballar amb jsp (java)... però per mi era força més complicat...

---

### Post by akyra on 2010-02-01
Estic mirant GTK, a veure si pot valer.

---

### Post by ifanlo on 2010-02-02
Hola!

Últimament he estat explorant una mica el llenguatge [Python]("http://www.python.org/"), i aquest m'ha portat a unes biblioteques gràfiques [wxWidgets]("http://wxwidgets.org/") (via [wxPython]("http://wxpython.org/")), i desde aquí la meva investigació m'ha dut al [Boa Constructor]("http://boa-constructor.sourceforge.net/"), un IDE a l'estil del Delphi.

Per ara, encara no l'utilitzo, estic amb el getting started del wxPython.

Per cert, la demo de wxPython és, en dues paraules, im-pressionant!  A l'Ubuntu, el paquet wx2.8-examples.

Igual us serveix alguna d'aquestes referències.

---

### Post by akyra on 2010-02-02
Moltes gracies, ara mateix l'he instal·lat.
Tens algun tutorial o alguna cosa senzilla per començar?

Gracies

---

### Post by ifanlo on 2010-02-03
> **akyra said:**
> Moltes gracies, ara mateix l'he instal·lat.
Tens algun tutorial o alguna cosa senzilla per començar?

Gracies

Si no tens gaires dificultats amb l'idioma de l'imperi els *getting started* de cada lloc tens un bon punt de partida.

En castellà he trobat bona documentació a:
[LIST]
[*]"Guía de aprendizaje de Python", del propi Guido Van Rossum (l'autor del llenguatge) y altres traduccions de la documentació oficial a [http://pyspanishdoc.sourceforge.net/index.html](http://pyspanishdoc.sourceforge.net/index.html)
[*]"[Aprendra a pensar como un programador con Python]("http://tutorialpdf.blogspot.com/2007/08/aprenda-pensar-como-un-programador.html")" (aquest m'ha encantat, és el meu preferit)
[*]"[Introducción a la programación con Python]("http://marmota.act.uji.es/MTP/teoria.shtml")", de la UJI, orientat a estudiants de primer cicle, no es gaire exhaustiu, però sí molt detallat i m'agrada pel gran volum d'exercicis proposats.
[*]"[Inmersión en Python]("http://es.diveintopython.org/")", breu, per a qui ja te clar els conceptes bàsics, ilustra molt bé sobre determinades tècniques avançades.
[*]"[Python para todos]("http://mundogeek.net/tutorial-python/")" també sembla interesant, però encara el tinc a la cua...  :-)
[/LIST]
Bé, amb això ja crec que tens sobre tropecentes hores d'estudi per davant.  :P

---

### Post by grind_lant on 2010-02-05
Jo no l'he provat, però he sentit meravelles del 'gambas':

[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

de totes maneres jo provaria Mono. Els que hi estan en contra és bàsicament més per temes de llicències que per qüestions de programació i usabilitat. 

El python està de moda ara, o bé també podries provar ruby, que si fa no fa és del mateix estil.

---

### Post by akyra on 2010-02-05
Gracies per les propostes.
Una pregunta, quin té la interficie gràfica més intuitiva?

---

### Post by PellRoja on 2010-02-06
A mi em van ensenyar JAVA  i em va anar força bé. Vaig poder crear la mateix aplicació que uns companys que l'havien fet amb .NET

Per programar interficies en Java m'ho van ensenyar amb NET Beans, que porta unes llibreries que es diuen swing, que només has de arrastrar i deixar anar els elements que vols a l'interficie.

També tens qtcreator, per crear aplicacions rapides amb QT4, les llibreries de KDE4 [http://qt.nokia.com/products/developer-tools](http://qt.nokia.com/products/developer-tools)

---

### Post by orestesmas on 2010-02-06
> **akyra said:**
> Volia preguntar quines eïnes es poden fer servir en linux per fer petites aplicacions, sobre tot formularis per BBDD, o "GUI".


Com és lògic tot depèn del tipus de coses que vulguis fer. Si és per això que dius, un "front-end" per accedir a bases de dades (suposo que mysql, postgres o similars), segurament la millor opció és fer servir un llenguatge "interpretat" com el python, perquè si t'emboliques amb coses com el c o c++ i no ho has fet mai, passaràs més estona provant d'entendre el llenguatge que no pas fent allò que tu vols fer.

Com a llenguatge de script el Python és una bona opció, però has de tenir en compte que l'elecció del llenguatge NO et força pas a escollir les llibreries gràfiques que has d'utilitzar, perquè avui en dia Python (i altres) tenen "bindings" o enllaços amb múltiples llibreries gràfiques. Així, pots usat wxWidgets, GTK o Qt, per exemple, i l'elecció d'una o altra és més aviat una qüestió de preferènies personals.

Jo t'aconsello que dónis una ullada a aquestes tres i després decideixis tu mateix.

Personalment jo utilitzo les Qt4 per fer petits programes. Són tècnicament molt avançades, són multiplataforma (Linux, Mac, Windows i dispositius mòbils), i tenen unes eines de desenvolupament professionals. Per exemple, per dissenyar interfícies gràfiques hi ha el Qt Designer, que és als repositoris d'ubuntu i te'l pots instal·lar sense problemes (paquet qt4-designer).

Les "bindings" entre python i qt es diuen "python-qt4". Hi ha un fum de tutorials sobre com programar amb python i qt, com ara 
[http://wiki.python.org/moin/PyQt](http://wiki.python.org/moin/PyQt). Només cal que googlegis una mica. També hi ha llibres, per si t'hi vols dedicar més seriosament: [http://www.qtrac.eu/pyqtbook.html](http://www.qtrac.eu/pyqtbook.html).

Que vagi bé.

---

### Post by akyra on 2010-02-08
Perdone-ho per no contestar a les vostres sugerencies, però acabo de ser pare un altre cop.

Respecte al que dius Orestemas, jo vaig treballar amb C a la universitat i vaig fer cursos després. Actualment estic desenvolupant aplicacions "Scada" les quals treballen amb entorn .NET.

Vaig pensar de que a vegades voldria fer petites aplicacions per fer GUI's, i també intentar treballar amb bases de dades SQL.

El que més em confon, és que quan estava a la universitat tot es feia amb UNIX, C i editor de texte.

Despre&#347; vaig treballar amb Visual Basic 6.0 i vaig fer un sistema Scada per a on treballava abans i finalment després vaig començar a collonejar amb .NET perquè el meu germa i treballa i em va semblar més o menys fàcil de començar i sobretot agradable visualment.

De fet buscava un entorn semblant, a on pugues arrastrar els objectes gràfics que volés i escriure el codi que calgués per fer-ho funcionar. Pel que em dius sembla que amb Qt4 seria el que estaria buscant.

Bé, aniré investigant a veure que m'agrada més.

Respecte al JAVA, també ho estic valorant, però realment no sé quina és millor elecció d'eina de progrmació. Bé, amb el C sembla que tot funciona en totes les plataformes.

Si algú té alguna altre sugerencia que m'ho faci saber.

Una pregunta, dins d'aquest forum, no hi ha un forum de programadors?

Moltes gracies

---

### Post by kimet on 2010-02-08
[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

---

### Post by papapep on 2010-02-08
> Una pregunta, dins d'aquest forum, no hi ha un forum de programadors?

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by ifanlo on 2010-02-09
> **akyra said:**
> Perdone-ho per no contestar a les vostres sugerencies, però acabo de ser pare un altre cop.

T'hem de felicitar o donar-te el pèsam?   :lolflag:

---

### Post by akyra on 2010-02-11
Sempre felicitar

---

