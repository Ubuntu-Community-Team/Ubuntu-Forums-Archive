---
title: "wireless evo-w541usb"
date: 2010-03-19
forum: Catalan Team
---

### Post by pelai21 on 2010-03-19
Hola, a veure si algú em pot ajudar. Tinc un ordinador vell i amb poques prestacions on hi he instal·lat l'Xubuntu 8.04.1. Per poder-me conectar a internet utilitzo un receptor de wireless evo-w541usb. Teòricament la distribució hauria de reconèixer l'aparell automàticamet (de fet, en un altre ordinador amb l'Ubuntu 9.10 no hi ha cap problema), però no acosegueixo configurar-lo de cap manera. He buscat per tot arreu, i al final recorro a vosaltres, a veure si em podeu ajudar. 



Quan teclejo lsusb, m'apareix el següent:


                           > **Bus 004 Device 003: ID 0ace:1215 ZyDAS WLA-54L WiFi**
 Bus 004 Device 001: ID 0000:0000   
 Bus 003 Device 001: ID 0000:0000   
 Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
 Bus 002 Device 001: ID 0000:0000   
 Bus 001 Device 001: ID 0000:0000   
I quan teclejo iwconfig, obtinc això:

                          > lo        no wireless extensions.
 

 eth0      no wireless extensions.
 

 eth1      IEEE 802.11b/g  ESSID:""  Nickname:"zd1211"
           Mode:Managed  Access Point: Invalid    
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Com podeu veure l'Xubuntu em reconeix l'aparell, però no puc veure les xarxes disponibles. Suposo que es tracta d'un problema de configuració, però jo reconec que sóc incapaç de resoldre'l. Porto una setmana trencant-me les banyes amb l'assumpte i em dono per vençut. A veure si algú és més hàbil que no jo.

---

### Post by quitus on 2010-03-20
Jo vaig utilitzar un d'aquests i no va ser fins la 8.10 (si no recordo malament) que no em va funcionar. Penso que hi havia un bug que feia que no funcionés amb la 8.04, sempre pots actualitzar el kernel si vols mantenir la versió 8.04 (no se si dic una bestiesa)


salut

---

### Post by pelai21 on 2010-03-20
No hi ha hagut sort. He seguit el teu consell i he instal·lat l'Ubuntu 8.10, però segueixo sense wireless. Amb una diferència. Ara, quan teclejo iwconfig, obtinc el següent resultat: 
  	 	 	 	 	> [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=1]wlan0     IEEE 802.11bg  ESSID:""  [/SIZE][/FONT][/COLOR] 
 [INDENT] [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Mode:Managed  Frequency:2.412 GHz  **Access Point: Not-Associated   **[/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Tx-Power=0 dBm   [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Retry min limit:7   RTS thr:off   Fragment thr=2352 B   [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Power Management:off[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Link Quality:0  Signal level:0  Noise level:0[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]         [FONT=Verdana, sans-serif][SIZE=1]Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/SIZE][/FONT][/COLOR]
[/INDENT]
A l'access point em surt "not-associated". Algú em podria explicar com podria associar el wlan0 a un determinat número mac? Jo no sabria com fer-ho des de la terminal. De totes maneres intentaré instal·lar les actualitzacions de l'intrepid, a veure si tinc sort.
  	 	 	 	 	[COLOR=#000000][/COLOR]

---

### Post by pelai21 on 2010-03-21
Arreglat. Després d'instal·lar l'xubuntu 8.10 vaig actualitzar el kernel fins la versió 2.6.27-15 i ja em reconeix l'aparell. Gràcies pel consell quitus, he après unes quantes coses!

---

