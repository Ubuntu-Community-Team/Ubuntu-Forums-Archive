---
title: "Targeta grafica ATI  - Té solució?"
date: 2010-09-13
forum: Catalan Team
---

### Post by rogermante on 2010-09-13
Hola a tothom!

Acabo d'instalar l'Ubuntu 10.04, i tot sembla funcionar perfectament, excepte que el rendiment que em dóna la targeta gràfica és bastant miserable, un vídeo a pantalla complerta tira a batzegades.

Info:
Ubuntu 10.04 - net i nou de fàbrica, res instalat
ATI Radeon 9100 IGP

En alguns posts he vist que per millorar el rendiment, puc instalar els drivers propietaris, en d'altres que els propietaris al 10.04 no són  compatibles, etc.. Total, que ho he provat i falla la instalació queixant-se que no tinc Xfree86 (pel que he llegit, sembla normal al 10.04, no?)

Algú té alguna idea sobre què puc fer, o si la única solució és tornar a l'XP (on la targeta no tenia cap problema).
Després de tant de temps fent servir Windows em venia de gust canviar a linux, però ara ja no ho veig clar...

Moltes gràcies per endavant!

Roger

---

### Post by kukat on 2010-09-13
Aquí comenten una combinació del driver lliure d'ATI combinat amb una cosa anomenada Gallium: 

[http://ubuntuforums.org/showthread.php?t=1553527](http://ubuntuforums.org/showthread.php?t=1553527)

però ATI no ha facilitat les coses per a tindre un driver per a les seues targetes a GNU/Linux. 
Jo tinc la Radeon 9550 i tampoc es veuen bé els vídeos amb flash.

Et referixes a vídeos del youtube amb flash o a un vídeo normal vist amb el VLC o similar??

---

### Post by wgarcia on 2010-09-13
En principi la teva targeta gràfica està plenament suportada per Ubuntu 10.04. Assegura't de no estar utilitzant el controlador propietari sinó el controlador obert d'ubuntu (que es diu "radeon"). 

Què posa si accedeixes al menú?:

Sistema -> Administració -> Controladors de maquinari

Assegura't que no s'està usant el "ATI accelerated graphics driver".

---

### Post by rogermante on 2010-09-13
Intentaré contestar-vos les preguntes que hem feu:

 - Acabo de provar-ho, i amb el flash és el mateix que quan reprodueixo un video amb el VLC. Mida normal tira bé, però tan bon punt poso pantalla completa, es nota que li costa tirar. Es veu, però mirar una cosa més llarga de mig minut ja es fa pesat.

 - Pel que fa a l'Ubuntu 10.04 suportar la meva tarjeta crec que sí, perquè es veu bé, amb bona resolució. 

 - A "hardware drivers" em diu que no "no proprietary drivers in use", que és el que espero veure perquè no he instalat res.

Pel que sembla, el paio d'aquest enllaç que em passes kukat ho ha solucionat per la via ràpida (bought a geforce...should solve the case), però si haig de comprar una targeta tan se val que hi torni a posar l'XP.

L'única cosa que hem quedava provar era fer servir els drivers propietaris d'Ati, però pel que sembla al 10.04 no són compatibles? O ho tinc tot mal entès? Vaig intentar instalar-los i no me'n vaig pas ensortir de totes maneres.


Gràcies de nou!

---

### Post by wgarcia on 2010-09-14
Potser doncs provar el controlador propietari, que en principi són compatibles amb aquesta versió d'Ubuntu. Pots anar a Sistema -> Administració -> Gestor de paquets Synaptic i buscar "fglrx" i instal·lar-lo, a veure si et dóna millor rendiment que el controlador obert.

---

### Post by epileg on 2010-09-14
Per a activar els controladors propietaris, Ubuntu té una eina específica. Vés al menú Sistema -> Administració -> Controladors de maquinari.

Si els controladors propietaris de Lucid et donen problemes, pots compilar la darrera versió. [Aquí]("http://www.gnulinux.cat/2010/07/amd-catalyst-10-7-amb-suport-per-a-opensuse-11-3-i-moltes-millores/") hi ha una bona explicació de com fer-ho.

Salut,

---

### Post by rogermante on 2010-09-16
Gràcies epíleg! Sembla que he arribat més lluny...

Tot i que em quedo encallat a l'últim pas:

sudo aticonfig --initial

em diu "no adaptors found". Segons el gestor de paquets synaptic tinc l’fglrx instal.lat.
Però haig de baixar alguna cosa més d'amd?

---

### Post by epileg on 2010-09-16
que has fet concretament? Has insta&#320;lat els controladors privarius amb el «Controlador de maquinaris» de l'Ubuntu? Has creat uns nous controladors amb Catalyst 10.7?

---

### Post by rogermante on 2010-09-16
He seguit les instruccions d'aquest enllaç que m'has passat.
Em sembla que ja entenc què passa...

Segons la wikipedia

"In 2009, the Catalyst driver officially dropped support for R500 and older chips, the FOSS driver being deemed stable and complete enough. The last driver release supporting older architectures is Catalyst 9.3."

Com que la meva és 9100 igp (diria RV200), quan instal·lo el catalyst 10.9 es queixa que no troba l'adaptador adequat. 

Quan segueixo les passes de la pàgina AMD, segons la mega targeta em fa descarregar això:
[http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

que és de l'any de la picor, i pel que he vist, no instal·la bé a l'Ubuntu 10.04. Sempre m'acaba fallant per un error o un altre.

Total, vosaltres que hi enteneu, tinc altra opció que:

a) tornar a l'XP, que és una llàstima
b) agafar una versió d'Ubuntu de l'any de la picor per tal que suporti aquests drivers

