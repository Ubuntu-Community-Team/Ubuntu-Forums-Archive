---
title: "arxius odt"
date: 2017-04-27
forum: Catalan Team
---

### Post by josep-maria on 2017-04-27
Tinc l'ubuntu 16.04.2 Xerus, Mate 1.12.1

No puc obrir cap arxiu .odt. Sí que puc obrir els .rtf i els .txt.

He reengegat el pc i tampoc no funciona.
Si canvio el nom del .odt per .rtf, surt un avís que diu: S'ha trobat un error de format del fitxer a 373,7(fila,columna).
Si el canvio a .txt, sí que l'obre, però surten milers de caràcters que no hi eren.
Em passa des d'avui a la tarda. No he fet cap actualització.

He provat de fer: sudo apt-get install --reinstall libreoffice
Les darreres línees de la resposta són:
S'està configurant libreoffice-sdbc-firebird (1:5.1.6~rc2-0ubuntu1~xenial1)…
S'està configurant libreoffice-sdbc-hsqldb (1:5.1.6~rc2-0ubuntu1~xenial1)…
S'estan processant els activadors per a libc-bin (2.23-0ubuntu7)…
pep@pep-System-Product-Name:~$ 

Suposo que ha anat bé, però segueixo sense poder obrir cap .odt.

---

### Post by wgarcia on 2017-04-28
Mira a veure què tens instal·lat de libreoffice, aquests dos paquets que et mostra a dalt no semblen ser els paquets principals de libreoffice. Per veure que hi ha instal·lat, des d'una terminal: 

```
dpkg -l libreoffice*
```

Si la sortida solt molt truncada perquè no es puguin veure els noms dels paquets, incrementa una mica l'amplada de la terminal (canviant-li la mida a l'escriptori).

---

