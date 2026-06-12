---
title: "errors de firmware"
date: 2007-08-28
forum: Catalan Team
---

### Post by muleta on 2007-08-28
Després de 64 execucions, quan he engegat l'Ubuntu, m'ha fet una mena de revisió general del pc i he vist que detectava diversos errors de firmware.

Potser no són importants perque s'ha iniciat i sembla que tot funciona.

És possible que els repari o que crei mecanismes de defensa per a passar-los per alt?.

---

### Post by papapep on 2007-08-28
Muleta, si no ens poses el missatge concret no tenim manera de saber de què parles, ho podem suposar, però res més.

---

### Post by muleta on 2007-08-28
Caram!. És que és molt difícil...

No són missatges sino aquells llistats que apareixen en pantalla negre, abans que s'obri el sistema operatiu i que no donen temps a prendre'n nota, amb prou feines a llegir-ho.

---

### Post by papapep on 2007-08-28
Fes-los una foto i la penges :-D

Per molt ràpid que sigui, tu entens que si no sabem què diuen, poc podem saber què contestar-te, oi? ;-)

---

### Post by muleta on 2007-08-28
Sí, ja ho entenc. No pretenia pas que ho endevinéssiu. De fet, ja he dit que no ho considero important. Només preguntava si és possible que l'Ubunto ho hagi resolt perque sempre dieu que s'encarrega de fer neteja i reparar errors.

No sabria com invocar-ho. :-k Potser hauré d'esperar 63 execucions més...8-[

L'ubuntu no fa scandisk, desfragmentació del disc i aquestes coses a demanda de l'usuari?.

---

### Post by papapep on 2007-08-28
Per definició Ubuntu, i qualsevol altra Linux, fa el que pugui fer windows i millor :-P

Respecte el tema de scandisc, té una eina que fa una tasca "similar" que es diu fsck (File System Check) que verifica cada certes vegades que es reinicia el sistema que estigui íntegre i, en cas de trobar problemes, intenta solucionar inconsistències que detecti al mateix.

Pensa que qualsevol similitud entre NTFS (ja no parlem dels FAT's) i EXT2, EXT3, ReiserFS i cia. és ciència ficció. 
Aquests sistemes de fitxers ja són molt més robustos que els primers que he citat, però a més, les eines que tens per a solucionar hipotètics problemes, que també en tenen, són molt superiors a les que tu esmentaves.
Et pots quedar sense un disc dur o les seves dades per culpa d'un error de ferro (que el disc dur s'ha mort) però és difícil que et passi per culpa del sistema de fitxers.

De la fragmentació: els tipus de sistemes de fitxers que t'he esmentat abans s'encarreguen ells solets d'estar ben nets i polits i el ràtio de fragmentació es manté en nívells mínims gairebé sempre, sense intervenció humana.

Òbviament, pots invocar manualment l'fsck (**ATENCIÓ: abans de fer-ho, que ja ens coneixem...és una eina que mal emprada et pot deixar el sistema fet un nyap. Informa't/Pregunta abans**). T'hem respost, per ara, algun cop "això no es pot fer"??? :-D

---

### Post by CarlesOriol on 2007-08-29
Els errors del firmware probablement son firmwares que et falten per determinats dispositius del teu ordinador.

Probablement un dispositiu usb (impresora, capturadora tv,...)  o alguna controladodra wifi (athena, broadcom 43xx...)

Quan vegis l'error t'ajudem a aconseguir-los

---

### Post by muleta on 2007-08-29
Gràcies a tots dos.

---

### Post by muleta on 2007-09-03
> **CarlesOriol said:**
> Els errors del firmware probablement son firmwares que et falten per determinats dispositius del teu ordinador.

Probablement un dispositiu usb (impresora, capturadora tv,...)  o alguna controladodra wifi (athena, broadcom 43xx...)

Quan vegis l'error t'ajudem a aconseguir-los

Ha tornat a sortir!. He agafat al vol un dels errors que, afortuunadament per a la meva velocitat d'escriptura, s'anava repetint. Era, més o menys, entre punts, barres i altres signes, alguna cosa així:

"error loading lib firmware bcn 43xx microcode5.fw"

Us sona a res?.

---

### Post by papapep on 2007-09-03
A mi no, però conec un tiu (de nom Gúgel ;-)) que diu que és el firmware d'una tarja wifi Broadcom, que suposo que deu ser la que té el teu ordinador.

Si no la fas servir no és cap problema gros, si la fessis servir segur que ja ho hauries detectat.

---

### Post by CarlesOriol on 2007-09-04
Té raó en gugel aquest que diu en papape, et falta el firmware privatiu de la tarjeta wifi broadcom 4300.

Pots extreure el firmware de la mateixa tarjeta usant el programa bcm43xx-fwcutter però: si uses el controlador lliure tindras la velocitat limitada a 11mbs

