---
title: "el pc tanca la sessió sol"
date: 2011-05-23
forum: Catalan Team
---

### Post by mggg on 2011-05-23
petit problema amb el [B]Ubuntu 11.04. Al posar un video amb qualsevol reproductor, es tanca la sessió del pc sol. ??? sobretot em passa al intnentar maximitzar o moure la pantalla del reproductor
[/B]

---

### Post by wgarcia on 2011-05-24
Fas servir la sessió que diu "Ubuntu"? (Fixa't en entrar el teu usuari a la barra de baix què posa) 

Si és el cas potser estàs fent servir Unity i això implica fer servir Compiz i es produeix un error relacionat amb la targeta gràfica. 

Per verificar-ho pots entrar a la sessió "Ubuntu clàssic sense efectes" i veure si pots reproduir l'error. Si no es reprodueix s'hauria de mirar quina targeta gràfica tens i quins controladors estàs fent servir. 

Si es reprodueix potser sigui una altra cosa.

Per tornar a iniciar a la sessió que estaves fent servir abans d'aquesta prova quan entres l'usuari mira un altre cop a la barra de baix i escull la sessió que estaves fent servir ("Ubuntu" o "Ubuntu clàssic" o el que fos).

---

### Post by prosso on 2011-05-25
Hola bones, 

aprofito el fil ja que el meu problema es semblant.

En el meu cas encara faig servir el Ubuntu 10.10; i moltes vegades es tanca sol. Al principi tenia la sensació que només passava quan reproduïa algun vídeo via web (el qual de per si moltes vegades en dona problemes de Shockwave), però la última vegada només tenia el Chromium obert amb 8-9 pestanyes obertes i ... puff!! Ubuntu es tanca!

Val a dir que no passa sempre tampoc ... es molt estrany.

Alguna idea? no hi ha cap lloc on quedi un registre d'aquests successos?

A revuere i gràcies :)

---

### Post by wgarcia on 2011-05-25
Pot ser un problema d'escalfament excessiu de la targeta gràfica, se sent que treballa molt intensament quan reprodueixes vídeo?

---

### Post by prosso on 2011-05-26
quan dius que "se sent" vols dir si s'escolta? si es el cas no sento res de diferent.

Si hi ha una altra manera de comprovar l'estat de la targeta gràfica ja m'ho direu.

Per si serveix: com he dit estic amb Ubuntu 10.10, no faig servir Unity i tinc els "Efectes visuals" descativats (crec que es el que han mencionat com a Compiz). El meu ordinador es un portatil Fujitsu Siemens Amilo M7440.

Gracies :)

---

### Post by mggg on 2011-06-04
Doncs he provat amb ubuntu, ubuntu classic i amb ubuntu classic sense efectes, i amb els tres passa el mateix, al reproduir un video, es tanca la sessió

---

### Post by wgarcia on 2011-06-04
Saps quina targeta gràfica tens? Si no ho saps entra en una terminal:

lspqci | grep -i vga

i comenta el que surt.

---

### Post by mggg on 2011-06-04
em diu això:

:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)

---

### Post by wgarcia on 2011-06-05
Prova entrar a la sessió d'escriptori "Ubuntu sense efectes" a veure si sense efectes especials quan reprodueixes els vídeos no es tanca el sistema. A veure si és alguna interacció entre els efectes especials i la reproducció de vídeos.

Mira també a "Paràmetres del sistema" (al menú de tancar a l'extrem esquerre del quadre superior) -> Maquinari -> Controladors addicionals a veure si t'ofereix instal·lar-te algun controlador gràfic especial.

---

### Post by mggg on 2011-06-06
he provat d'entrar a  la sessió "Ubuntu sense efectes" i em passa el mateix

he mirat a sistema - administració - controladors adicionals, però no em troba cap controlador 

(aquest menu maquinari no l'he trobat (??))

---

### Post by wgarcia on 2011-06-06
Quan comença l'ordinador, t'ofereix el menú Grub amb algun altre nucli anterior que puguis provar? A l'última versió em sembla que surt com "Altres versions de linux" o alguna cosa així. Seria interessant si puguessis entrar en aquest nucli més antic i puguessis provar si continua el problema, que no sigui un problem del nucli actual de Linux que  interactuï malament amb la teva targeta gràfica.

---

### Post by mggg on 2011-06-07
amb la versió anterior, la 10.04 em funciona perfectament i no tinc cap problema,

ademés amb la 11.04 l'ordenador em va més lent

---

### Post by wgarcia on 2011-06-08
La versió anterior a la 11.04 seria la 10.10, no la 10.04.

El que dic no és provar la versió anterior sinó algun nucli més antic, si els tens al menú inicial (Grub). Hauria de sortir sota "Versions anteriors de Linux" o una cosa així.

---

### Post by mggg on 2011-06-14
doncs no tinc cap versió anterior, el 11.04 el vaig instalar en un hdd nou

---

