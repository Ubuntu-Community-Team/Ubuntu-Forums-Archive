---
title: "Error a /dev/sda"
date: 2012-11-27
forum: Catalan Team
---

### Post by gilcent on 2012-11-27
Hola,

Sóc un usuari amateur de l'Ubuntu. Estic intentant instal·lar-lo a un portàtil vell de la meva veina, és un compaq nx9005. He inserit el cd de l'ubuntu 10.04 i pensava després actualitzar-lo amb l'ultima versió a través del gestor d'actualitzacions. El cert és que segueixo totes les passes que em diu, faig les particions o en altres intents faig; "esborra el disc i utilitza'l per complet". Tant amb particions com sense, quan comença a instal·lar-se i es troba al 15% del procés em surt un missatge d'error on diu:
[B]
Imput/output error during read on /dev/sda[/B]

He provat també d'instal·lar l'ubuntu 9.04 alternate i em surt el mateix error.
Que algú sap què pot ser?

Fins aviat

---

### Post by wgarcia on 2012-11-27
Aquest missatge pot ser degut a diverses causes:

1) Alguna configuració del BIOS de l'ordinador, com ara una contrasenya per accedir o una opció de SATA que no correspon. Si pots entrar a la configuració del Bios en iniciar la màquina pots provar diverses opcions a veure si t'ho arregla.

2) El disc o USB que estàs usant per fer la instal·lació està malament. Prova amb un altre. 

3) El disc on estàs instal·lant té fallades, mira si aconsegueixes alguna eina de diagnosi de discos, hi ha uns CD live que porten aquestes eines.

Per cert, tots som usuaris amateurs per aquestes contrades...

---

### Post by gilcent on 2012-11-28
Dubto que sigui el Cd d'instal·lació, ja que n'he provat dos el 10.04 i el 9.04 i em dóna el mateix error. El cert és que no sé si he aconseguit entrar al BIOS. Si premo F2 em demana un password que no tinc el qual per desactivar-lo, segons internet, haig de desmontar la pila del BIOS i no sóc capaç de desmuntar l'ordinador d'un altre. Si premo "esc" em surt el "Boot Menu"; 1.+Removable Devices. 2.CD-ROM Drive, 3.+Hard Drive, 4.Built-In LAN, però en cap moment puc modificar res, només escollir-ne una i prémer intro.
Potser el cd d'anàlisi de discs em pot resoldre el problema o només ho analitza? Creieu que m'ho puc arreglar o en aquest cas dur-lo a un professional.

A reveure

---

### Post by wgarcia on 2012-11-28
Això de la contrasenya és sospitós, és possible que sigui la raó per la qual no es pot accedir a crear particions noves. 

Quant als discos d'anàlisi també porten eines per corregir errors als discos, però si un disc dur comença a fallar molt és millor canviar-lo i no estar sempre arriscant el desastre. Però no és segur que aquest sigui el problema, sobretot si l'altre sistema operatiu no dóna cap mena d'errors.

---

### Post by gilcent on 2012-12-04
D'acord, continuaré fent algunes proves, vejam si ho aconsegueixo. Si no ho provaré canviant el disc dur.

Fins aviat

---

