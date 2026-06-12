---
title: "Gravació Musica a Ubuntu"
date: 2007-05-27
forum: Catalan Team
---

### Post by kukat on 2007-05-27
Tinc l'Ubuntu Studio, i tinc una pedalera ZOOM amb conexió usb. Però la meva tarjeta de so no es res de l'altre mon, es la que venia a la placa base (ASROCK)... Es pot fer alguna cosa per grabar la guitarra? I també tinc un saxo, es pot grabar també amb un micròfon conectat a l'ordinador amb el mini-jack? La veritat es que no tinc ni idea, i sempre m'ha fet ilusió grabar algunes melodies o alguns acords per a fer alguna cansó, però mai he tingut sort amb el WIndows....

---

### Post by pisuke on 2007-05-27
Qualsevol tarjeta de so deu tenir entrada de micro. Conecta-hi un microfon. Amb el gravador de sons que té per defecte hauries de poder gravar qualsevol cosa.

Fixa't que l'entrada del micro estigui activada. (Ho pots veure si vas a l'altaveu que es veu al costat del rellotge->botó dret->obrir control de volum i fixa't en les diverses pestanyes que hi ha que les referències al microfon estiguin activades).

Amb això hauries de poder gravar sense problemes. Suposo que la qualitat serà modesta, però segur que suficient per començar a jugar.

---

### Post by kukat on 2007-05-27
Be, he conectat el microfon / Beyerdynamic/ al mini jack de l ordinador, hi he fet el que has dit de la icona de so. Pero ara quin programa utilitze per a enregistrar el so??? el programa Ardour hem diu el seguent> 
There are several possible reasons:

1) JACK is not running.
2) JACK is running as another user, perhaps root.
3) There is already another client called "ardour".

Please consider the possibilities, and perhaps (re)start JACK

????? 
Per que??? Necesite comprarme una tarjeta?? No he configurat alguna cosa?? 

El que vull unicament es grabar alguns acords, algunes melodies amb el saxo, i fer alguns esquemes per a despres desenvolupar alguna canso, no demane mes ;)
Si algu hem dona alguna solucio hem posaria molt content. 
I si algu sap com funcionar la pedalera ZOOM amb el Ubuntu Studio tambe seria meravellos!! 
Gracies!!

---

### Post by lluisanunez on 2007-05-27
Audacity és el teu programa.
Hi ha un bon manual aqui:
[http://mosaic.uoc.edu/pdf/Captura_y_Edicion_de_Audio_con_Herramientas_Libres.pdf](http://mosaic.uoc.edu/pdf/Captura_y_Edicion_de_Audio_con_Herramientas_Libres.pdf)

---

### Post by CarlesOriol on 2007-05-27
no no, l'audacity no.

Ja vas ben encaminat. l'ardour és el teu programa no és el cubase però no està gens malament.
Hi ha un projecte [http://www.jokosher.org/](http://www.jokosher.org/) que sembla un tema senzillet però maco. 

Bé... seguim amb l'ardour la confgiuració del dimoni del jack és la part més complicada.

Abans de tot cal que insta&#320;lis el nucli lowlatenci (amb el synaptic) 

Despres el jack (amb el synaptic)  (que sería l'equivalent de l'asio en uindous) i un cop fet cal que configuris les entrades i sortides.

---

### Post by CarlesOriol on 2007-05-28
No tens obert el dimoni Jack.

En ubuntustudio obre el jackcontrol (aplicacions > so i video -> Jack control) i després inica'l (start) 

[I]
1) JACK is not running.
2) JACK is running as another user, perhaps root.
3) There is already another client called "ardour".[/I]

---

### Post by kukat on 2007-05-28
Ja tinc el dimoni Jack funcionant. I lo que m'has dit abans del "Low Latency" deu ser el que tries al principi, quan s'inicia l'ordinador... no? (en el GRUB, si no m'equivoque). 
Que faig ara? jejeje. M'enrecorde amb el Windows que amb  el CUBASE SX no vaig arribar a fer-ho funcionar mai...espere que tingam més bona sort!!jejeje
Gràcies.

---

### Post by kukat on 2007-05-28
He estat investigant i ja se que es el Synaptic Package Manager (al Sabayon hi havia una cosa similar, però per a KDE). El que dius que tinc que instalar és el alsaplayer-jack???  I l'altre que tinc que instalar, hi ha moltes coses semblants... QUina de totes és? 
Hem surt: 
Linux-Backports-Modules-2.6.20-15-lowlatency
linux-backports-lowlatency
Linux-Headers-2.6.20-15-lowlatency
Linux-Headers-2.6.20-16-lowlatency
Després ixen un fum de Linux-Image-Lowlatency
Linux-Lowlatency a seques.
I finalment Linux-Restricted-Modules-Lowlatency uns quants també.

Quin es??

---

### Post by CarlesOriol on 2007-05-28
Anem per passos.

