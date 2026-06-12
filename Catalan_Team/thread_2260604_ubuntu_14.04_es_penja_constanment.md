---
title: "ubuntu 14.04 es penja constanment"
date: 2015-01-13
forum: Catalan Team
---

### Post by diablessamariken on 2015-01-13
Hola companys

tinc problemes amb l'ubuntu. Resulta que darrerament es penja amb molta freqüència quan estic treballant. No he trobat una relació directa entre el programa que estic utilitzant i el moment de les aturades.
La pantalla no perd la imatge, simplement deixa de respondre el cursos i el teclat. 
Com que es tracta d'un ordinador portàtil, la solució que he trobat és abaixar la pantalla com si tanqués l'ordinador, esperar que quedi en stand by i tornar-lo a obrir. Aleshores simplement prement una tecla es torna a iniciar des d'allà on l'havia deixat. 
De vegades es torna a penjar al cap de pocs minuts, i d'altres vegades triga força més a fer-ho.

Alguna idea del que podria fer?

Informacions bàsiques:


UBUNTU 14.04 LTS de 64-bit
Processador: Intel® Core™ i5-2450M CPU @ 2.50GHz × 4 
Gràfics: GeForce GT 520M/PCIe/SSE2

Tinc una targeta gràfica NVIDIA amb el controlador de propietat
NVIDIA Corporation GF119M [GeForce GT 520M]


Com ho veieu?
Gràcies
Astrid

---

### Post by wgarcia on 2015-01-13
Té pinta de ser algun programa que consumeix tots els recursos de memòria i/o processador i deixa l'ordinador sense respondre. En primer lloc assegura't que tens tot actualitzat, en segon lloc s'hauria d'investigar més. Per exemple: és la penjada sobtada o notes que l'ordinador es comença a fer més lent en la resposta abans de penjar-se?

---

### Post by diablessamariken on 2015-01-20
Hola Wgarcia

podria ser d'un programa, però quìn? jo només utilitzo habitualment el firefox, libreoffice i gimp. A més a més, ara mateix acabo d'encendre l'ordinador i abans que pugués obrir cap programa ja s'ha penjat.

Pel què fa al soroll, m'hi he fixat i no es nota res abans de penjar-se.

Alguna altra idea?

Gràcies

---

### Post by wgarcia on 2015-01-21
A veure que no sigui algun problema de maquinari amb la memòria RAM o el disc. Aquesta última penjada fa pensar que no és que hi hagi un programa que faci el tonto. Per descartar primer el tema de memòria, pots fer un test de memòria en iniciar l'ordinador. Si veus el menú d'inici (que et permet arrencar l'Ubuntu o altres sistemes al principi), hi ha una opció a "Opcions avançades" (aquesta opció la dic de memòria, potser no es digui exactament així) que diu "Memtest". Si no veus aquest menú d'entrada a l'Ubuntu (potser perquè sols tens l'Ubuntu instal·lat i llavors entra directament), en quant s'inicia l'ordinador i i després que passen els missatges inicials prem la tecla Majúscula (la fletxa cap a dalt a l'esquerra del teclat que es fa servir per les majúscules) i mantingues-la premuda fins que aparegui el menú.

---

### Post by diablessamariken on 2015-05-29
Hola ubuntaires

segueixo tenint problemes amb ubuntu. Sense cap patró de repetició aparent, de sobte, l'ordinador queda penjat. 

He provar de fer el test de memòria però no vaig detectar cap cosa estranya. He anat actualitzant el sistema operatiu quan hi ha hagut noves actualitzacions disponibles, però no he pogut resoldre el problema.

Alguna idea més?

Gràcies
Astrid

---

### Post by wgarcia on 2015-05-30
Segueixo pensant que és un problema de la gràfica, les targetes NVIDIA són una mica punyeteres a Linux. Pots mirar quina versió del controlador propietari està usant? Això ho pots fer entrant a Paràmetres de sistema -> Programari i actualitzacions i mirar la pestanya "Controladors addicionals".

Sobre  Linux i Nvidia és famós el [ditet que li va dedicar el Linus Torvald.]("https://www.youtube.com/watch?v=MShbP3OpASA#t=2977") l'any 2012.

---

### Post by diablessamariken on 2015-06-05
Insereixo aquí la captura de pantalla on es veuen els controladors disponibles i el que s'està utilitzant.


[https://drive.google.com/file/d/0B72IbWwHcYl0T1dqa1RaakE3U2s/view?usp=sharing](https://drive.google.com/file/d/0B72IbWwHcYl0T1dqa1RaakE3U2s/view?usp=sharing)

---

### Post by wgarcia on 2015-06-07
Prova de canviar a la que diu Xorg Nouveau, aquest és el controlador obert, si veus que les gràfiques no perden massa prestació (és a dir no es veu pitjor o no et funciona alguna cosa), pots fer-la servir. Jo la faig servir al portàtil que tinc ara i va molt bé.

---

### Post by diablessamariken on 2015-07-16
He canviat al controlador obert i les aturades han cessat. Però ara he perdut la capacitat de regular la brillantor de la pantalla... suposo que no es pot tenir tot...

Gràcies!
Astrid

---

### Post by wgarcia on 2015-07-18
Obre un altre fil amb aquest nou tema, a veure si a algú li passa i pot donar una mà.

---

