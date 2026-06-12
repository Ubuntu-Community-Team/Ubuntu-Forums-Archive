---
title: "Webcam VGP-VCC7 a un Vaio PCG-4N2M es desconfigura sola"
date: 2011-02-13
forum: Catalan Team
---

### Post by 19preguntes on 2011-02-13
Hola,
cada cop que engego l'ordinador em trobo amb què l'Ubuntu ha deixat de detectar la webcam integrada. He de reiniciar l'ordinador amb Windows (tinc una partició del discdur on encara conservo Windows), engegar qualsevol programa que faci anar la webcam i tornar a reiniciar l'ordinador amb Ubuntu. Llavors la càmara funciona amb l'Ubuntu perfectament. Com podeu imaginar, és una mica pesat fer tota aquesta moguda cada cop. Algú sap com fer-ho perquè la webcam no es desconfiguri cada cop que tanco l'ordinador?

El model del meu pc i de la webcam integrada són els que he indicat al títol.

Gràcies!

---

### Post by 19preguntes on 2011-02-13
M'he oblidat de dir que tinc instal·lada la versió 10.04 (lucid) d'Ubuntu.
Salut!

---

### Post by wgarcia on 2011-02-14
Quan passen aquestes coses a vegades el BIOS ha estat compilat per a Windows i per tant Linux no pot reiniciar segons quines coses. Normalment passa amb el control de la temperatura dels processadors, per exemple, però suposo que també pot passar amb la càmera. 

Mira quan inicies l'ordinador si pots entrar al menú de configuració del BIOS i a veure si trobes algun paràmetre relacionat amb la càmera integrada. 

Una altra possibilitat és mirar d'actualitzar la BIOS. Ves a la web de SONY VAIO a veure si tens la BIOS més actualitzada i si donen instruccions sobre com actualitzar-la. Segurament et donaran instruccions per actualitzar-la des de Windows.

---

### Post by 19preguntes on 2011-02-14
Gràcies wgarcia,
no he trobat cap paràmetre del Bios que semblés tenir a veure amb al webcam. De totes formes he provat de canviar els pocs que es podien tocar, però sense èxit.

Des de Windows he accedit a Vaio Update i resulta que tenia bastantes coses per actualitzar. Les he actualitzat totes (no n'hi havia cap que es referís explícitament al Bios) però tampoc ha donat resultat. Per cert, que entrant el número de sèrie a la página oficial de Sony Vaio he descobert que el model del meu pc no era el que he posat al títol d'aquest fil (que és el què posa a l'enganxina que hi ha sota el pc), sinó el VGN-TZ31MN.

Per si de cas he repetit l'operació que vaig fer en el seu dia de baixar el driver que, si ho recordo bé, es diu r5u870, però tampoc ha servit de res.

Bé, seguiré buscant per Internet i fent proves, a veure si hi ha sort.

Salut i gràcies de nou!

---

### Post by 19preguntes on 2011-03-15
Hola, ja he resolt el problema amb la webcam. He seguit les intruccions que he trobat en aquest blog:  [http://www.riveragallardo.es/2009/11/webcam-vaio-vgn-tz-en-ubuntu.html](http://www.riveragallardo.es/2009/11/webcam-vaio-vgn-tz-en-ubuntu.html)
i ha donat resultat.

Potser només caldria especificar que en la part final, enlloc de fer  exactament el que es diu al blog, he seguit les instrucción del document  README que ve dins la carpeta que has baixat prèviamet (potser els què en sabeu  riureu, però quan no en tens ni idea, com és el meu cas, agraeixes  aquesta classe d'aclariments).

Ara la webcam funciona perfectament, al menys amb Cheese i Skype, que són els programes que jo faig servir.

Per si de cas aclareixo que ho he fet amb l'Ubuntu 10.10 (64bits).

Salut!

---

