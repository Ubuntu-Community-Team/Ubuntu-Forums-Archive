---
title: "Insta&#320;lar Amarok 1.4 a Jaunty Jackalope"
date: 2009-04-25
forum: Catalan Team
---

### Post by kukat on 2009-04-25
Salutacions!!

Anava a preguntar com s'insta&#320;lava la versió anterior a la 2.0 de l'Amarok, ja que no m'agrada gens la nova versió, i a més a més, als minuts de tindre la 2.0 funcionant... ja em va petar! :confused:

Bé, per a insta&#320;lar la 1.4 hi ha que fer el següent:

En una terminal ("Aplicacions", "Accessoris", "Terminal") escrivim:

**sudo gedit /etc/apt/sources.list**

Ens sortirà l'editor de Text. Afegim les següents línies al final del tot (les fonts d'on s'insta&#320;larà):

*#Amarok 1.4*
[I]deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main[/I]

A continuació, hi ha que afegir la clau per a poder insta&#320;lar-ho. Escrivim al Terminal:

[B]sudo apt-key adv --recv-keys --keyserver \
keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63[/B]

Després actualitzem i insta&#320;lem:

sudo apt-get update
sudo apt-get install amarok14

Hi ha que posar amarok14!!! :)

Salutacions!

---

### Post by PatrickVogeli on 2009-04-25
ostres tiu, moltes gracies, despres ho provare! La veritat es quel l'amarok 2 el trobo una cagada impresionant... han fet completament malbé el que considero que era el millor reproductor de música disponible... tant en linux, com mac, com windows..

salut!

---

### Post by LitusMayol on 2009-04-25
> **PatrickVogeli said:**
> ostres tiu, moltes gracies, despres ho provare! La veritat es quel l'amarok 2 el trobo una cagada impresionant... han fet completament malbé el que considero que era el millor reproductor de música disponible... tant en linux, com mac, com windows..

salut!

Quatre (enlloc de tres) quarts del mateix.

---

### Post by kukat on 2009-04-25
a mi també em sap molt mal com ha "evolucionat" l'amarok...haurien d'haver mantingut l'aspecte que tenia i anar desenvolupant-lo a millor, però crec que no han encertat......es una llàstima molt gran...Estic provant el Songbird també, però la llicència que inclou no m'ha fet molta gràcia!:)

---

### Post by albert-I on 2009-05-01
Suposo que coneixeu que moltes de les funcions que s'han perdut. Seran recuperades en pròximes actualitzacions.

---

### Post by orestesmas on 2009-05-03
Ui, a veure si ara resultarà que els més joves sou també els més conservadors...

1) La filosofia del programari lliure és "allibera aviat, allibera sovint". Amarok 2 és un canvi radical d'arquitectura interna respecte la 1.4. Si haguessin esperat a "tenir-ho tot lligat", probablement els desenvolupadors s'haurien mort abans.

2) Com diu albert-I, la interfície no està acabada, i poc a poc s'aniran incorporant coses que hi havia a la 1.4 i que ara per ara s'han deixat pel camí. De tota manera, els desenvolupadors ja adverteixen que NO TOT el que tenia la 1.4 es portarà a la 2, perquè hi ha coses que han descobert que es poden fer millor, o diferent:

> Not all of Amarok 1.4's features will necessarily return in Amarok 2. Many features will be ported over, a lot of new features will be added, and some old features will simply be dumped for good. Amarok 2 isn't simply a souped up version of Amarok 1, but it's almost completely a new program, and you can't expect it to work exactly like 1.x. If we wanted that, we could simply have taken 1.x and stuck a big "2.0!" logo on it, and be done with it. "

En [aquest enllaç]("http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html") expliquen quines característiques tornaran i quines no.

Jo de vosaltres em relaxaria i em tornaria a mirar amb calma l'Amarok 2. Passegeu-vos per la pàgina web, subscriviu-vos a "l'insider", comproveu que ara la base de dades pot suportar una quantitat enorme de fitxers sense arrossegar-se, descobriu els serveis web i tot el que us pot oferir la interfície basada en Plasma, les capacitats de "scripting", etc. Potser tot això no us és útil a vosaltres, però son definitivament millores i seran útils a molta gent.

I en qualsevol cas, si no necessiteu tot això, sempre es poden fer servir programes més senzills. El programari lliure té aquesta gràcia: et permet escollir. Ara be: jo no utilitzaria Amarok 1.4 perquè es basa en unes llibreries que aviat deixaran d'estar mantingudes i tot plegat esdevindrà una font de problemes més que de solucions.

---

### Post by LitusMayol on 2009-05-03
No no, si no diem (almenys jo) que en un futur el **Amarok2** no m'agradi més. 


Però ara per ara és un programa que a mi m'havia creat moltes espectatives que mesos després encara no ha complert i que està lluny, lluny de fer-ho. Que què era el que m'agradava del **Amarok 1.4**? Doncs la majoria de coses que han desaparegut de la 2. Potser per això el meu rebuig. Ja estic subscrit a l'*insider* i hi vaig llegint els canvis. Però segueixo pensant que li falta molt. S'ha fet un pas enrere per poder arribar més endavant del que s'havia arribat (o almenys això és el que jo entenc). Però per mi aquest pas ha sigut massa enrere. 

Això sí: he de dir que considero que manega amb molta més facilitat les biblioteques pesants (la meva té més de 10.000 cançons i anava volat). A veure si d'aquí un anyet (tan de bo abans) ja puc dir que em passo al 2!

---

### Post by kukat on 2009-05-04
Pense el mateix....i també per l'aspecte....:( no m'agrada l'aspecte que té!!! I no es pot canviar de ninguna forma (he vist que es poden canviar els botons del "Play" i això, però....)
Deurien de fer alguna cosa per als que gastem Gnome, ja que no queda gens bé. Al KDe guarden tots la mateix aparença, i quedarà la mar de bé (questió de gustos)

Salut!

---

### Post by kukat on 2009-05-05
mmmm.....he vist açò: [http://www.kde-look.org/content/show.php?content=93854&forumpage=0](http://www.kde-look.org/content/show.php?content=93854&forumpage=0)

i està molt molt bé!!!
però no se com s'insta&#320;la!! i mira que li he pegat voltes!!

Algun amant del Kde que tinga alguna idea de com insta&#320;lar-ho?

EDITO: Crec que no es pot insta&#320;lar....si no m'equivoque es una idea...no? xè! llàstima, estava molt bé!
Salut!

---

### Post by PatrickVogeli on 2009-05-05
no es pot instal·lar, ja que no existeix... kde4 brainstorm. És un conecepte només.

---

### Post by kimet on 2009-05-05
Prova "jajuk", un reproductor escrit en java molt complert però molt xucla-recursos, per ordinadors una mica potents.

Salut.

---

