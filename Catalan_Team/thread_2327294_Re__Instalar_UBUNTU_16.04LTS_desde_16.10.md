---
title: "Re:  Instalar UBUNTU 16.04LTS desde 16.10"
date: 2016-06-09
forum: Catalan Team
---

### Post by martibitria on 2016-06-09
Hola de nou altre vegada,
Vull instal·lar el 16.04LTS, per consell vostre i no m'en surto!! en el llapis USB ja tinc descarregat el ISO de UBUNTU 16.04LTS

Quan engego ordinador prement F12 o F2, entrar BIOS, per arrancar per USB a mi en el meu ordinador no em surt, el llapís USB. per tant sempre engega desde el disc dur es a dir el UBUNTU 16.10.

Jo quan vaig instal·lar UBUNTU desde el XP, ho vaig fer amb la imatge ISO al USB i un programa que no recordo el nom algo així com universal USB installer o linux live creator. de veritat no recordo, aquets els he mirat per internet.

No se que faig malament!! Haig de formatejar tot?? a on he vist em diu que no, que aixo mai

He mirat per internet i uns diuen començar per creador discos arrencada i res, altres m'han fet anar al Gparted. els programas que esmentat abans,  el USB installer i el linux live creator no me funcionan.

Teniu alguna guia infalible? el ordinador el puc formatejar sense problemes, no tinc cap dada ni res important.

Gracies

Martí

Per cert,
el meu ordinador és un Toshiba Satellite L20-101

---

### Post by wgarcia on 2016-06-09
Has creat l'USB d'instal·lació amb el "Creador de discs d'arrencada" (no sé si es diu exactament així) de l'Ubuntu? O has copiat directament la imatge a la memòria USB? Si has fet aquesta segon opció no arrencarà, has de fer-lo amb el programa de creació de discos d'arrencada.

---

### Post by martibitria on 2016-06-09
Jo el que he fet he descarregat el ISO de la pagina de UBUNTU i l'he copiat al pendrive.

D'aquí he obert el creador de disc d'arrencada i he fet el que deia. I aquest pendrive per explicarme s'ha convertit en UBUNTU 16.04, OK?? pperò d'aquí ja no fa res més. he engegat de nou ordinador i res.
Això també ho he probat amb el ISO, pero de la carpeta de baixada i res!

Gracies

---

### Post by jmaspons on 2016-06-10
des de quina versió d'Ubuntu has creat el disc d'arrencada? Sembla ser que la versió del creador de discs d'arrencada d'Ubuntu 14.04 i anteriors no permeten crear imatges de les versions 15.10 i posteriors.

---

### Post by wgarcia on 2016-06-11
Penso que hauries de mirar si l'ordinador està configurat per arrencar primer des de l'USB que des del disc dur. Això es fa entrant a la configuració abans que l'ordinador comenci el sistema operatiu, normalment prement la tecla F2 o F4 (la major part de sistemes et mostren un missatge dient quina tecla és just després de prémer el botó d'arrencada de l'ordinador). Al menú de configuració s'ha de buscar quelcom semblant a "Boot" i aquí mirar algun lloc on puguis reordenar la seqüència (primer disc USB, segon disc dur , etc.).

El problema que diu el jmaspons sí que hi és, però 1) donaria un missatge d'error diferent al que em sembla que li dóna al martibitria, 2) el programa de creació de discos d'arrencada el van arreglar a les últimes versions, si ho ha fet des de la 16.10 que tenia instal·lada penso que hauria de funcionar.

---

### Post by martibitria on 2016-06-11
Arrencar primer desde el USB, no em deixa, no hi ha la opció desde BIOS!!!! Per això ho feia desde aquells programes USB installer o algo aixi.

Per CD podria però tampoc em deixa, diu que el CD no es un arxiu local o algo aixi

---

### Post by wgarcia on 2016-06-11
Quins dispositius d'arrencada hi ha a la llista de dispositius disponibles al menú de configuració de la BIOS?

---

### Post by martibitria on 2016-06-12
LAN
FDD
CD/DVD
+HDD

He arrancat amb el USB conectat

[IMG]http://i64.tinypic.com/es0y7d.jpg[/IMG]

---

