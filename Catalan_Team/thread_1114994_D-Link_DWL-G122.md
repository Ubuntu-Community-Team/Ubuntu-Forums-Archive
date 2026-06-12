---
title: "D-Link DWL-G122"
date: 2009-04-03
forum: Catalan Team
---

### Post by prostata on 2009-04-03
a un portatil marca NEC i sota Ubuntu, clar, ;-) l'he conectat aquest usb Wiffi i m'agafa les xarxes que troba, pero la del meu modem thomson, el que tin a la sobre taula, em demana una contrasenya. L'he possat la meva i d'latres per provar, pero no hi ha forma dins de casa de conectar-lo al cable-modem d'ONO, perque cap de les contrasenyas me les accepta...què puc fer...??

Gràcies

---

### Post by quitus on 2009-04-03
Sembla bastant clar que no "reconeix" la contrasenya. Pots provar de entrar en l'enrutador i canviar-la, millor encara, deixes la xarxa sense encriptar i un cop hagis comprovat que tot rutlla ja la podràs encriptar.


salut

---

### Post by torracastanyes on 2009-04-03
Mira't quin tipus d'encriptació té el router. Sembla que aquest adaptador només soporta WEP i WPA/PSK.
Si el router llegeix un codi diferent és normal que no reconegui la contrassenya i si és WPA/PSK, has de posar-hi la que et dóna el router (Sol estar escrita a sota).

---

### Post by PatrickVogeli on 2009-04-04
sembla que no poses la contrasenya correctament.. quina contrasenya li poses?? La teva d'usuari?

---

### Post by prostata on 2009-04-05
Si, li poso la meva contrasenya d'usuari, a sota del modem hi ha una cosa semblant que diu : MAC 011E3D4F007 però res de res, i hara a més, totes les xarxes que veia, fent busca xarxes ocultes, han desparegut, i només em sur una anomenada Applexxxxx

---

### Post by torracastanyes on 2009-04-05
La contrassenya d'usuari que dius es la de ubuntu?. No tens cap contrassenya de xarxa?.La wifi funcionava avans o és el primer cop que l'engegues?. El router l'has comfigurat tú o el va instalar algú altre?.
Hauríes d'entrar a la comfiguració del router i mirar com està.
La manera de fer-ho depèn de cada router i ho trobaràs al manual. Si no tens l'original a mà, pots trobar-lo a la web del fabricant.

---

### Post by PatrickVogeli on 2009-04-05
> **prostata said:**
> Si, li poso la meva contrasenya d'usuari, a sota del modem hi ha una cosa semblant que diu : MAC 011E3D4F007 però res de res, i hara a més, totes les xarxes que veia, fent busca xarxes ocultes, han desparegut, i només em sur una anomenada Applexxxxx
Ho tens mal entes. El teu wifi te una contrasenya, que no te res a veure amb la d'ubuntu... li has de posar aquesta. Si no la tens has d'entrar al router a traves de cable i posar-ne una de nova.

salut

---

### Post by prostata on 2009-04-06
Perdoneu la meva ignoràcia sobre temes de configuració wifi, adjunto una imatge que pot ser val que mil paraules. 

com podeu veure hi ha una contrasenya, que crec que te 26 dìgits i si mal no recordo la vaig posar jo mateix, pero es clar que no es veu i per tant no en tinc ni idea de quina és, puc canviar-la per una de nova??? Serìa aquesta la contrasenya que em demana l'adaptador quan vull entrar a la xarxa Thomson..?? Clar que entrar a la xarxa Thomson em pot anar bé a casa, però i a fora de casa...??Perquè s'han perdut la resta de xarxes "invisibles" que avans surtien..??...Perquè si conecta a la xarxa Apple Network a9ce47 i diu que estic conectat amb un 66% de senyal no puc navegar per internet ni fer servir el Thunderbird...???

---

