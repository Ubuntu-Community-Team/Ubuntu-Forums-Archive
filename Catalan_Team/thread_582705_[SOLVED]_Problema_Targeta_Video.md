---
title: "[SOLVED] Problema Targeta Video"
date: 2007-10-20
forum: Catalan Team
---

### Post by kukat on 2007-10-20
Primer de tot, espere que ho passeu molt bé a la Festa!!!!!!

Bé, ja tinc la nova distro, i quan vaig arrencar per primera vegada amb ella, hem va demanar d'instalar els drivers de la meva ATI. Jo, totalment convençut de que en aquesta aniria, ho vaig fer. 

Pero al reiniciar el ordinador, es queda la pantalla en negre. Però he pensat una cosa... I si la resolució es molt gran i no es soportada per la meva pantalla? Hi ha alguna manera de configurar la resolució de pantalla amb algún commandament? Ho dic per que el sistema si que funciona, però no es veu res a la pantalla. La questió serie algún comandament per a baixar-li la resolució, o alguna cosa així. 

O altra opció seria desinstalar el driver, però com? 

Gràcies.

---

### Post by xoldy on 2007-10-20
Hola bon dia, a mi sempre m'ha anat molt be cridar la consola, i he seguit aquest [fil]("http://ubuntuforums.org/showthread.php?t=510985&highlight=ati"). 
En Carles Oriol explica com fer-ho. Seguint les instruccions per instal·lar el driver fglrx i després reconfigurant les finestres, podras triar les ressolucions suportades per la teva targeta. En el meu cas concret, com hauràs llegit en altres fils, és una ATI x1600 i com a màxim li puc posar una 1280x800, però es veu molt nítid. Una batalla que penso que tinc perduda és la de poder veure els efectes d'escriptori, però em fa una mica de por seguir instruccions que he llegit pels fòrums. Voldria conservar aquesta instal·lació uns mesos.

Espero que et serveixi.

---

### Post by kukat on 2007-10-22
Al.lucinant. Així m'he quedat després de solucionar (a mitges) el problema de la targeta gràfica. 

Quina idea va passar pel meu cap quan se me va ocorrer probar l'Ubuntu amb la meva pantalla de 15 polsades (una deixes que tenen la pantalla petita, que crec que tendrà més de 10 anys...) I misteriosament funcionaba!!!! 
Ho conte més detingudament. La pantalla en un principi estava partida en uns 5 o 6 trossos, però m'ho he apanyat per a baixar-li la resolució quasi a ceges, i ara funciona bé. 

A qui se li va ocorrir posar la resolució a 1900 x no se qué???? Normal que no funcionara. També he dut una pantalla plana d'un amic que se l'havia acabat de comprar i posava: "Input Device not Suported"... No funcionava ni amb la pantalla plana, i ho feia amb una de fa 10 anys!!!

Ara ja la tinc en la pantalla que normalment gaste, però conectant-la en "calent", ja que la pantalla de posar la contrasenya i el nom d'usuari està a la resolució de 1900 x alguna cosa. 

Hi ha alguna forma de canviar-li la resolució a la pantalla d'entrada dels usuaris??????? 

Coses curioses que passen en la vida d'un Ubuntaire amb una tarja ATi. 

Gràcies (espere  que no vos moleste tot aquest rollo)

---

### Post by kukat on 2007-10-22
Crec que hem tocarà deshabilitar el controlador restringit d'Ati, i esperar a veure si trauen el controlador lliure (que no se si aixó ocorrira algun día).

De moment tinc 3 problemes, i crec que estàn tots relacionats amb la targeta: 

1. L'inici amb els usuaris, que tendrà una resolució de 1920 x 1440, i la meva pantalla no ho soporta ( ni la majoria, per el que he vist amb la pantalla plana que he portat). 

2. Els videos es veuen de forma extranya. Es veuen partits. Ha Youtube es veuen bé, però a l'ordinador ni de conya. 

3. Ara pareix que l'OpenOffice tampoc funciona, degut a no se quina cosa de Java, hem dona el seguent error:* (process:15792): WARNING **: Unknown error forking main binary / abnormal early exit ...*

Per lo demés funciona de meravella. Però són problemes greus...

Si no es pot solucionar, llevaré el controlador, i ha funcionar sense ell fins que tragen algún...

