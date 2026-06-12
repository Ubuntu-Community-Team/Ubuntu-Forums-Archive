---
title: "impressora"
date: 2015-03-29
forum: Catalan Team
---

### Post by josep-maria on 2015-03-29
Tinc l'ubuntu 10.04 i el gnome 2.30.2, a un PC Hewlett Packard Compaq.
D'ençà que hi vaig ficar l'ubuntu, no ha funcionat la impressora ni el scanner.
He canviat la impressora per una altra, però tampoc no funciona.
He mirat a: paràmetres del sistema > impressora, i puc veure el model de la impressora, i sembla que està tot bé.
No sé on més mirar.

---

### Post by wgarcia on 2015-03-29
No has dit quin model d'impressora tens. A més, la versió d'Ubuntu que tens és força antiga, l'hauries d'actualitzar almenys a la 12.04, em sembla que aquesta versió deixa de tenir suport a l'abril d'enguany.

Si l'ordinador és massa antic per donar suport a les versions més noves de l'Ubuntu, sempre pots provar si amb Lubuntu, que està pensat per a ordinadors més antics o amb menys prestacions, et pot anar bé.

---

### Post by josep-maria on 2015-03-29
He provat amb dues impressores: Hewlett Packard diskjet 1050, i Epson stylus SX100.

---

### Post by wgarcia on 2015-03-30
Tampoc has dit com connectes la impressora, tot i que suposo que serà per USB, i si el sistema l'arriba a veure o si et dóna algun missatge d'error.

---

### Post by josep-maria on 2015-03-30
Les impressores estan connectades per USB. Ja he provat a uns quants punts de connexió, sense cap resultat.
Si miro a sistema>administració>impressió, veig els models de les dues impressores, i una està marcada com a habilitada.
Si, per exemple, vull escanejar, em diu: "Ha fallat l'escaneig. No hi ha cap escaner disponible. Si us plau, connecteu-ne un".

---

### Post by josep-maria on 2015-03-31
Si canvio l'ubuntu a la versió 12.04, seguiré tenint el mateix escriptori gnome?

---

### Post by wgarcia on 2015-03-31
Suposo que quan dius "escriptori gnome" et refereixes a la versió Gnome 2, oi? És a dir la versió antiga abans que els de Gnome passessin al Gnome 3 (també dita Gnome Shell).  Doncs no, la versió 12.04 ja corre amb les noves llibreries GTK. Ara bé, em sembla que hi ha una versió que es diu Gnome Fallback que simular aquesta versió anterior del Gnome. Si anem a versions més recents, hi ha una versió d'Ubuntu que es diu Ubuntu Mate que port l'escriptori "Mate" que és un desenvolupament amb la versió recent de les llibreries GTK i l'aparença del Gnome antic, però sols està disponible a partir de la versió 14.10, i com a sabor oficial de l'Ubuntu estarà disponible a partir de la 15.04. 

De totes maneres per configurar les impressores no crec que sigui necessari actualitzar la 10.04, el que sí serà necessari serà a partir de finals d'abril perquè aquesta versió deixarà de tenir suport (hauran passat 5 anys des que va llençar-se a l'abril de 2010).

---

### Post by josep-maria on 2015-03-31
I com es fa per configurar les impressores?

---

### Post by wgarcia on 2015-04-01
Per a les impressores Hewlett Packard totes les distribucions de Linux porten un paquet de programari que es diu "hplip" que en principi hauria de permetre una configuració fàcil. Actualment tinc 3 impressores Hewlett Packard a sistemes diferents (i versions d'Ubuntu diferents, tot i que més recents que la teva) i almenys jo no tinc cap problema amb cap. Normalment endolles la impressora a USB, obres l'aplicació "impressores", cliques "Afegir impressora", i la impressora endollada es veu a la llista de l'esquerra. La resta és "clicar i acceptar", a part d'entrar-li un nom a la impressora pràcticament tota la resta és automàtic. 

D'impressora EPSON fa temps que no en tinc i hauria de mirar com es configura, tot i que fa uns anys quan en tenia tinc el record que no em va donar massa feina per configurar.

Mira el següent: endolla i desendolla la impressora. Entra a una terminal l'ordre "dmesg". Mira les últimes línies del carro que surt, a veure si veus alguna cosa relacionada amb la impressora (aquesta ordre "dmest" et mostra els missatges que va produint el sistema des que vas iniciar-lo, i va afegint a les últimes línies tots els missatges que es van produint.)

Suposo que el port USB on estàs connectant les impressores funciona bé amb altres dispositius tipus llapis de memòria i semblants, oi?

---

### Post by josep-maria on 2015-04-01
He engegat la impressora, i l'he desendollat dels 220V. He fet mseg, i les darreres línies de la resposta són:

[ 7806.536891] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 7806.537145] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 7816.752023] eth0: no IPv6 routers present
[ 9354.228044] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 9354.395161] usb 3-2: configuration #1 chosen from 1 choice
[ 9354.447182] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0841
[ 9354.447353] usbcore: registered new interface driver usblp
[ 9356.138043] usb 3-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 9364.648051] usb 3-2: USB disconnect, address 2
[ 9364.648309] usblp0: removed

