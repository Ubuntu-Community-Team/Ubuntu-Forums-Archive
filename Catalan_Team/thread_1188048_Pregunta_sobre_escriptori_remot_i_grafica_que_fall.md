---
title: "Pregunta sobre escriptori remot i grafica que falla"
date: 2009-06-15
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-06-15
Hola a tothom,

a veure si algu de vosaltres sap la resposta a la següent pregunta, ja que m'ha deixat una mica extranyat el tema.

A casa tinc un portatil al qual jo diria que li falla la tarjeta grafica, ja que ni la pantalla del portatil ni la externa es veuen be, sinó que fa ralles i coses rares.

La questió és que jo pensava que per escriptori remot funcionaria bé, pero em fa exactamente el mateix. Es el comportament normal i esperat i, per tant la gràfica falla definitivament, o busco per algun altre lloc ja que s'hauria de veure bé?

Merci i salut

---

### Post by papapep on 2009-06-15
Quan dius "escriptori remot", vols dir per VNC? amb aquest protocol estàs veient la sessió gràfica oberta al host, o sigui que és normal que ho vegis igual de malament, per que estàs veient **el mateix**. 
Una altra cosa seria si diguessis que exportant les X's per SSH també se't veu malament. Ho has provat això?

---

### Post by PatrickVogeli on 2009-06-15
he provat tot el que té l'ubuntu. EL pc m'ha arribat sense disc dur, així que esta "funcionant" sobre el LiveCD de la versió 9.04, activant la opció d'escriptori remot.

Es curios, ja que despres m'he fixat que, 2 cops he iniciat el cd tal qual i la pantalla es veia malament a tot arreu. Despres, 2 cops he iniciat en mode grafic segur i, oh sorpresa, les pantalles del pc es veien malament pero remotament bé...

seguire fent proves.

salut

---

### Post by CarlesOriol on 2009-06-17
> **papapep said:**
> ...per que estàs veient **el mateix**. 

Doncs no, **ni de conya.**

Tot i que no és el cas, pots tenir una gràfica que fa la composicio' malament a la pantalla encara que el buffer de video sigui bo i és aquest el que es transmet via vnc. (fins i tot pots tenir problemes de conexionat i cables que aquests no passen pel tub del vnc :-D )

---

### Post by papapep on 2009-06-17
Quan dic "el mateix", evidentment, em refereixo que està veient el senyal que genera la gràfica del servidor VNC. És clar que, fins i tot en el cas de que no tingui monitor connectat a la placa,  veurà el contingut que aquesta li envia. La resta que comentes és obvi: el que genera la placa és el primer pas, la resta ja són figues d'un altre paner :)

---

### Post by PatrickVogeli on 2009-06-17
bé, finalment, el portatil ja no es a les meves mans. La memoria es l'únic que vaig poder canviar, i seguia donant el problema. Tant el processador com la gràfica anaven integrades i sense possibilitats de canviar-se. 

Vaig desconecta tots el perifèrics possibles, deixant només el més basic i ho continuava fent.

Total.. que perdut estava i perdut continua.

salut i merci

---

