---
title: "[SOLVED] Wi-Fi Orange"
date: 2007-09-10
forum: Catalan Team
---

### Post by Druiling on 2007-09-10
Hola tots.
Primera: estic flipant d'haver trobat aquest fòrum!
Segona: Porto uns dies intentant d'instal.lar-me l'Ubuntu i no he tingut cap més problema que el tema de la connexió inalàmbrica.
Tinc un wifi orange Sagem fast 1500 i un portàtil Asus A6. 
Jo crec que l'Ubuntu em reconeix tant el sagem com el usb amb el dispositiu connectat que hi ha d'anar sempre, però a l'hora de configurar-los, només fa que crear xarxes noves i no em dona connexió (tampoc cap error). Jo diria que deuen ser els drivers, però per més que busco, no trobo res, i n'he trobat del sagem 800, però no tinc ni idea de com descarregar ni instal.lar per si de cas anessin bé.
ALGÚ EM POT DONAR UN COP DE MÀ? SI US PLAUUUUUU!!!!](*,)
Jo vull deixar micros ja
Gràcies per endavant.

---

### Post by pespin on 2007-09-10
Wei, no cal que obris un altre post per la mateixa cosa, que el tens aquí[http://ubuntuforums.org/showthread.php?t=547654]("http://ubuntuforums.org/showthread.php?t=547654")

Jo no t'he respost perquè no acabo d'entendre el problema.

> Tinc un wifi orange Sagem fast 1500

Això que és? la targeta? el mòdem? :confused:

provar a fer un iwconfig a veure si et detecta el dispositiu.

---

### Post by papapep on 2007-09-11
Druiling: t'he esborrat el nou fil duplicat. Tingues paciència, no cal obrir nous fils del mateix tema si no et contesten.

Per començar, ens hauries d'explicar bé el teu cas: quina marca i model és l'stick usb que fiques a l'ordinador? Intentes connectar al router amb encriptació (quina) o sense,etc...

---

### Post by patrickfromspain on 2007-09-11
Duriling, hem sembla que t'has fet un bon embolic. Anem per parts:

Sagem F@st 1500: es el modem router adsl. Te 3 o 4 port ethernet i es inalambric tambe, per tant porta una antena. NO té conexió USB, no necessita drivers.

Sagem F@st 800/840: modem adsl per USB, suposo que d'uns 10cmx10cm. Necessita drivers per a funcionar.

Sagem WL****/XG****: adaptador inalambric per usb, de la mida d'un llapis de memoria USB. Necessitar drivers per a funcionar

Ara ja saps que es cada cosa. Dius que tens un F@st 1500, doncs bé, no necessites res que vagi per USB (entenc que parle d'un adaptador inalambric USB WL/XG), ja que el teu portatil ja porta el wifi integrat. Amb el network manager, nomes hauries de buscar la teva xarxa inalambrica i posar la contrasenya (estan a sota el ruter si no has tocat res) i ja hauries de poder navegar. 

Salut!

---

### Post by Druiling on 2007-09-11
Hola a tots tres!
Primera i més important, us demano que perdoneu els meus impulsos "pardillos", hauria d'haver preguntat de bon començament i no posar-me dels nervis com va passar finalment.
D'altra banda, patrikfromspain, tens raó, és un router wifi amb quatre ports  i antena, al que em referia amb l'USB, és que per tal que funcioni, hi ha un altre dispositiu que haig de tenir connectat al portàtil, com una mena d'USB, que deu ser el que envia el senyal a l'antena i l'adaptador que dius tu, cosa que no deixa de ser curiosa perquè he tingut dos wifis més (d'altres companyies), i no em calia cap més dispositiu que la meva targeta wifi.
El wifi em diu que la seguretat és WEP, authentication network OPEN però security enabled (NO ENTENC RES).
Quant al tema de si he posat el nom de l'aparell i la contrasenya, si, i em dona connexió, peró no m'obre cap plana web, i al cap d'una estona em desconnecta el wifi.
En fi, no sé què més puc dir-vos a banda de tornar a demanar-vos disculpes.
Salut!!
D.):P

---

### Post by Druiling on 2007-09-11
Hola nois.
En Papapep m'ha donat una pista que he seguit i "bingo"!.
El tema era el WEP. He aconseguit a la fi configurar la connexió taxantaxantaxannnnnn!!
Escric des de l'Ubuntu a la fiiiiiiiiiiiiiiiiiiiii.
Gràcies a tots plegats.
Ens veiem.
Salut.

D.
:guitar:

---

### Post by patrickfromspain on 2007-09-11
Molt be :)

En aquest forum he posat un post sobre un substitut del network manager: wicd. Igual t'interesa.

---

### Post by papapep on 2007-09-11
Enhorabona i benvingut a la nostra comunitat! ;-)

---

