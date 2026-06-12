---
title: "Escoltar música i películes amb bluetooth"
date: 2009-02-03
forum: Catalan Team
---

### Post by laieta on 2009-02-03
Bon dia.

Encara soc massa passarell amb l'Ubuntu i encara que busco pels fòrums no m'acabo d'aclarir del tot. Ara la pega que tinc és que m'aniria bé poder escoltar música mp3 o veure pel·lícules, tant en DVD com DIVX, i no hi ha manera de fer que en els diferents programes que utilitzo això es pugui configurar.

De fet els auriculars els tinc ben aparellats i em funcionen amb el Skype.

Si a algú se li acudeix una solució...
Gràcies

---

### Post by SiscoGarcia on 2009-02-03
Cap problema, laieta, per aquí em sembla que hi hem passat tots. Potser et cal entendre que els formats mp3 i divx són propietaris, de manera que d'entrada amb ubuntu no hi ha els còdecs que et permeten llegir aquests formats ja que tot el que s'hi inclou és de codi obert. La solució és afegir-hi els "ubuntu-restricted-extras"; això és, obrir una consola (Aplicacions>Accessoris>Terminal) i afegir-hi la comanda "sudo apt-get install ubuntu-restricted-extras" (sense cometes). Et demanarà la teua contrasenya, l'escrius (no es veurà res) i baixarà i instal·larà els paquets.

En principi ja estarà fet, però potser et cal alguna cosa. Si mires d'obrir algun fitxer d'aquests amb el reproductor de pel·lícules o d'àudio i no hi és algun paquet, ja et demanarà d'instal·lar-lo.

Fàcil, no?

EDITO: tot això si fas servir ubuntu (gnome), amb altres sabors els programes seran diferents però no gaire ;)

---

### Post by laieta on 2009-02-03
Gràcies per la resposta i l'explicació Sisco. El problema no el tinc en el format de la música o del vídeo, sinó en poder-ho escoltar a través d'un auricular bluetooth. El que tinc em funciona amb el Skype però no se com configurar-lo en el Totem, VLC, etc.

Gràcies.

---

### Post by SiscoGarcia on 2009-02-03
Vols dir que el problema no és de configuració del dispositiu; és a dir, si vas a la icona del bluetooth i pitges amb el botó secundari et dóna l'opció de configurar un dispositiu nou. Això ja ho has fet? Dono per fet que sí. Pots mirar-te la configuració? Et detecta els auriculars? Suposo que sí perquè ho has aconseguit amb l'Skype, però continua detectant-te'ls?

A tot això, laieta, sigues benvinguda al fòrum! Per cert, passa't pel [fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") i explica'ns alguna cosa; i ja que hi som, fes una ullada al [fil d'iniciació]("http://ubuntuforums.org/showthread.php?t=599965") per saber com funcionem ;)

---

### Post by laieta on 2009-02-04
Bon dia.

Sisco, ja he fet els deures :)

Teòricament el dispositiu funciona, està ben reconegut i amb el Skype no falla.

Crec que el que necessito és un programa que em permeti seleccionar l'auricular bluetooth com a dispositiu de sortida d'àudio, enlloc dels altaveus o els auriculars amb cable. He provat diferents programes sense sort. Si hi hagués manera d'associar els auriculars bluetooth a l'ALSA podria ser una alternativa, però no se com fer-ho.

Gràcies

---

### Post by SiscoGarcia on 2009-02-05
No ho he provat però googlejant una mica he trobat [això]("http://despuesdegoogle.com/2007/08/14/musica-sin-cables-auriculares-bluetooth-en-linux/") i [això altre]("http://www.ubuntu-es.org/index.php?q=node/64681"). Tot a partir d'[aquesta entrada]("http://www.google.es/search?hl=ca&client=firefox-a&rls=org.mozilla%3Aca%3Aofficial&hs=QPn&q=auriculares+bluetooth+ALSA&btnG=Cerca&meta=") al google.

Espero que t'ajudi ;)

---

