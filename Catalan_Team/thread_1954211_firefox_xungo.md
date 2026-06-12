---
title: "firefox xungo"
date: 2012-04-07
forum: Catalan Team
---

### Post by jesús sol on 2012-04-07
salut!
tinc un Ubuntu lucid linx, ahir vespre em va avisar de que calia posar actualitzacions. Un cop fet, el Firefox no va bé. He perdut les dades que guardava de les pàgines habituals i les contrassenyes de algunes. Sabeu si es pot arreglar?
Moltes gràcies.
Jesús

---

### Post by wgarcia on 2012-04-09
És estrany, normalment no es perden dades del firefox a les actualitzacions. 

Tens còpia de seguretat? El firefox desa totes les seves configuracions a una carpeta que es diu ".mozilla" (amb el punt endavant, cosa que la fa invisible al navegador de fitxers, per veure-la pots fer Control-H). Si tens còpia de seguretat podries restablir aquesta carpeta i en principi s'haurien de restablir totes les teves configuracions i favorits del firefox.

---

### Post by prostata on 2012-04-09
has sentit parlar d'una extensió que es diu Xmarks...va de conya...

---

### Post by wgarcia on 2012-04-10
Pensava que Xmarks ja no estava suportada (a mi em va arribar un missatge fa dos anys o així que l'empresa que la portava ja no li donaria més suport).

El Sync del propi Firefox ha millorat de totes maneres molt i ara et permet mantenir totes les configuracions sincronitzades i serveix de còpia de seguretat per als favorits i les claus.

---

### Post by prostata on 2012-04-10
Hi va haver un temps que Xmarks no tenia suport, i la volien treure de circul-lació, però s'ho van pensar i als pocs mesos ja ho van deixar córrer i novament la van "activar"

Salut

---

### Post by jesús sol on 2012-04-11
Salut gent!
Ho sento molt però sóc molt inhàbil amb aquestes coses. No tinc còpia de seguretat -almenys que jo sàpiga!-, he estat incapaç de trobar la carpeta .mozilla, m'agradaria saber com fer una còpia de seguretat, i com utilitzar-la, el firefox no va bé,-les "adreces d'interès" surten, però el firefox o no hi va o quan les obre (com ara el correu yahoo,)no acaben de funcionar-, a la barra de direccions, no hi surt res escrit. En fi, he hagut d'utilitzar el google chrome per poder navegar.
Haig de baixar-me un firefox nou, es pot arreglar, o què puc fer?
Moltes gràcies i disculpeu la meva ignorància! ...és el que hi ha.
Jesús

---

### Post by wgarcia on 2012-04-12
Com deia la carpeta ".mozilla" en principi està oculta (perquè el nom comença amb un punt), pero si obres el navegador de fitxers a la teva carpeta d'inici, i fas Control-H, hauries de veure tots els fitxers i carpetes ocultes, entre d'altres aquesta. 

Per veure si alguna configuració està causant el que veus podries crear un nou perfil per a Firefox i veure si amb aquest nou perfil tot torna a la normalitat. 

Per crear un nou perfil pots fer la combinació de teclat ALT-F2 i escriure

```
firefox -P
```

Aquí veuràs un assistent per crear el nou perfil. No esborris l'antic perfil (no sé si posa "default" o alguna altra cosa) perquè aquí tens tots els teus favorits i claus. Simplement es per veure si amb el nou perfil Firefox torna a la normalitat i després s'haurien de recuperar els favorits i claus. 

Una altra possibilitat és que hi hagi alguna extensió que no sigui compatible amb l'actualització de Firefox i estigui causant el que veus. 

Si tens extensions habilitades (ho pots veure a Eines -> Extensions) jo les deshabilitaria totes i començaria habilitant una per una a veure si hi ha alguna que causi el problema que veus.

---

### Post by jesús sol on 2012-04-13
salut!
noi, està clar que això no està fet per mi. Per molts control h que he fet, no he aconseguit veure la carpeta .mozilla.
Seguint les instruccions he creat un perfil nou, a més del default. Però va igual de malament que l'altre.
He intentat deshabilitar les extensions. A Eines, no hi ha res que digui extensions. He pensat que potser vols dir Complements. He clicat complements i la bèstia es queda "pensant" però no s'obre res. Total, que l'únic "deshabilitat" sóc jo!
Si se us acut quelcom més que pugui intentar, no quedeu!
Gràcies per tot!
Jesús

---

### Post by kukat on 2012-04-16
És Ubuntu o Kubuntu? 
SI tens un Kubuntu és CTRL + . 
(Control + el punt)

---

### Post by jesús sol on 2012-05-08
Doncs malgrat la vostra ajuda he estat incapaç de tornar la normalitat al Firefox. I he hagut de navegar amb Chrome.
...fins avui!! En el gestor d'actualitzacions, ha aparegut una nova entrega, en la qual hi havia quelcom de Firefox. Les he baixat i instal·lat, i el Firefox s'ha reparat i no he perdut absolutament res. Tot torna a funcionar!
Gràcies a tots!
Jesús

---

### Post by wgarcia on 2012-05-08
Doncs seria quelcom relacionat amb la interfície gràfica de Firefox per integrar-lo a l'escriptori Ubuntu. Avui he vist que a les actualitzacions venia "ubufox", que és justament això.

---

### Post by manelfus on 2012-05-10
Aquest mati aixo m'ha passat a mi i sense haber-hi fet cap actualitzacio tant de l'Ubuntu  com del firefox de cop i volta m'han desaparegut totes les adreces d'interes aixi com el funcionament "anormal" del navegador

   La solució ha estat fer-hi una copia del fitxer bookmarks-data*.json que es trova dintre d'una carpeta anomenada:bookmarkbackup que a l'hora esta dintre de la carpeta oculta .mozilla. 

   Despres de copiat aquest fitxer i desat a l'escriptori eliminarem la carpeta oculta .mozilla de la nostra carpeta personal. Tornarem a obrir el firefox aixo ens creara una nova restauracio d'aquest navegador .

   Sols ens caldra ficar de nou les adreces d'interes per aixos clicarem en adreces d'interes/mostrar totes les adreces d'interes/importacio i copia de seguretat/Restaura una copia de seguretat/Trieu un fitxer i buscarem l'arxiu bookmarks(la data* que sigui).json i buala tornarem atindre totes les nostres adreces d'interes.

    Si us fitxe-ho aquestes apareixen amb l'icone en blanc , conforme les ane-ho obrint tornaran a apareixer les icones


vinga salut i benzina 

manel

---

### Post by jesús sol on 2012-05-10
Ei! molt bé! ...he anat seguitnt les instruccions i está molt clar!. Ja he fet una còpia i l'he posat a l'escriptori. Llàstima que ara el firefox va molt bé i no puc "arreglar-lo"!! :)
gràcies 
Jesús

---

### Post by wgarcia on 2012-05-12
Doncs sembla una bona solució per preservar els "favorits", manelfus, però no sé si un usuari que tingui també claus desades, i altres configuracions i extensions, pugui preservar tot amb aquest procediment. 

Potser hi hagi algun procediment que faci una còpia de seguretat de les configuracions del Firefox més general.

---

