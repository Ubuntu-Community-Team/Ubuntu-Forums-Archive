---
title: "Gparted no reconeix teclat i ratolí"
date: 2009-07-27
forum: Catalan Team
---

### Post by prostata on 2009-07-27
Per fi la meva esposa ha permès que li instal·li ubuntu en el seu ordinador, això si amb la seva petita partició windows, així que amb Gparted em disposava a crear la corresponent partició, per deixar espai a l'ubuntu, però aquí comença el problema que no se m'ha havia presntat mai i que paso a descriure esperant que m'ajudeu a solucionar-ho.

Gparted arrenca amb normalitat però en fer-ho no em reconoeix ni el teclat ni el ratolí, de manera que no puc operar per res amb Gparted. He provat instal·lar també Jaunty directament però em succeeix el mateix problema, teclat i ratolí no els reconeix...

Què puc fer...??

Salutacions

---

### Post by SiscoGarcia on 2009-07-27
Hola prostata, què tal si ens dones una mica d'informació sobre el ferro de la teua esposa? Una altra cosa, el gparted del que parles és el que inclou el CD autònom d'ubuntu o és una [distro]("http://gparted.sourceforge.net/livecd.php") independent? Ho dic perquè a mi l'únic cop que m'ha passat una cosa semblant va ser fent servir una versió beta de gparted.

Una altra cosa, de quina versió de windows estem parlant? Ho dic perquè el vista alguna vegada ha donat algun problema en alguna màquina.

---

### Post by prostata on 2009-07-27
Ok, tens raò

AMD 1600MH
Nvidia
RAM 1Gb
Teclat, el de sempre vull dir, normalet...normalet ;-)

Versió Gparted, no ho sé ben bé deu fer uns 6 mesos que la tinc, si vols info més especìfica, demana..demana

Gràcies

Edito per ampliar Info:

WXP pro
ara he intentat amb la versió liveCD 0.3.411 però continua el problema, surt la pantalla Gparted però el teclat i el ratolí no "son operatius"

---

### Post by SiscoGarcia on 2009-07-27
No sé quina configuració de teclat li dius que tens (si és que t'ho permet fer), però dient-li que tens teclat espanyol amb "punt volat al mig de la L" m'ho ha admés sempre. Una altra cosa, ja has provat a fer la partició des del gparted que inclou el CD autònom de l'ubuntu? T'ho dic perquè així "mates dos pardals d'un tret".

---

### Post by prostata on 2009-07-28
> **SiscoGarcia said:**
> No sé quina configuració de teclat li dius que tens (si és que t'ho permet fer), però dient-li que tens teclat espanyol amb "punt volat al mig de la L" m'ho ha admés sempre. Una altra cosa, ja has provat a fer la partició des del gparted que inclou el CD autònom de l'ubuntu? T'ho dic perquè així "mates dos pardals d'un tret".

Finalment he pogut usar gparted-live-0.4.5-5.iso i ja tinc Ubuntu Jaunty a l'ordinador de la meva dona, però, sempre un però...ara passa el següent:
en arrencar el Grub no em permet fer servir el teclat per sel-leccionar quin S.O vull arrencar, ja saps la pantalleta en que el Grub mostra kernel XXX, altre SO, o Ubuntu.

Arrenca automàticament Jaunty ja que com et dic el teclat no el reconeix i no puc doncs sel-leccionar el que en un moment donat m'interessi... Un cop a Ubuntu tant el ratolì com el teclat funciona adecuadament...

Gràcies

Edito per ampliació d'info:

Que el teclat sigui USB pot tenir res a veure..?? i si así fos com ho podrìa arreglar..??

---

### Post by SiscoGarcia on 2009-07-28
> **prostata said:**
> Que el teclat sigui USB pot tenir res a veure..?? i si así fos com ho podrìa arreglar..??

Precisament d'això et volia parlar, ja que a la feina tenim algun ordinador que no reconeix els teclats USB però sí que reconeix els PS2; la solució és clara, es tracta de fer servir teclats d'aquest tipus.

Per cert, com que has pogut fer servir Gparted, dono per fet que aquest no era el problema, ja que a més t'ha permès d'instal·lar la jaunty; per tant la única explicació que hi trobo és que el problema sigui de maquinari.

---

### Post by PatrickVogeli on 2009-07-28
Segurament la teva placa sigui bastant vella i el suport per a teclats USB bastant deficient o, directament, inexistent (a nivell de BIOS, a nivell de SO no té res a veure).

A la bios hi pots entrar utilitzant? Si hi pots entrar, mira a veure si hi ha alguna opcio per activar el suport per a teclats usb.

Si no hi ha res, i suposant que el teclat no sigui un combo de teclat i ratoli inalambric, pots comprar un adaptador de PS2 a USB i llestos, sera igual que si tinguessis un teclat PS2.

Salut

---

### Post by prostata on 2009-07-29
> **PatrickVogeli said:**
> Segurament la teva placa sigui bastant vella i el suport per a teclats USB bastant deficient o, directament, inexistent (a nivell de BIOS, a nivell de SO no té res a veure).

A la bios hi pots entrar utilitzant? Si hi pots entrar, mira a veure si hi ha alguna opcio per activar el suport per a teclats usb.

Si no hi ha res, i suposant que el teclat no sigui un combo de teclat i ratoli inalambric, pots comprar un adaptador de PS2 a USB i llestos, sera igual que si tinguessis un teclat PS2.

Salut

ja li he posat un adaptador USB-PS/2 però tampoc funciona, a més:
en arrencar la màquina el teclat funciona puc fer F2 per anar a la BIOS, però no se on mirar el tema del teclat..i altre cosa, el grub triga 10 segons en arrencar en lloc del 30 normals, per anar a jaunty...

o sigui, pel que sigui que encara ignoro, el teclat es actiu en arrencar l'equip, pero es torna inactiu a partir que el Grub entra en acció, però desprès un cop arrenca jaunty torna a ser actiu...quin lio oi???

Gràcies

---

### Post by prostata on 2009-07-29
Bé doncs el serial a finalitzat i tot per 4.5 Euros.... tanta llauna i tot es reduïa a:

D'altres fòrums em van informar i ho vaig comprovar que tots els teclats amb USB i inhalàmbrics Jaunty no els reconeix, es dir, si, però pot donar aquests problemes, de fet crec que algú per aquí ja apuntaba en aquesta direcció, jo com sabeu he provat amb tots els adaptador USB a PS/2 sense èxit, i finalment vaig canviar el meu teclat a la màquina de la meva dona, aquest teclat es vell i va de serie amb PS/2 i.....tot arreglat, arrenco ubuntu, i puc seleccionar en el grub al que vull escullir....per tant he anat a la botiga d'abaix i per 4.5 Euros he comprat un nou teclat...i tot arreglat per una mica més de 500 Peles....si m'adono avans...!!!!!:(:(

Gràcies per la vostra col-laboració

---

