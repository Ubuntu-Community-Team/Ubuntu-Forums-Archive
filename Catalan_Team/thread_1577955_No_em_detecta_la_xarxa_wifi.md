---
title: "No em detecta la xarxa wifi"
date: 2010-09-19
forum: Catalan Team
---

### Post by MaverickVZ on 2010-09-19
Hola a tothom. Sóc molt nou pel que fa a la utilització d'Ubuntu i m'he descarregat l'última versió per a netbook.
M'he trobat amb el problema de que no puc connectar-me a la xarxa wifi de casa, he trobat el servidor, li he posat la clau però tot i això segueixo sense tenir connexió. L'indicador de la wifi no para de fer pampallugues.
Tinc una targeta wifi Marca Realtek Device 8172.
He llegit en altres llocs sobre la compatibilitat de les targetes wifi amb Ubuntu i que cal utilitzar el programa ndiswrapper per instal·lar els drivers de windows... però aquí ja m'he perdut.
Algu podria ajudar-me?
Moltíssimes gràcies

---

### Post by kukat on 2010-09-19
hola!!!
Ho tinc apuntat de quan ho vaig fer una vegada. A veure si és així:

1. Primer de tot insta&#320;les el ndiswrapper mitjançant aquest comandament a la consola:

***sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9***

2. Agafes el CD on estan els drivers de Windows de la teua targeta WIFI, i busques la carpeta amb els drivers al CD. És un arxiu acabat en "*.inf". 

3. Copies el driver a l'ordinador, i a la consola, situat en la carpeta on es troba el driver, fas:

***sudo ndiswrapper -i "nom_driver.inf"***

4. Comproves si s'ha insta&#320;lat:

***sudo ndiswrapper -l***

5. Carreges el mòdul de la targeta:

[B][I]sudo depmod -a
sudo modprobe ndiswrapper[/I][/B]

6. Si tot funciona bé, quan està activat el carregues així:

***sudo ndiswrapper -n***


Val. És una mica complicat tot açó....Per tal de que es carregue a l'inici cada vegada que inicies l'ordinador, tens que editar el fitxer "modules". S'edita a la terminal amb:

***sudo gedit /etc/modules***

I al final afegeixes:
**ndiswrapper**
I guardes el fitxer.

Ara falta escanejar les xarxes i connectarte!

insta&#320;lem les Wireless tools:

***sudo aptitude install wireless-tools***

i analitzem les xarxes així:

***iwlist wlan0 scan***

Jo al final, per a connectar-me, i després de molts intents ho vaig solucionar així:

**iwconfig wlan0 essid "nom_de_la_connexió" channel NUM_CANAL rate auto**


I aixó es tot (quasi res....). SI hi ha una solució més fàcil m'agradaria saber-la a mi també!

Salut!

---

### Post by kukat on 2010-09-19
Doncs mira per on:

[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Dos enllaços on expliquen altres mètodes. JO amb una targeta, mitjançant el ndiswrapper ho vaig fer com he dit abans, però igual amb la teva és més fàcil!

Salut!

---

### Post by MaverickVZ on 2010-09-21
Moltes gràcies!
Ja ho tinc solucionat, diria, jeje.

---

### Post by wgarcia on 2010-09-21
Seria útil que descriguessis com ho has solucionat, i marquessis "Solved" a "Thread tools", per si algú ho necessita en el futur.

---

