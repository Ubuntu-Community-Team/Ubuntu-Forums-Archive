---
title: "L'únic wifi que no detecta, el meu"
date: 2014-08-16
forum: Catalan Team
---

### Post by simfomet on 2014-08-16
Hola, acabo d'instal·lar en un netbook lubuntu 14.04.1 LTS i tot va bé però hem trobo que tinc dos routers a casa que utilitzo segons on he de treballar o la cobertura wifi que hem donen, Comtrend HG536+ i comtrend AR5387un. Evidentment tinc clar que no poden estar en marxa els dos alhora. No són res de l'altre món però vaig tirant. El cas és que quan vull connectar el netbook via wifi hem detecta perfectament el 536 però ni olora el wifi de l'altre. No el veu encara que estiguis al costat.

Com és possible que no vegi la xarxa wifi??? Me'n detecta un munt de veïns i demés, no sembla res de controladors...

---

### Post by wgarcia on 2014-08-16
Pots detectar el wifi amb algun altre ordinador o sistema operatiu?

---

### Post by simfomet on 2014-08-22
> **wgarcia said:**
> Pots detectar el wifi amb algun altre ordinador o sistema operatiu?

I tant, en aquest mateix netbook on he instal·lat lubuntu 14.04.1 abans hi tenia un vell windows xp que connectava sense problema. Tinc un portàtil amb windows 7 que es connecta sense problema tant al wifi del AR com del 536HG+

---

### Post by wgarcia on 2014-08-28
Prova, si pots, de canviar el canal que usa l'antena wifi. Això normalment es fa entrant a la configuració del router, si no tens instruccions per al teu model, normalment es fa entrant al navegador d'Internat una adreça tipus 

[http://192.168.1.1](http://192.168.1.1)

o cosa semblant, a més demana un usuari i clau, que normalment és admin/admin.

A la configuració hi hauria d'haver-hi l'opció de canviar de canal, a vegades el canal que fa servir el router té massa senyals. 

També pots provar de canviar el tipus d'autentificació, si es WPA/WPA2 posar sols WPA2 (no convé posar WEP perquè és molt fàcil de hackejar). 

No se m'acuden de moment altres coses a fer.

---

### Post by jscurial on 2014-11-30
Bé no sé si el teu problema és el mateix que he tingut jo, de fet a casa el notebook no hi havia manera i en canvi a algun bar m'hi havia enganxat perfectament. Sabia que alguna cosa i havia amb el driver de la wifi (paquet bcmwl-kernel-source que és l'usat en el meu notebook) però seguia les instruccions de diferents webs i res. Finalment ho he solucionat executant ubuntu des d'una USB i he vist que era un problema de configuració en el programari de controlador propietari. Havia de seleccionar "no utilitzar dispositiu".

Ruta:
Configuració de sistema-programari i actualitzacions-controlador addicionals.

t'adjunto captura.

sort

---

