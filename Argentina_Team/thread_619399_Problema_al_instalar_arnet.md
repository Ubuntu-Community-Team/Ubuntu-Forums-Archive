---
title: "Problema al instalar arnet"
date: 2007-11-21
forum: Argentina Team
---

### Post by Pabliich on 2007-11-21
wenass gente.. tube un problemita quise instalar arnet en mi pc pero no puedo segui este tuto  [http://www.ubuntu-es.org/index.php?q=node/45097](http://www.ubuntu-es.org/index.php?q=node/45097) y en la parte que dice  $ sudo br2684ctl -c 0 -b -a 0.33

NOTA: los parámetros 0 y 33 corresponden al VPI y el VCI de mi ISP, ustedes deberán adaptarlo al suyo.
Si todo está bien, les saldrá esto:
RFC1483/2684 bridge: Interface "nas0" created sucessfully
RFC1483/2684 bridge: Communicating over ATM 0.0.33, encapsulation: LLC
RFC1483/2684 bridge: Interface configured  


ami me da error creo qe es por el "  los parámetros 0 y 33 corresponden al VPI y el VCI de mi ISP, ustedes deberán adaptarlo al suyo" pero nose como se adapta al mio... ayuda pliss!!!

---

### Post by faktorqm on 2007-11-21
Arnet Highway (Argentina): Protocolo PPP sobre Ethernet. VPI = 0 y VCI = 33.
Ciudad Internet (Argentina): Protocolo PPP sobre Ethernet. VPI = 0 y VCI = 33.
Ciudad Internet (zona de Wilde, Avellaneda, Argentina): Protocolo PPP sobre Ethernet. VPI = 
8 y VCI = 35.

espero que te sirva. salu2!

---