T'aconsello que si vols usar-la uti&#320;litzis el mòdul ndiswrapper amb el controlador de windows deshabilitant el bcm43xx a etc/modules/blacklist. 

Pensa que en qualsevol cas estas usant programari privatiu sigui el firmware o sigui el controlador de windows

---

### Post by muleta on 2007-09-04
Novament, gràcies a tots dos.

De moment, no em complicaré més la vida i tiraré de cable. Si vull connexió wifi, utilitzaré un altre pc amb windows.

Potser més, endavant, quan hagi après més a moure'm per l'entorn Linux, ho intenti arreglar.

---

### Post by CarlesOriol on 2007-09-04
Amb l'ndiswrapper i aquesta tarjeta en 3 minuts es pot muntar sense cap mena de problema.

El dia que vulguis quedem a l'irc i ho fem junts

---

### Post by muleta on 2007-09-05
Agraeixo el teu oferiment, Carles, però crec que tinc seriosos problemes de firmware.

Se'm instal·len i desinstal·len programes sense el meu permís. No descarto que ho hagi provocat jo mateixa. Per exemple, l'altre día vaig descobrir que tenia instal·lat Network  Management i, com que no sabía què era ni ho havia instal·lat pas, vaig creure que ja es negaria a desinstal·lar-se si era necessari i ho vaig desinstal·lar amb l'afegir/eliminar. Potser no ho tenia d'haver tocat.

Més tard vaig instal·lar l'mldonkey, amb totes les dificultats que comporta i, cada vegada que el tanco, es desinstal·la.

Ahir, sense tenir cap programa en funcionament, el pc es va enlentir moltíssim en l'execució de qualsevol ordre meva. Fins i tot el cursor anava una mica a la seva. Si hagués estat a Windows hauria pensat en un virus o spyware i hauria passat tota mena de antitots.

Vaig fer un test de memoria amb el cd-live i, com que a les 4 hores només n'havia realitzat el 78 %, l'he deixat treballar tota la nit. Doncs bé: Aquest matí estava exactament en el mateix punt, però amb 0 errors.

Si tot això és culpa meva vol dir que no n'aprendré mai i que Linux no és pas per a tothom sino per a personas especialment capacitades.
 
Windows deu tenir la seva raó d'existir, si algunes persones no som capaces de fer funcionar Linux. Allà no cal saber-ne, perque el SO s'encarrega de tot, dialoga amb l'usuari utilitzant un llenguatge fàcil, fins i tot no cal saber anglès per accedir a les pàgines d'ajuda o per instal·lar control·ladors.

---

### Post by CarlesOriol on 2007-09-05
Bé... es un post curiós...

anem per parts:

> rec que tinc seriosos problemes de firmware.

No tens cap problema amb el firmware. L'unic que et falta aquest de la targeta wifi que tens.

> Se'm instal·len i desinstal·len programes sense el meu permís.

Ni de conya, això no és windows.

El network-manager s'insta&#320;la predeterminadament amb l'ubuntu,

El mldonkey el desconec però es impossible que per molt que ell mateix vulgui es desinsta&#320;li sol. 

> Ahir, sense tenir cap programa en funcionament, el pc es va enlentir moltíssim en l'execució de qualsevol ordre meva. Fins i tot el cursor anava una mica a la seva. Si hagués estat a Windows hauria pensat en un virus o spyware i hauria passat tota mena de antitots. 

Si pot ser, en la insta&#320;lació predeterminada de l'ubuntu hi ha determinats programes que s'activen de manera temporitzada i que pots veure al monitor del sistema. Bàsicament son 2 indexadors el updatedb que analitza tots els arxius de l'ordinador per quan vulguis fer un locate i un altre d'insta&#320;lació manual el servei del beagled. 

El test de memòria (per molta que en tinguis) ha de durar minuts no hores, es possible que hi hagi algun error al teu ordinador. No cal que engeguis el live per passar-lo pots executar-lo directament del disc dur. 

Crec que t'has angoixat una mica per tonteries i no n'hi ha per tant. Evidentment seria molt més senzill si els fabricants d'ordinadors i dispositius co&#320;laboressin oferint bons ordinadors amb bones distribucions de linux preinstallades i ben configurades on l'usuari novell no hagués de patir per les eleccions més elementals (com el teu cas quan vas provar el sistema de 64 bits abans)

Malgrat tot el mon del windows és un infern entre virus spywares, has tingut mai problemes installant un controlador (si et passa ho portes clar i recorda que el windows ara no el pots reinsta&#320;lar)... o un dispositiu que ja no existeix... o senzillament trucar a microsoft?... a veure si algú et pot ajudar en un problema... o amb la darrera actualització ha deixat de funcionar algun programa, dispositiu o joc que tenies?

Crec que el canvi al programari lliure és immens, més que qualsevol actualització del windows i cal pendre-s'ho en calma. Els avantatges que aconsegueixes al final no tenen preu.

---

