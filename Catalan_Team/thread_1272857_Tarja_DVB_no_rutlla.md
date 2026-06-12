---
title: "Tarja DVB no rutlla"
date: 2009-09-22
forum: Catalan Team
---

### Post by HermesM on 2009-09-22
Abans veia la tele perfectament però ara em diu device no connected.
Cercant amb Google he trobat que per veure la tarja fes
 **dmesg | grep DVB**
i el resultat és aquest:

[B][   12.612730] saa7134[0]: subsystem: 1461:2c05, board: AverTV DVB-T 777 [card=85,autodetected]
[   12.612928] input: saa7134 IR (AverTV DVB-T 777) as /devices/pci0000:00/0000:00:09.0/0000:05:06.0/input/input7
[   12.941650] DVB: registering new adapter (saa7134[0])
[   12.941653] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...[/B]
¿S'haurà espatllat la tarja o hi ha una solució?

---