### Post by wgarcia on 2016-06-12
No hi ha cap altre lloc al menú de configuració de la BIOS que sigui per habilitar l'USB? En tot cas, també es podria gravar un DVD (a les últimes versions la imatge d'instal·lació no cap en un CD) i arrencar des del DVD.

---

### Post by martibitria on 2016-06-13
No, la USB no és pot habilitar.
A la BIOS ja he posat arrencar primer per CD/DVD.
Per DVD, no puc, em baixo el ISO, I com s'ha de posar o copiar al DVD, ja ho he fet pero em surt fallo, us ensenyo foto de pantalla i mostra del que he fet per si ho faig malament.

Copio i enganxo a CD i clicko escriu al disc
[IMG]http://i65.tinypic.com/2reoaw8.jpg[/IMG]

Enregistro com a fitxer. (enregistre el contingut també ho he probat)
[IMG]http://i66.tinypic.com/2mq9oxf.jpg[/IMG]

Aqui enregistre
[IMG]http://i65.tinypic.com/2cxbuo2.jpg[/IMG]

Després em surt aquest error
[IMG]http://i66.tinypic.com/r0e2hj.jpg[/IMG]

---

### Post by wgarcia on 2016-06-13
Hauria de ser "Enregistra com a contingut", no com a fitxer. Acaba bé l'enregistrament o et dóna un error?

---

### Post by martibitria on 2016-06-13
Hola

Ho he fet enregistra com a contingut i em surt el error de la ultima foto.

I gracies per tota la ajuda

---

### Post by wgarcia on 2016-06-14
Sembla que el dispositiu CD/DVD està donant un error. A vegades netejant la lent s'arregla, o potser sigui un error més complicat. Saps si aquesta unitat funciona bé?

---

### Post by martibitria on 2016-06-14
Ostres el CD/DVD, no em funciona!!!

He posat un CD i no llegeix

---

### Post by wgarcia on 2016-06-14
Té algun altre dispositiu d'entrada l'ordinador?

---

### Post by martibitria on 2016-06-15
No, no tinc cap altre

---

### Post by wgarcia on 2016-06-16
Però té connexió a Internet?

---

### Post by martibitria on 2016-06-16
sí

---

### Post by wgarcia on 2016-06-17
Una cosa que no entenc és com vas instal·lar la versió 16.10 si el CD no et funciona i no pots arrencar des d'USB, segons entenc?

---

### Post by martibitria on 2016-06-17
La versió 16.10 va ser amb la ordre sudo do-release-upgrade -d del terminal.

La versio 16.04LTS, la vaig instal·lar amb ISO dins un USB més un programa que no recordo el nom que te feia arrencar desde USB.

El programa era un com aquest, però per UBUNTU no serveix

[https://es.answers.yahoo.com/question/index?qid=20110627214501AAhne4n](https://es.answers.yahoo.com/question/index?qid=20110627214501AAhne4n)

Hi havien molts altres ppero no serveixen per UBUNTU

---

### Post by wgarcia on 2016-06-19
Interessant aquesta opció, no la coneixia, sempre s'aprèn alguna cosa nova. Llegint una mica més, sembla que aquest és un mètode possible per al teu cas on no hi ha l'opció d'iniciar des d'USB al menú de configuració del BIOS i tampoc no et funciona el CD ROM (això sembla l'acudit aquell que xocaran dos trens i res funciona per evitar-ho). 

Però abans s'ha de determinar com està instal·lat el sistema, en quines particions. Per això convé donar l'ordre següent:

```
sudo fdisk -l
```

Això indicarà els discos durs que hi ha i l'ordre de les particions.

---

### Post by martibitria on 2016-06-19
[IMG][IMG]http://i66.tinypic.com/6svrlc.png[/IMG][/IMG]

[IMG][IMG]http://i65.tinypic.com/2bruyp.png[/IMG][/IMG]

[IMG][IMG]http://i68.tinypic.com/205b9fo.png[/IMG][/IMG]

---

### Post by wgarcia on 2016-06-19
D'acord, a l'última línia es veu que el sistema està instal·lat a la partició /dev/sda1, això serveix a sota quan es fa una entrada al menú grub que apunti a un programeta que en teoria permet arrencar des d'usb.

Doncs aquí van uns passos amb el benentès que jo no ho he provat mai, però considerant que no tens dades a preservar, no costa res provar-ho. S'ha de fer servir un programa que es diu "plop boot manager", però el problema és que aquest programa està pensat per a Windows i no per a Linux. Tot i així, es pot forçar l'ordinador a iniciar des d'aquest programa. A més d'això hi ha altres opcions a la pàgina d'aquest programa, però primer es pot provar el següent:

1) S'ha de baixar l'última versió de "plop manager" des de:
[https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)

S'ha de baixar l'última versió dels "zip" que es veuen a la primera taula, per exemple la que veig jo és "plpbt-5.0.15.zip", desant el fitxer a algun lloc on el podem trobar amb el navegador de fitxers.

2) Clicant sobre el fitxer-arxiu "zip", s'obre el programa de descompressió, i s'ha d'extraure un fitxer que està a la carpeta "/plpbt-5.0.15/Linux/" i que es diu "plpbt.bin". Es pot extraure sols aquest fitxer arrossegant-lo des del programa de descompressió fins a l'escriptori, per exemple, o extraure tot i buscar aquest fitxer dins de les carpetes que es creen (que tindran el nom indicat abans).

