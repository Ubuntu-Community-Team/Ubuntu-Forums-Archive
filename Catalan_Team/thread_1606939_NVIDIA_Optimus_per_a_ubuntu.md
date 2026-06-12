---
title: "NVIDIA Optimus per a ubuntu?"
date: 2010-10-27
forum: Catalan Team
---

### Post by idrojsnop on 2010-10-27
Hola a tothom,

Em vull comprar un portàtil: ASUS U30JC i porta una tarja gràfica NVIDIA GEFORCE G 310M i soporta tecnologia NVIDIA OPTIMUS.

I m'agradaria saber si ja hi ha controladors per a aquest tipus de targes gràfiques. Perquè m'agradaria explotar aquest potencial ja que el trobo interessantíssim i em farà que em duri la bateria molt i molt més.

Algú em podria dir alguna cosa? 

Jo he llegit que hi ha gent desenvolupan-t'ho, però jo sóc usuari i no tinc pas nivell com per posar-me a desenvolupar, hehe.

Bé, moltíssimes gràcies!

---

### Post by albandy on 2010-10-27
> **idrojsnop said:**
> Hola a tothom,

Em vull comprar un portàtil: ASUS U30JC i porta una tarja gràfica NVIDIA GEFORCE G 310M i soporta tecnologia NVIDIA OPTIMUS.

I m'agradaria saber si ja hi ha controladors per a aquest tipus de targes gràfiques. Perquè m'agradaria explotar aquest potencial ja que el trobo interessantíssim i em farà que em duri la bateria molt i molt més.

Algú em podria dir alguna cosa? 

Jo he llegit que hi ha gent desenvolupan-t'ho, però jo sóc usuari i no tinc pas nivell com per posar-me a desenvolupar, hehe.

Bé, moltíssimes gràcies!

Segons el que he llegit als forums de NVIDIA encara no tenen pensat donar suport per la tecnologia OPTIMUS a GNU/Linux.

hhttp://www.nvnews.net/vbulletin/showthread.php?p=2183477#post2183477

De totes formes amb els drivers de NVIDIA tindràs acceleració gràfica igualment, però sense fer servir aquesta tecnologia.

També he llegit que si que s'implementarà al driver obert, però això tardarà.

---

### Post by idrojsnop on 2010-10-27
Ja veig que fins d'aquí un temps no ho podré fer servir, però pensant a llarg termini és una bona inversió comprar-me aquest portàtil pq tard o d'hora surtirà el controlador.

També m'agradaria comentar una cosa, a mi m'interesaria més tenir desactivada la NVIDIA mentre no existeixin aquests controladors, ja que així la bateria em duri molt més. I en algun cas excepcional, quan vulgui jugar o fer anar algo q necessiti gràfica, connectar-la. És a dir, fer el balanceig de forma manual.

Algú sap si activar i desactivar la gràfica en questiò em serà fàcil? Si el linux em detectarà bé les dues gràfiques o es tornarà boig?

Algú té alguna experiència?

Gràcies!

---