### Post by torracastanyes on 2009-04-06
Efectivament, aquesta contrasenya es la que et cal per entrar a la xarxa. Es clar que es pot canviar, el que no sé és si facil o no.
Això ho hauríes de mirar al manual.

Sobre conectarte fora de casa, hauràs de buscar una xarxa oberta (que no demani contrasenya) o bé emprar xarxes conegudes amb contrasenyes conegudes.

El que trobis més o menys xarxes pot dependre de moltes coses, fins i tot del temps que faci, i aquesta xarxa que et conecta però no et deixa navegar pot ser que utilitzi un filtre MAC, vol dir que no demana contrasenya, pero només deixa conectar a màquines "autoritzades".

---

### Post by prostata on 2009-04-06
Ja l'he solucionat i ja puc conectar-me amb la xarxa Thomson de casa, la solució ha estat mes fàcil del que em pensava, però clar, havia d'arrivar, he fet el següent, per si algù altre es troba en el mateix problema:

des de la pàgina de configuració del modem-router-cable d'ONO.
Pestanya: Wireless

Les cuatre primeres caselles que surten= disable
la casella webencryption: pot sel-leccionar la de 128 bits o la de 64bits. Això voldra dir que en funció de la que agafis, s'ha d'introduir una clau de la mateixa llagariaperò he agafat l'opció final que diu: Passphrase, he introduït un mot i a continuació he clicat sobre: GENERATE WEB KEY i la casella currentnetwork key=1,.
Dins les caselles NETWORKKEY 1 a 4 hi han aparegut les claus generades anteriorment, i com que jo he seleccionat previament la casella currentnetwork key el valor=1, doncs a partir d'aquí la contrasenya que em surt a aquesta casella, es la que al conectarme amb l'adaptador d-link, a la xarxa Thomson i en demanarme la pasword, l'hi introdueixo aquesta i colorin colorado....

Vull aprofitar per agrair-vos els vostros esforços per tal d'ajudarme..

Gràcies

---

### Post by ffp on 2009-04-06
Ostres Prostata,
Tens l'Ubuntu en "castellano"
Sistema > Administració > Suport d'idioma
Afegir Catalan;Valencian, d'acord, enter !
I després posar "Idioma per defecte" Catalan;Valencian.

Sento afegir-ho en aquest fil, però es que no ho he pogut resistir.

---

### Post by prostata on 2009-04-06
Moltes gràcies per la observació ffp, de bon rotllo ;-) ;-)

---

### Post by Molsa on 2009-04-10
> **prostata said:**
> el mateix problema:

des de la pàgina de configuració del modem-router-cable d'ONO.
Pestanya: Wireless

Això no entenc que vols dir. I m'aniria bé, perque és exactament el mateix problema.

---

### Post by torracastanyes on 2009-04-10
I el mateix router també?

Vol dir que, generalment, els routers es configuren des d'una pàgina web. La pots veure a la captura que ha posat en prostata més amunt.
Només has d'obrir el navegador i escriure la IP del router.

---

### Post by Molsa on 2009-04-10
No és el mateix router, el meu es un scientific atlanta.

---

### Post by torracastanyes on 2009-04-10
Per poder-lo configurar, hauríes de mirar el manual per saber la IP, el codi d'usuari i la contrassenya per poder entrar a la pàgina, i també per saber con està organitzada i quines opcions té.
Aquestes pagines son pròpies de cada router i cadascuna es diferent.

Editat: Mira't si això et serveix:

[http://www.adslzone.net/webstar2320.html](http://www.adslzone.net/webstar2320.html)

---

### Post by SiscoGarcia on 2009-04-11
> **Molsa said:**
> No és el mateix router, el meu es un scientific atlanta.

Molsa, si no és el mateix router has d'iniciar un nou fil perquè potser la solució és una altra. Recorda de repassar les [instruccions de començament]("http://ubuntuforums.org/showthread.php?t=599965") ;)

---

