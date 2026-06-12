---
title: "firefox se'm tanca sol (en totes les pagines)"
date: 2009-02-04
forum: Catalan Team
---

### Post by antonix on 2009-02-04
Hola,

Em vaig instalar de nou el intrepid i la veritat que estic molt content, pero al cap d'unes setmanes m'ha aparegut un problema, El firefox (3) se'm tanca de sobte, estiga en la pagina que estiga, ja siga youtube, vilaweb, google, o els mateixos forums de l'ubuntu. No recorde si vaig fer alguna actualitzacio abans que em passes o que..
Si l'execute des del terminal quan es tanca em diu aixo: 

Segmentation fault
 
A veure si em podeu tirar un cop de ma.

Altres coses que m'han sorgit: 

Mentre intente "arreglar" el firefox m'he instalat el koqueror, escrivint aci m'he adonat que no puc posar accents. Tampoc se com posar-lo en catala.

Moltes gr`acies

---

### Post by papapep on 2009-02-04
Prova a fer un memtest de la RAM a l'arrencada, que no tinguis algun banc de memòria malmés, i el Firefox (que ocupa lo seu de RAM) intenti fer servir una posició elevada de memòria i peti per això.

---

### Post by Tomàs M. on 2009-02-05
A banda dels sempre savis consells d'en papapep, també pots provar d'engegar-lo amb un perfil nou (firefox -profilemanager), a veure què passa.

---

### Post by antonix on 2009-02-05
Papapep, he fet el memtest i no m'ha eixit cap error, i com diu Tomas, l'he engegat en un perfil nou i va perfecte. A que es pot deure aixo? Haure d'entrar d'ara endavant amb el nou perfil? 
Be, moltes gracies

---

### Post by Tomàs M. on 2009-02-05
Doncs sembla clar que alguna cosa hi ha al perfil antic que t'ho provoca... sí, jo faria servir el nou. Si vols provar de recuperar adreces d'interès, extensions, configuracions... jo provaria d'instal·lar FEBE, fer una còpia selectiva i anar recuperant pas a pas, fins que trobis la part que provoca les tancades... o no. Jo una vegada vaig acabar recuperant-ho tot i amb el problema que tenia solucionat al perfil nou.

Sort!

---

### Post by socderafel on 2009-02-14
Hola a tots! he descobert hui aquest fòrum i crec que ja no l'abandonaré...

Anem al tema.

Has instal.lat el paquet libflashsupport?
Si es així, desinstalal. Hi ha un problema d'incompatibilitat amb aquest paquet quan obres alguna pàgina amb flash...
Resulta curiós que un paquet per a veure flash dona problemes amb flash...
Jo ho vaig instal.lar perque no tenia sò als videos flash amb firefox, i em passava el mateix. La sol.lució va ser posar tots els canals d'audio a ALSA.

Espere t'haja ajudat...

Saluts desde el País Valencià!!!

---