Si tens l'ubuntustudio (vaig veure tard que parlaves de l'ubuntustudio) ja tens insta&#320;lat el lowlatency i el jack.

Tenint sols l'ubuntu es complica un pel la configuració. A més l'arduor va un munt de versions desfasat.

Ara per començar sols et cal iniciar el jack tal com t'he dit al missatge anterior.

Engega el programa crea una pista i fes una prova d'enregistrament. (rec + rec a la pista + play (o barra espai))

---

### Post by kukat on 2007-05-28
Crec que ho he fet be: He anat a Session, Després a Add Track/bus, i he creat un track nou. (he posat stereo). I he posat els dos recs (per a que posar dos?) i després el play. S'ha grabat el que deia pel micro, però es sent molt molt baixet. Ho tinc conectat amb un adptador a minijack...

---

### Post by kukat on 2007-05-28
fa també petits sorolls...al minimitzar, al maximitzar, i quan estic fent coses per internet  fa petits sorolls...?????? No se que pot passar.

---

### Post by CarlesOriol on 2007-05-28
El rec superior per indicar que enregistri i el de les pistes per indicar on enregistra.

El problema que tens amb el microfón és per que de fet et falta un component et caldria una taula o previ (com pot ser el panell d'algunes targetes que ténen una part externa -la meva: [http://www.creative.com/products/product.asp?category=1&subcategory=204&product=4925](http://www.creative.com/products/product.asp?category=1&subcategory=204&product=4925) ) entre l'ordinador i les fonts d'audio que et normalitzi volums.

Al mesclador d'algunes targetes d'audio senzilles a vegades permet una entrada amb més volum de la font de micrófon però normalment produeix distrorsions.

He penjat un petit video (sense so) per si et serveix de referència [http://www.archive.org/details/ComenarAmbLardourAmbUbuntustudio](http://www.archive.org/details/ComenarAmbLardourAmbUbuntustudio)

---

### Post by kukat on 2007-05-28
Que et va costar la Sound Blaster i el panell? 
També fa sorolls quan no està conectat el micròfon ( deu ser per que está el Jack funcionant). Doncs...No hi ha manera de fer que aumenti el volum si no es comprant una bona tarjeta? Fare per comprar-ne una...:(

---

### Post by CarlesOriol on 2007-05-28
Ja fa temps que la vaig comprar ara ja no deu existir.

Al web d'ardour en recomanen algunes i ténen wiki forum i de tot.

Amb les targetes bones no hi ha tant soroll però també és bona idea que l'entrada anterior a la targeta tinguis alguna cosa una mica "arregladeta" i així pots compensar micrófons i equalitzar més directament, jo tinc un [http://www.amazon.com/Yamaha-MG8-2FX-Channel-Stereo/dp/B000B8V9YM](http://www.amazon.com/Yamaha-MG8-2FX-Channel-Stereo/dp/B000B8V9YM) però compte. Estem parlant de grabacions amateurs.

Per tenir un pel més de qualitat ja has d'anar a les m-audio.

---

### Post by kukat on 2007-05-28
Perdona per fer el pesat... I que hi ha de la Pedalera ZOOM???? Et funciona per USB correctament amb aquest programa? Necessita també una bona tarjeta igual que amb el micròfon? Es que aquesta semana l'he deixada (la pedalera) i per aixó no t'havia preguntat res abans, ja que no la tinc aquí per poder probar-ho... Però seria una gran alegria saber que aixó si que va :D . 
La pedalera es aquesta: [http://www.pop-music.com.ar/images/zoom%20G2%20u%20guitarra%20web.jpg](http://www.pop-music.com.ar/images/zoom%20G2%20u%20guitarra%20web.jpg)  
Si tenim la mateixa... quina alegrai!!jejeje;)

---

### Post by CarlesOriol on 2007-05-28
no no... la teva és molt guapa!!

Jo tinc una 505 i una 5XX nosé qué... així com una digitech rp80 ... vaja... les de pobre.

Tinc uns amics que ténen una botiga de música a l'hospitalet (evidentment amb ubuntu al punt de venta des de fa 2 anys!!) i em sembla que ténen la teva per algun lloc. A veure si un dia d'aquests passo i faig un cop d'ull a la bèstia.

---

### Post by kukat on 2007-05-28
Tampoc val tant!! Crec que hem va costar uns 120 euros (fa 1 any o més) Però tampoc t'ho puc dir segur. Però la vaig conseguir currant a l'obra a l'estiu, que jo tampoc tinc ni un puto duro. La teva funciona bé amb USB en aquest programa? o fa falta altre programa? Está ja es la ultima pregunta, que tinc que estudiar!!jejejejejej;)

---

### Post by CarlesOriol on 2007-05-28
home... no té usb. Per tant podem dir que no va malament ;-)

---

### Post by CarlesOriol on 2007-05-28
Podries preguntar-ho directament a ells si ténen res per linux.

La informació de contacte al seu web:

Zoom Corporation
E-mail: [email]info@zoom.co.jp[/email]

---

