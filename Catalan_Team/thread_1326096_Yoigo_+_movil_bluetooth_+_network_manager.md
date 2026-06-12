---
title: "Yoigo + movil bluetooth + network manager"
date: 2009-11-14
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-11-14
Hola a tothom,

fa uns dies he canviat de proveïdor de movil, passant de vodafone a yoigo, i de telefon, ara tinc un Nokia 5800.

Mai m'havia interessat massa això de poder fer anar el movil com a modem per a internet, però donat que la companyia nova té un cost assumible, doncs m'agradaria poder configurar-ho tot per a que hem vagi, algun dia em pot ser útil.

Us explico com ho faig, que va i que no va:

Faig servir el blueman com a gestor de bluetooth, i el connecto com a DialUp networking. Llavors el NM em detecta el modem i m'insta a configurar-lo, selecciono yoigo, poso el numero a marcar i quan intento connectar, em desconnecta a l'instant. M'imagino que no arriba ni a connectar.

Buscant per la web, he vist un [fil en un blog]("http://blog.tenak.net/go/142/") on explica com fer servir el wvdial, així que connecto el telefon fent servir el Blueman i amb el wvdial entra perfecte i puc navegar. La configuració del wvdial es aquesta:

```

$ cat /etc/wvdial.conf
[Dialer Yoigo]
Modem = /dev/rfcomm0
Phone = *99***1#
Username = ''
Password = ''
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"

```

A algú li ha passat alguna cosa similar? M'agradaria poder fer servir el network manager a poder ser..

Per cert, utilitzant el wvdial i canviant a /dev/ttyACM0, també em funciona connectat per cable. NM tampoc va!

Merci!

---

### Post by quitus on 2009-11-15
Aquest telefon funciona perfectament com a mòdem des de la 9.04 sense haver de remenar la configuració, tots aquests fils que expliquen com conectar-se solen ser molt antics o referir-se a altres distribucions. 
Això que dius de "posar el numero a marcar" m'estranya molt, normalment amb seleccionar el proveïdor de la xarxa (yoigo) i el país (espanya) ja n'hi ha prou.  
Has provat des de un livecd?
Potser es un problema de la xarxa, ja que necessites una bona connexió 3G
salut

---

### Post by PatrickVogeli on 2009-11-15
si si, es el primer que vaig fer... provar a no tocar res. A més, la configuració del telefon no l'he tocada, només la de les dades de connexió, que semblen ser erronies. A l'instant de posar connectar, em surt directament "Xarxa GSM desconnectada" i, com dic, amb el wvdial funciona perfectament, sempre.

salut

---