O pot ser que el fet que vegi els vídeos a pantalla completa a molt baix rendiment sigui degut a alguna altra cause que no sigui els drivers?

---

### Post by epileg on 2010-09-16
El rendiment està molt directament relacionat amb el controlador.

Quina ubuntu 10.04 has insta&#320;lat, 32 o 64 bits? si és la de 64 bits, prova a insta&#320;lar [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/fglrx64_6_8_0-8.28.8-1.x86_64.rpm](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/fglrx64_6_8_0-8.28.8-1.x86_64.rpm) després de convertir-lo a deb amb l'aplicació alien.

$ sudo alien --scripts fglrx64_6_8_0-8.28.8-1.x86_64.rpm

Per últim, has comentat unes quantes vegades la possibilitat de tornar a XP. Per a mi això no és una opció, però si creus que aquesta és la solució, endavant.

---

### Post by rogermante on 2010-09-16
gràcies per respondre, i per la paciència!

He instal·lat el de 32 bits, pot funcionar el paquest aquest de 64? És el mateix que amd em fa instal·lar, o sigui que crec que si, no? 

Després d'instal·lar l'alien, executo la comanda tal com has dit però em dóna error (no pot crear una carpeta).


No és pas que vulgui tornar a l'XP, m'agrada més l'Ubuntu si et sóc sincer, però l'ús principal que faig d'aquest ordinador és connectat a la tv i mirar dvds... Fa 2 setmanes que rameno i ja tinc la parenta nerviosa que vol mirar una peli :-)
Si, puc comprar també una targeta més nova, però això ja són diners i potser no anirà bé tampoc amb la placa mare, que també és vella obviament...

En fi, moltes gràcies per l'ajuda. Aniré provant quatre coses més de moment fins que ho vagi pelut (o me'n surti!)

---

### Post by epileg on 2010-09-16
Si el sistema és de 32 bits, el controlador també ho ha de ser, no pot ser de 64 b its.

El teu rodinador és un sobretaula? si és així, jo tinc una tarja ati agp prou bona i que no puc fer servir en la meva placa mare nova (amb pcie). Si et va bé i t'interessa te la puc enviar.

---

### Post by rogermante on 2010-09-16
Quan estava escrivint això de comprar una targeta, també m'ha vingut al cap que potser alguna de segona mà puc trobar a algun lloc.

Gràcies per l'oferiment, però estic a l'estranger, i enviar-ho encara seria més car aquí, o sigui que miraré de trobar algú amb una targeta vella (però no tant com la meva!) que no facin servir com et passa a tu.

Com a mínim ara tinc més o menys clar què puc fer! :-)

Gràcies de nou pel cop de mà, m'heu estat de bona ajuda!

Roger

---

### Post by quitus on 2010-09-16
Hola, donat que el tema del driver sembla que ha quedat clar, el següent pas podria ser intentar optimitzar l'equip per la reproducció de vídeos, et passo una adreça de un foro de vídeos HD on expliquen com fer-ho.

[http://hdteam.es/showthread.php?t=12893](http://hdteam.es/showthread.php?t=12893)

Un altre opció es provar amb altres reproductors, em va sorprendre la bona qualitat de la reproducció del XBMC 

salut

---

