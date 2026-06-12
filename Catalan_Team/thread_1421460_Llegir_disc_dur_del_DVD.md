---
title: "Llegir disc dur del DVD"
date: 2010-03-04
forum: Catalan Team
---

### Post by jinglada on 2010-03-04
El meu DVD-R5200 (HDD + DVD Recorder), marca Prinston, s'ha mort perquè la placa frontal falla i segons el SAT no es troba el recanvi. 

Voldria recuperar els vídeos gravats al disc dur. L'he connectat per USB però a '/media' no apareix. 
A 'Utilitat de discs Palimpsest' diu: Disc dur de 250 GB / WDC WD25 00BB-55RDA0 / Sense partir / No reconegut / L'SMART no és disponible. /dev/sdb

Què faig? Gràcies.

---

### Post by quitus on 2010-03-06
Potser el disc dur no està alimentat, podries obrir-lo i comprovar l'alimentació amb un tester.

salut.

---

### Post by jinglada on 2010-03-07
> **quitus said:**
> Potser el disc dur no està alimentat, podries obrir-lo i comprovar l'alimentació amb un tester.

salut.

Gràcies quitus per la resposta. 
El disc és un IDE de 3,5".
La placa frontal del DVD que falla, és la que transmet les ordres de comandament.
Muntat en el DVD, el disc dur, si que estava alimentat ja que al posar el DVD en marxa, responia al test inicial rodant igual que feia el lector-gravador.

Tret del DVD i muntat en una caixa externa amb connexió USB, degudament alimentada passa el que dic al missatge anterior.

Ara l'estic veient en el GParted i diu: /dev/sdb (232.88 GiB), partició, sistema de fitxers, no assignat.
A informació del dispositiu diu :
Model: WDC WD25 00BB-55RDA0 
Mida: 232.88 GiB
Camí: /dev/sdb
Tipus d'etiqueta de disc: desconegut
Capçaleres: 255 
Sectors/pista: 63
Cilindres: 30401
Sectors totals: 488392065

En aquest disc hi tinc gravats, passats del vídeo, un futimé de concerts de "Jazz en la 2" i també del "Jazz & Co" del 33 i no m'agradaria haver de torna a gravar-los.

No hi cap software que pugui accedir a aquest disc?

---

### Post by wgarcia on 2010-03-08
Hi ha diversos programes, alguns et recuperen la partició si la veuen i uns altres intenten recuperar les dades. 

La pàgina en anglès:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

et dóna diverses alternatives.

---

### Post by jinglada on 2010-03-08
> **wgarcia said:**
> Hi ha diversos programes, alguns et recuperen la partició si la veuen i uns altres intenten recuperar les dades. 

La pàgina en anglès:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

et dóna diverses alternatives.

Gràcies wgarcia. M'ho miro i ja informaré... o preguntaré més ;)

---

### Post by jinglada on 2012-02-11
Després de gairebé dos anys he decidit reintentar recuperar els videos gravats en aquest HD del DVD. 
Vull provar l'Ubuntu-Rescue-Remix i al web [http://ubuntu-rescue-remix.org/node/466](http://ubuntu-rescue-remix.org/node/466), que és on hi ha la versió per al Lucid, hi llegeixo:
-----------------------------------
*** Metapackage ***

Would you prefer to work with a full graphical interface?

The live environment has a very low minimum requirement due to the fact that there is no graphical interface (powerful command-line only). If you prefer to work in a graphical environment, a metapackage is available which will install the data recovery and forensics toolkit onto your current Ubuntu Desktop system.
-----------------------------------
Em podeu dir, please, com es fa per a obtenir el "metapackage" i instal·lar-lo?
Gràcies a la bestreta.

---

### Post by jinglada on 2012-02-11
> **jinglada said:**
> Després de gairebé dos anys he decidit reintentar recuperar els videos gravats en aquest HD del DVD. 
Vull provar l'Ubuntu-Rescue-Remix i al web [http://ubuntu-rescue-remix.org/node/466](http://ubuntu-rescue-remix.org/node/466), que és on hi ha la versió per al Lucid, hi llegeixo:
-----------------------------------
*** Metapackage ***

Would you prefer to work with a full graphical interface?

The live environment has a very low minimum requirement due to the fact that there is no graphical interface (powerful command-line only). If you prefer to work in a graphical environment, a metapackage is available which will install the data recovery and forensics toolkit onto your current Ubuntu Desktop system.
-----------------------------------
Em podeu dir, please, com es fa per a obtenir el "metapackage" i instal·lar-lo?
Gràcies a la bestreta.

Perdoneu. L'acabo de veure al Synaptic i ja l'estic instal·lant.

---

### Post by jinglada on 2012-02-26
Finalment ho estic recuperant. Ja he vist trossos de vídeos i crec que tindré una feinada a ajuntar els fragments però tindré l'avantatge de tenir-ho a l'ordinador.

1) Amb successives passades estic creant una imatge del HD del DVD en un altre HD extern, amb la comanda *sudo ddrescue -r 3 -C /dev/sdb /media/Dades/image /media/Dades/logfile* 

2) Estic obtenint fitxers *.mpg* amb *photorec /log /d /media/Dades/fotorec image*

Ja informaré quan acabi i si tot va bé ja posaré el *[Solved]*.

---

### Post by jinglada on 2012-02-26
El *ddrescue* és molt lent, 840 kB/s de mitjana, que per les 250 GB del HD, representa unes 83 hores. En canvi el *photorec* va tardar 8126 segons per a 59 GB, o sigui unes 9,6 hores per a les 250 GB.

Hi ha alguna manera de poder dedicar més recursos al *ddrescue* per a fer-lo anar més ràpid?

En el següent àlbum [http://ubuntuforums.org/album.php?albumid=2465](http://ubuntuforums.org/album.php?albumid=2465) hi ha dues impressions de pantalla referents als recursos i processos quan solament funciona el *ddrescue.*

Obro un altre fil amb el tema dels recursos.

---

### Post by jinglada on 2012-02-28
Enganxo els fitxers de l'àlbum del post anterior per a facilitar-ne la lectura.

---