3) Ara des d'una terminal, s'ha de copiar aquest fitxer a la carpeta d'inici del sistema:
```
 sudo cp plpbt.bin /boot 
```
primer s'ha de navegar a la terminal a la carpeta on està aquest fitxer, o donar tot el camí perquè l'ordre "cp" trobi el fitxer.

4) Ara s'ha de modificar el menú d'arrencada "grub" perquè el sistema arrenqui des d'aquest programa. Per això primer s'ha d'editar un fitxer:

```
sudo nano /etc/grub.d/40_custom
```

S'han de afegir les següents línies al final d'aquest fitxer:

```

menuentry "Instal·la Plop Boot Manager" {
    set root='(hd0,1)'
    linux16 /boot/plpbt.bin
}

```


5) Ara has de reiniciar el sistema. Com sols tens instal·lat linux, perquè es vegi el menú del grub2, has de prémer la tecla de majúscula en quan s'iniciï el sistema perquè es mostri aquest menú. En aquest menú s'hauria de veure una entrada que digui "Instal·la Plop Boot Manager". Escull aquesta opció i ara t'hauria de sortir un menú amb opcions per iniciar des d'USB. 

Si es queixa que li falten llibreries, s'haurà de compilar el programeta primer, per tant es complica la cosa una mica, però no gaire.

---

### Post by martibitria on 2016-06-19
Una cosa, jo actualment tinc instalat el UBUNTU 16.10, 

Ho dic per això:** "Doncs aquí van uns passos amb el benentès que jo no ho he provat mai,  però considerant que no tens dades a preservar, no costa res provar-ho.  S'ha de fer servir un programa que es diu "plop boot manager", però [COLOR=#ff0000]el  problema és que aquest programa està pensat per a Linux i no per a  Windows[/COLOR]. Tot i així, es pot forçar l'ordinador a iniciar des d'aquest  programa. A més d'això hi ha altres opcions a la pàgina d'aquest  programa, però primer es pot provar el següent:"**

Que no ens hagim entes??

Confirma que provi el que has dit al anterior post!!

Gracies

En el punt 3, no ho ser fer!!!
Això:[B] primer s'ha de navegar a la terminal a la carpeta on està aquest fitxer,  o donar tot el camí perquè l'ordre "cp" trobi el fitxer.

[/B]

---

### Post by wgarcia on 2016-06-19
Volia dir "pensat per a Windows i no per a Linux", he editat i corregit el missatge anterior. 

Segurament s'haurà baixat a la carpeta "Baixades" de la teva carpeta d'inici. Per tant si el teu usuari és "pepitu" , per navegar a aquesta carpeta pots donar la següent ordre a la terminal:

```
cd /home/pepitu/Baixades
```

Substitueix "pepitu" pel teu nom d'usuari, que a les captures anteriors em sembla que és "marti".

---

### Post by martibitria on 2016-06-19
OK.
Com puc escriure o copiar les lineas del final del punt 4??


només em surt per escriure a dalt de tot i despres per confirmar com es fa??