### Post by albandy on 2010-10-27
fes un cop d'ull a això:
[http://ubuntuforums.org/showthread.php?t=1460557](http://ubuntuforums.org/showthread.php?t=1460557)

---

### Post by idrojsnop on 2010-10-27
Si, ja veig. Gràcies, bona aportació.

Però veig que no s'aclaren ni ells, és a dir: n'hi ha un que diu que el kernel de linux ja porta incorporat aquesta opció.. però jo crec que no és veritat.

Algú té més informació?

---

### Post by idrojsnop on 2010-10-29
Algú sap alguna cosa més?

---

### Post by wgarcia on 2010-10-30
Encara no hi ha suport a Linux per targetes gràfiques "híbrides", com la NVIDIA Optimus. El que sí hi ha és un treball intens "upstream", és a dir no específicament a Ubuntu sinó a nivell de nucli compartit per totes les distribucions Linux, amb la qual cosa el més normal és que d'aquí a poc hi hagi suport. Per tant si ets valent pots comprar-te el sistema si t'agrada, anar funcionant sols amb la targeta Intel, i anar seguint l'evolució del tema per veure quan pots habilitar les dues targetes gràfiques.

---

### Post by idrojsnop on 2010-11-09
Al final m'he comprat l'asus bamboo, que és si fa no fa el mateix que el que us deia en el post anterior.

Val a dir que he ficat l'ubuntu i estic molt i molt content. Em va perfecte, tot i que amb alguna unitat virtual he provat d'instal·lar la targeta gràfica "nvidia optimus" i es tornava boig i no ensenyava res per pantalla.

Ara mateix estic amb ubuntu, i amb la intel (crec que és la intel). Tal i com me l'ha configurat l'ubuntu ell sol estic anant amb tots les efectes de l'escriptori i estic molt content. L'ordinador em va perfecte amb Ubuntu, molt millor que amb Window$ 7.

Si algú sap alguna cosa sobre com puc mirar quina tarja gràfica tinc activada, digueu-m'ho. Que així podré postejar-ho per aquí i fer algun review per a la comunitat catalana, perquè estic fart de llegir reviews amb anglés.

Sort!

---

### Post by wgarcia on 2010-11-10
No és mala estratègia, si almenys et funciona una de les targetes, perquè més d'hora que tard apareixerà el suport per la doble targeta. 

Per veure quines targetes tens activades pots fer des d'una terminal:

lspci | grep -i vga

---

### Post by albandy on 2010-11-12
Tingueu present que Ubuntu vol fer servir Wayland en comptes de Xorg a la 11.04 i wayland suporta el gpu hot swap, per lo que suposo que no hi haurà problema amb aquesta tecnologia

---

### Post by ssssuizaaaa on 2010-11-12
idrojsnop,

Suposo que vols dir que t'has comprar el ASUS U33JC. Jo tinc aquest i el tinc amb doble boot amb Windows 7 i Ubuntu netbook amb unity. Apart de problemes amb unity que es un escriptori que m'agrada molt pero que sembla que encara no està acabat del tot, el principial problema que li trobo es que gasta molta bateria. Més del doble que windows 7 i aixó per un portatil que una de les seves virtuts és la duració de la bateria, és difícil d'entomar. Estic mirant d'arreglar el tema, aquí deixo links per si hi ha algu altre interessat:
[http://beyondteck.blogspot.com/2009/01/improve-battery-life-on-linux-laptop.html](http://beyondteck.blogspot.com/2009/01/improve-battery-life-on-linux-laptop.html)
[http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/](http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/)
[http://www.lesswatts.org/tips/index.php](http://www.lesswatts.org/tips/index.php)

Salutacions,

Xavier

---

### Post by idrojsnop on 2010-11-22
He estat mirant-me tota la informació que m'heu proporcionat i us vull dir unes quantes coses.

En primer lloc. Teniu idea de quina de les dues tarjetes m'està funcionant? Al fer la comanda "lspci | grep -i vga", em surt el següent:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

M'agradaria saber què passa per tal de intentar optimitzar al màxim la duració de la bateria. I podre-ho compartir amb els altres usuaris d'ubuntu que tenen el mateix "problema" que jo.

En segon lloc dir que ubuntu 11.04, incorporarà l'Unity però segurament no substituirant Xorg per Wayland fins a l'alliberament de la versió 11.10. A més d'això, pel que he llegit (corregiu-me si m'equivoco), Wayland encara no incorpora la tecnologia per a poder balancejar les GPU. Per tan, per a solucionar el problema, els usuaris d'ubuntu haurem d'esperar com a mínim a la versió 11.10... un anyet.

Us deixo un enllaç molt interessant que parla de tot això i del desenvolupament d'aquesta tecnologia (anglès): [http://www.phoronix.com/scan.php?page=news_item&px=ODc2NQ](http://www.phoronix.com/scan.php?page=news_item&px=ODc2NQ)

Pel que fa a la tecnologia "GPU hot swap", no he sabut trobar res gaire interessant per la xarxa. Algú em pot explicar en què consisteix? I qui la desenvolupa?

També dir que hi ha una gent que estan intentant desenvolupar la tecnologia "Linux Hybrid Graphics", aquest bloc n'és la columna vertebral: [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/).

Jordi.

PD: Disculpeu per contestar tan tard, hehe. Amunt el tema, que s'ha posat molt interessant! Per cert, el portàtil q tinc és el mateix que en Xavier, l'ASSUS U33JC.

---

### Post by wgarcia on 2010-11-22
Em sembla que si dones la comanda amb l'opció "-v", és a dir:

lpsci -v | grep -i vga

podràs veure quina de les dues targetes està operativa.

---