### Post by josep-maria on 2017-04-28
pep@pep-System-Product-Name:~$ dpkg -l libreoffice*
Desitjat=desconegUt/Instal·la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió       Arquitectura Descripció
+++-==============-============-============-=================================
ii  libreoffice    1:5.1.6~rc2- i386         office productivity suite (metapa
un  libreoffice-ac <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-av <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-av 1:5.1.6~rc2- i386         GStreamer backend for LibreOffice
ii  libreoffice-ba 1:5.1.6~rc2- i386         office productivity suite -- data
ii  libreoffice-ba 1:5.1.6~rc2- i386         office productivity suite -- shar
ii  libreoffice-ba 1:5.1.6~rc2- i386         Database connectivity drivers for
un  libreoffice-bu <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-ca 1:5.1.6~rc2- i386         office productivity suite -- spre
ii  libreoffice-co 1:5.1.6~rc2- all          office productivity suite -- arch
ii  libreoffice-co 1:5.1.6~rc2- i386         office productivity suite -- arch
un  libreoffice-de <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-de <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-dr 1:5.1.6~rc2- i386         office productivity suite -- draw
un  libreoffice-em <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-ev <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-fi <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-fi <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-gc <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-gn 1:5.1.6~rc2- i386         office productivity suite -- GNOM
un  libreoffice-gr <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-gr <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-gt 1:5.1.6~rc2- i386         office productivity suite -- GTK+
un  libreoffice-gt <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-he <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-he 1:5.1.4-0ubu all          office productivity suite -- Cata
ii  libreoffice-he 1:5.1.4-0ubu all          office productivity suite -- Engl
ii  libreoffice-im 1:5.1.6~rc2- i386         office productivity suite -- pres
ii  libreoffice-ja 1:5.1.6~rc2- all          office productivity suite -- arch
un  libreoffice-ka <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-kd <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-l1 1:5.1.4-0ubu all          office productivity suite -- Cata
un  libreoffice-l1 <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-ma 1:5.1.6~rc2- i386         office productivity suite -- equa
un  libreoffice-my <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-of <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-og 1:5.1.6~rc2- i386         LibreOffice Impress extension for
ii  libreoffice-pd 1:5.1.6~rc2- i386         PDF Import component for LibreOff
un  libreoffice-pr <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-pr <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-re <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-re 1:5.1.6~rc2- i386         LibreOffice component for buildin
un  libreoffice-sc <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-sc <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-sc <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-sd 1:5.1.6~rc2- i386         Firebird SDBC driver for LibreOff
ii  libreoffice-sd 1:5.1.6~rc2- i386         HSQLDB SDBC driver for LibreOffic
un  libreoffice-sd <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-st 1:5.1.6~rc2- all          office productivity suite -- Bree
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-st 1:5.1.6~rc2- all          office productivity suite -- Gala
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-st 1:5.1.6~rc2- all          office productivity suite -- Huma
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-st <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-un <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-wi <cap>        <cap>        (no hi ha cap descripció disponib
ii  libreoffice-wr 1:5.1.6~rc2- i386         office productivity suite -- word
un  libreoffice-wr <cap>        <cap>        (no hi ha cap descripció disponib
un  libreoffice-wr <cap>        <cap>        (no hi ha cap descripció disponib
pep@pep-System-Product-Name:~$

---

### Post by wgarcia on 2017-04-28
Sembla que tens tot el necessari de libreoffice instal·lat (tot el que comença amb "ii" són paquets instal·lats). 

Prova d'obrir un fitxer odt des d'una terminal i mira si llença algun missatge d'error:

```
libreoffice fitxer.odt
```

des d'una terminal.

---

### Post by josep-maria on 2017-04-28
Diu que l' arxiu.odt no existeix.
He provat amb un parell de noms i sempre diu que no existeixen.

---

### Post by wgarcia on 2017-04-29
Has de posar primer a la teva carpeta d'inici (on s'obre la terminal) algun fitxer ".odt", o des de la terminal anar-te'n a una carpeta on hi hagi un fitxer d'aquest tipus, per exemple si tens un fitxer a "Documents":

```
cd /home/pep/Documents
```

o obrir la terminal en una carpeta on hi hagi un fitxer d'aquest tipus, o posar-li tot el camí al nom del fitxer perquè el trobi, per exemple si està a "Documents":

```
libreoffice /home/pep/Documents/fitxer.odt
```

---

### Post by josep-maria on 2017-04-29
Fent això que dius sí que puc obrir els arxius odt. 
Però si faig doble clic al seu nom, no s'obren.
Només no puc obrir l'arxiu odt que ha provocat tot aquest merder. Per tant, l'esborraré.
Però sí que caldria obrir la resta del odt fent-hi doble clic.

---

### Post by wgarcia on 2017-04-29
Quan fas doble clic sobre els fitxers "odt", dóna algun missatge d'error quan no els pot obrir?

---

### Post by josep-maria on 2017-04-30
No. Només surt el rellotge de sorra que va fent voltes vint segons, i prou.

---

### Post by wgarcia on 2017-04-30
No sé què pot estar passant, però si no tens massa configuracions pròpies del LibreOffice, pots provar de recrear el perfil de l'usuari, a veure si ho arregla. Per recrear el perfil d'usuari, tanca completament el libreofffice, i reanomena el perfil. Quan tornis a obrir el libreoffice, es recrearà. Per canviar el nom del perfil d'usuari:

```
 mv ~/.config/libreoffice/4 ~/.config/libreoffice/4.vell
```

Compte que si tenies configuracions pròpies, amb això és perdran. Encara hi seran a la carpeta "4.vell" si això no arregla el problema i vols recuperar les configuracions prèvies.

---

### Post by josep-maria on 2017-04-30
No sé si tinc cap configuració pròpia, perquè no sé què són les configuracions que dius.
Jo sempre feia doble clic al nom de l'arxiu i ja hi entrava. Com es fa per tancar completament el libre office? I això de reanomenar el perfil? I per tornar a obrir el libre office?

---

### Post by wgarcia on 2017-05-01
Si no has fet cap personalització al libreoffice, dons no tens configuracions. 

Per reanomenar el perfil, que en realitat és una carpeta dins de la teva carpeta d'inici, les instruccions són les indicades al meu missatge anterior.

Per últim per reiniciar el libreoffice, si tanques tots els documents i el tornes a obrir, es reiniciarà.

---

### Post by josep-maria on 2017-05-03
He fet  mv ~/.config/libreoffice/4 ~/.config/libreoffice/4.vell
he tornat a fer reinstall libre office
he fet apt autoremove
he reengegat el pc
Però encara no funciona.

---

### Post by wgarcia on 2017-05-04
Si cliques amb el botó dret del ratolí sobre un fitxer ".odt", què mostra a la primera línia? Hauria de mostrar quelcom com "Obre amb el LibreOffice".

---

### Post by josep-maria on 2017-05-04
Quan faig clic al nom de l'arxiu amb el botó dret surt aquest menú:

-obre amb caja.......................... no fa res
-obre amb atril........................... diu que no es pot obrir
-obre amb engrampa.................. diu que no es pot obrir
-obre amb writer........................ SÍ QUE FUNCIONA
-obre amb muntador.................. no fa res
-obre amb una altra aplicació:.... en surten moltes més

---

### Post by wgarcia on 2017-05-04
Fen el mateix que vas fer, és a dir clicant amb el botó dret de ratolí, escull ara "Propietats" al menú contextual que s'obre (en comptes d'"Obre amb..."). A la pestanya de "Propietats" que posa "Obre amb" mira quina aplicació és la que obre els odt per defecte, si no és el LibreOffice a aquesta pestanya pots escollir el LibreOffice a sota i canviar l'aplicació per defecte per a aquest tipus de fitxers.

---

### Post by josep-maria on 2017-05-05
Deia que era el caja, Ja hi he marcat el libreoffice, i ara ja va bé. Però jo no havia tocat pas res. 
Moltes gràcies.

---

### Post by wgarcia on 2017-05-06
Sí, és estrany que s'hagi canviat sol, potser l'ha canviat alguna actualització o alguna interacció estranya entre aplicacions.

---