---

### Post by kukat on 2007-10-25
Section "Screen"
	Identifier	"Default Screen"
	Device		"Targeta de vídeo genèrica"
	Monitor		"Monitor genèric"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4

Puc canviar alguna cosa aquí per a que no hem surta la pantalla d'inici (la de usuari i contrasenya) a una alta resolució, per a que no s'apague el monitor????

Si es esborrant les altes resolucions, ho arreglarem fàcilment...

Gràcies

---

### Post by Satboy on 2007-10-25
Hola Kukat,
 Vés a **Sistema -> Administració -> Finestra d'entrada -> Seguretat**,  i si així ho desitges, marca la casella "habilita l'entrada automàtica" així ja mai més et demanarà l'usuari i la contrasenya i se t'engegarà l'**Ubuntu** sol.

 Siau! ;-)

---

### Post by kukat on 2007-10-26
Gràcies!!! 

Ara l'únic problema que tinc es la reproducció dels videos, el Open Office i el XPDF, que no hem funcionen amb els drivers privatius d'ATI (els videos hem surten fora de la finestra del programa!!). Es una pena, ja que tot el demés funciona de meravella, i si deshabilite el driver els gràfics van molt lents i costa molt de carregar les webs. 

Que li falta per a que funcionen aquestos programes i els reproductors de videos??? TInc que instalar alguna cosa per a que funcione bé, o simplement esperar a veure si trauen un driver decent? 

l'Abi Word si que hem funciona bé, així que no sé si es que hem fa falta instalar alguna cosa. Gràcies novament.

---

### Post by kukat on 2007-11-12
Bones gent!!!!!


La meva "lluita" amb l'ATI continua. Espere que hem pugeu ajudar resolvent alguns dubtes, ja que s'hem fa dificil saber les noves noticies sobre ATI/drivers/linux. 

Bé, com ja sabreu tinc una ATI Club 3d Radeon 1650 pro, que porta molts problemes en Linux (en que estaria pensant, per que no vaig comprar una NVIDIA!!!:(),

Fa dues setmanes va sortir aquesta noticia:

[http://www.fayerwayer.com/2007/10/wena-ati-nuevos-drivers-para-linux-con-soporte-para-compiz/](http://www.fayerwayer.com/2007/10/wena-ati-nuevos-drivers-para-linux-con-soporte-para-compiz/)

Algú hem pot explicar si açó vol dir que ja es pot fer alguna cosa amb la meva tarja????? Tinc que instalar alguna cosa, o encara no funcionaria bé amb el meu model? He estat investigant però no trobe res en clar.

Moltes gràcies a tots en un dia tan trist.

---

### Post by CarlesOriol on 2007-11-12
Inta&#320;la els controladors amb l'envy ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ) fins que ho hagi una versió final.

---

### Post by kukat on 2007-11-12
:oops: No sé com instalar-ho... Hem baixe el paquet envy_0.9.8-0ubuntu13_all.deb, però després no se com fer-ho per a que funcione aquest programa...Primer descomprimeixc el paquet, i hem surten 2 arxius comprimits: control.tar.gz i data.tar.gz...però no se com instalar-los...

No es pot fer un sudo apt-get install per a instalar-ho? he provat sudo apt-get install envy,però no funciona (supose per que no està als repositoris oficials, no?) 

Gràcies company!

---

### Post by kukat on 2007-11-12
Moltes, moltes, moltíssimes gràcies!!!!!!!!!:guitar:

Es tanta la meva alegria, són tants els mesos i mesos esperant aquest moment, que estic eufóric....

Per fi, ha passat: L'ATI CLUB 3D RADEON 1650 PRO HEM FUNCIONA!!! Ja funcionen els efectes!!!! Ara solament hem fa falta vorer com funcionen  els efectes, però de segur que m'ensenyaré de seguida!!! 

Moltes gràcies una vegada més. Si no fos per vosaltres, mai ho havera acoseguit. Es tanta la bellesa d'aquest sistema operatiu, que quasi se me cau la llagrimeta...jejejejej. Massa euforia, massa mesos esperant, i per fi!!! 

De seguida pose el [SOLVED]

Gràcies una altra vegada!!!!:guitar:  Rock!!!

---

### Post by CarlesOriol on 2007-11-13
F E L I C I T A T S !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

