---
title: "problemes amb la connexió de bluetooth i ubuntu 14.04"
date: 2017-01-06
forum: Catalan Team
---

### Post by txotxi on 2017-01-06
Hola a totes, 
ja fa uns dies que no em puc connectar al bluetooth que tinc per tal d'escoltar música....fins fa una setmana no tenia problemes però ara em resulta impossible, no se si ha estat degut a una actualització o que....el fet és que l'ordinador em reconeix l'aparell, però no em deixa establir-hi connexió.
De fet quan entro a paràmetres del sistema-bluetooth, aquest em mostra l'aparell en qual em vull connectar, però no em deixa obrir el botó de connexió, tot i així em diu que si que estic aparellat.....no se que pot succeir.

---

### Post by wgarcia on 2017-01-07
Jo el primer que provaria seria eliminar el dispositiu i tornar-lo a aparellar. 

Si això no funciona, mira si l'ordre següent (des d'una terminal) mostra algun bloqueig al dispositiu del bluetooth:

```
rfkill list
```

---

### Post by txotxi on 2017-01-08
Hola Wgarcia, he provat d'eliminar el dispositiu i tornar-lo a emparellar i segueixo sense poder conectar-me... 

en la ordre de la consola em surt això:

[IMG]https://s24.postimg.org/rdpe7b7xx/terminal_rfkill.png[/IMG]

quan vaig a connectar-me a traves de parametres del sistema, el que succeeix és que l'aparell amb el qual em vull connectar m'apareix com a visible i aparellat però no em deixa fer click a la connexió:

[IMG]https://s27.postimg.org/606obbqgz/bluetooth.png[/IMG]


no entenc que succeeix

---

### Post by wgarcia on 2017-01-08
Sí, és estrany. Una possibilitat és intentar afegir el teu usuari al grup "bluetooth". Primer t'has d'assegurar que puguis gestionar els grups. Per això mira si tens instal·lat el gestor de grups: 

```
sudo apt-get install gnome-system-tools
```

Si està instal·lat, ara obre "Usuaris i grups" i clica sobre "Gestiona grups". Busca el grup "Bluetooth", i clica sobre "Propietats". Aquí et sortirà el teu usuari i si no està marcat, marca'l.

---

### Post by maximil13 on 2017-02-14
Hola a tothom.

Fa temps que el rendiment del dispositiu intern de bluetooth del meu ordinador (tinc un lenovo B580), és un malson. Es talla la connexió, connecta però no funciona. Les últimes dues setmanes, visitant fòrums, tutorials, tot. El mateix que a tu. Al meu cas, amb uns auriculars Pionner, bluetooth 4.0.

1- És un problema d'un mòdul de pulseaudio que no s'ha carregat.

Escriu a la consola,

```
cat /var/log/syslog | grep bluetoo*
```

i si et trobes alguna cosa semblant
```
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Not enough free handles to register service
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Not enough free handles to register service
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Sap driver initialization failed.
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: sap-server: Operation not permitted (1)
Feb 14 20:16:09 Lenovo-mx--B580 bluetoothd[1203]: Loading LTKs timed out for hci0
Feb 14 20:16:10 Lenovo-mx--B580 NetworkManager[1223]: [1487099770.2599] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Feb 14 20:38:58 Lenovo-mx--B580 bluetoothd[1203]: a2dp-sink profile connect failed for FC:58:FA:F9:3D:04: Protocol not available
Feb 14 20:39:20 Lenovo-mx--B580 bluetoothd[1203]: a2dp-sink profile connect failed for FC:58:FA:F9:3D:04: Protocol not available
```

Potser el mòdul discover de pulseaudio,

```
pactl load-module module-bluetooth-discover
```

Després d'activar-ho, prova de connectar.

Si et dóna un error, és que el mòdul està actiu. Llavors la segona opció.

2-Existeix un bug amb els protocols a2dp, el mòdul que gestiona pulseaudio per al so en connexions d'àudio, no canvia de HSP/HFP a2dp o a2pd no engega , a2dp que és la connexió d'audio de qualitat, l'altra és la connexió amb un mans lliures.

Un exemple de l'error als logs del sistema.
```
eb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Current Time Service could not be registered
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: gatt-time-server: Input/output error (5)
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Not enough free handles to register service
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Not enough free handles to register service
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: Sap driver initialization failed.
Feb 14 20:16:05 Lenovo-mx--B580 bluetoothd[1203]: sap-server: Operation not permitted (1)
Feb 14 20:16:09 Lenovo-mx--B580 bluetoothd[1203]: Loading LTKs timed out for hci0
Feb 14 20:16:10 Lenovo-mx--B580 NetworkManager[1223]: [1487099770.2599] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Feb 14 20:38:58 Lenovo-mx--B580 bluetoothd[1203]: a2dp-sink profile connect failed for FC:58:FA:F9:3D:04: Protocol not available


```

altra entrada amb l'error, quan vols canviar dels perfils d'àudio
```

Feb 14 21:50:13 Lenovo-mx--B580 bluetoothd[1203]: Endpoint registered: sender=:1.130 path=/MediaEndpoint/A2DPSource
Feb 14 21:50:13 Lenovo-mx--B580 bluetoothd[1203]: Endpoint registered: sender=:1.130 path=/MediaEndpoint/A2DPSink
Feb 14 21:51:14 Lenovo-mx--B580 bluetoothd[1203]: Unable to get Headset Voice gateway SDP record: Host is down
Feb 14 21:51:23 Lenovo-mx--B580 bluetoothd[1203]: /org/bluez/hci0/dev_FC_58_FA_F9_3D_04/fd0: fd(35) ready
```

Jo faig servir bluez, però l'error és el mateix.

La solució per això, és un rotllo.
Des de la configuració del so, canvia de a2dp a HSP/HFP, després tancas la connexió. Ho tornes a connectar i un altre cop, fas el canvi de HSP/HFP a a2dp.
Jo vaig fer-ho tot, tots el post, wikis, i fins i tot, el que diuen en aquesta entrada. El problema és que són dos problemes.
-El xip interno (broadcom). Cada vegada que demanava una pàgina web amb la wifi, el bluetooth fallava. Però amb una connexió amb cable, no.
L'única solució, un dongle bluetooth, de fet estic fent servir un de la marca trust, amb un xip broadcom i versió 2.0, i no tinc problemes. Ha millorat molt la qualitat del so i la connexió amb altres dispositius (mòbils, tauletes, etc). Cap problema **de soroll o talls.** El micròfon del pionner funciona, puc parlar per Skype.
-L'altre maca, la càrrega del mòdul discover-bluetooth i el modul a2sd a pulseaudio.

Salut i sort.

---