Més amunt n'hi han més, però no sé si tenen res a veure amb la impressió.

Si faig: sistema>administració>impressió, veig dues icones (una de cada model d'impressora), i una d'elles està marcada com a predeterminada.
He provat les dues impressores a un altre pc, i funcionen bé.
També he canviat el port usb uns quants cops, sense cap resultat. Si fico una memòria flash al mateix port, funciona bé.

---

### Post by wgarcia on 2015-04-01
Suposo que amb la impressora que has generat aquestes línies és la HP, oi? En tot cas, el que pots fer és anar a sistema>administració>impressió, desendollar la impressora, esborrar la impressora (clic amb el botó dret a la finestra d'impressió i "suprimir"), endollar la impressora, clicar sobre "Afegeix", i a la barra esquerra del diàleg que s'obre t'hauria de sortir la impressora que has endollat a l'USB. L'escull, i continues l'addició de la impressora, són dos o tres diàlegs força intuïtius. A veure si tornant-la a instal·lar s'arregla.

Potser l'únic pas complicat és quan et pregunta el model, fixa't quin és i a veure si et surt a la llista de models que et proposa.

---

### Post by josep-maria on 2015-04-01
Ara tinc conectada la Epson.
He fet tot això que dius de tornar-la a insta&#320;lar, però tampoc no funciona. Ja ho havia fet abans d'escriure al forum. He posat bé el model. 
Quan em pregunta si vull imprimir una pàgina de prova, li he dit que sí, però no fa res més.

---

### Post by wgarcia on 2015-04-02
A la cua d'impressió, queda algun missatge de "treball retingut" o alguna cosa així?

---

### Post by josep-maria on 2015-04-03
No. A la cua d'impressió no hi ha mai res.
Sí que surt una finestreta que diu "la pàgina de prova s'ha enviat com a tasca 66".

---

### Post by wgarcia on 2015-04-07
Potser el teu paquest hplip és una mica antic. Pots fer des d'una terminal:

```
dpkg -l hplip
```

i enganxar el resultat?

---

### Post by josep-maria on 2015-04-08
Diu això:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nom            Versió        Descripció
+++-==============-==============-============================================
ii  hplip          3.10.2-2ubuntu HP Linux Printing and Imaging System (HPLIP)

---

### Post by wgarcia on 2015-04-09
Si, és una mica antiga, l'actual versió de hplip és 3.15 . Potser sigui una altra cosa, però també és possible que l'actualització de hplip permeti configurar almenys la impressora HP. L'Epson funciona amb altres controladors. Per tant crec que hi hauria dues opcions, 1) la millor seria actualitzar el sistema almenys fins a la versió 12.04, si realment vols mantenir-te amb el "Gnome clàssic" s'hauria de mirar quin entorn d'escriptori et permet mantenir aquest tipus d'interfície, crec que seria la millor opció perquè com et deia la versió d'Ubuntu que tens, la 10.04, deixa de tenir suport, i per tant actualitzacions de seguretat i d'altres, a partir de finals d'aquest mes (abril), 2) una opció una mica pitjor en el meu entendre és intentar actualitzar la versió d'hplip, baixant-la directament del lloc de descàrregues d'aquest programa, és una opció que no sé si funcionarà 100% segur perquè potser les versions més noves de hplip requereixen llibreries més actualitzades que les que porta Ubuntu 10.04.

---

### Post by josep-maria on 2015-04-14
He canviat a la versió 14.04, tal com dèieu, i ja funciona la impressora. La pega és que he perdut l'escriptori gnome, que anava la mar de bé. Gràcies.

---