Això que diu de ^(mes la lletra) no se com es fa, he probat de escriure i res!!!!!

Disculpa t'estigui donant la tarda

[IMG][IMG]http://i63.tinypic.com/16aqf5v.png[/IMG][/IMG]

---

### Post by wgarcia on 2016-06-20
Amb les fletxes pots anar a l'última línia i posar-te al final de la línia. Un cop aquí si prems la tecla "Intro" et crearà una nova línia i pots escriure.

---

### Post by martibitria on 2016-06-22
Quan escric la línia clicko control +o (per desar) i al final em surt un [B]$ 

[/B]Ara que haig de fer més?? 

[IMG][IMG]http://i65.tinypic.com/105w57p.png[/IMG][/IMG]

---

### Post by wgarcia on 2016-06-23
Ara hauries de reiniciar l'ordinador, i prémer la tecla majúscula tan bon punt comença a engegar perquè es vegi el menú "grub" d'arrencada. A aquest menú t'hauria de sortir una entrada que posi "Instal·la plot boot manager". Clicant aquesta opció s'hauria d'iniciar aquest programa i mostrar-te l'opció d'iniciar des d'usb.

---

### Post by martibitria on 2016-06-23
M'ha sortit això

Penso que és UNetbootin, però que et sembla si fem Install Ubuntu??

Si fem install ubuntu es instal·larà el 16.04 o el 16.10??

Moltes gracies per la teva paciència un deu per tu

[IMG][IMG]http://i63.tinypic.com/59yjy8.jpg[/IMG][/IMG]

---

### Post by martibitria on 2016-07-02
Amb aixo no se que sha de fer

[IMG][IMG]http://i65.tinypic.com/2rdkvbt.png[/IMG][/IMG]

---

### Post by wgarcia on 2016-07-04
Has de crear la partició per al sistema i muntar-lo ("/"). Mira si les explicacions que donen en aquest missatge et serveixen (està en anglès):
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by martibitria on 2016-07-04
He probat i em dona fallo, el meu angles es nul!!!

despres he probat aquest i tambe em dona error.

[https://www.google.es/?client=firefox-b#q=crear+particio+ubuntu&gfe_rd=cr](https://www.google.es/?client=firefox-b#q=crear+particio+ubuntu&gfe_rd=cr)

---

### Post by 77zetadisseny79 on 2016-07-04
Hey Nois! Disculpeu estaba totalmente perdut amb el foro anglés. Soc toalment en el mon de Ubutuntu, mágradaria que recomanareu algun fil díntroduccio. Merci

---

### Post by wgarcia on 2016-07-05
Hola 77zetadisseny79,

Regla número 1: obre el teu propi fil i no facis servir fils existents per a les teves preguntes.

---

### Post by wgarcia on 2016-07-08
martibitria: quin fallo et dóna? I tinc una curiositat: com has acabat solucionant el problema de manca de CD i USB per instal·lar?

---

### Post by martibitria on 2016-07-10
He instal·lat en altre ordenador amb el mateix problema de la BIOS que no reconeix USB.

D'aquesta manera: **instalar con unetbooting**
[http://paraisolinux.com/4-maneras-de-instalar-ubuntu-sin-cd-ni-usb/](http://paraisolinux.com/4-maneras-de-instalar-ubuntu-sin-cd-ni-usb/)

---

### Post by martibitria on 2016-07-10
del error em surt això
[IMG][IMG]http://i65.tinypic.com/o69uhf.jpg[/IMG][/IMG]

---

### Post by wgarcia on 2016-07-11
No sé exactament com funciona la instal·lació usant unetbootin, perquè ho fa des del propi sistema, i per tant el sistema està muntat i no deixarà canviar les particions. Possiblement primer hagis de crear una partició buida, reduint la mida d'alguna de les existents, amb prou espai per instal·lar l'Ubuntu. Un cop instal·lat l'Ubuntu a aquesta partició buida usant el unetbootin, un cop reiniciat el sistema, s'ha d'escollir arrencar aquesta instal·lació. I llavors es pot eliminar l'altra instal·lació anterior i recuperar l'espai que ocupaven aquestes particions.

No sembla una tasca fàcil si no es disposa d'una certa experiència amb Linux, particions, etc.

---

