---
title: "Problema con 2 placa WiFi (interna/USB) ubuntu 14.04"
date: 2015-11-17
forum: Argentina Team
---

### Post by ezequiel5 on 2015-11-17
Hola,

Tengo una Notebook Dell Inspiron 14 que trae la Red Wifi Dell Wireless 1397 WLAN Mini-Card, le instale ubuntu 14.04, y le conecte via USB una placa de Red Wifi AirLive WL1600USB (RTL8187L) para tener mayor alcance con la señal wireless.

El sistema reconoce ambas placas y si pongo conectar en ambas redes conecta, pero cuando quiero navegar no puedo con la placa USB.

Probe de poner desconectar en la red Wifi interna para que solo navegue por la placa USB pero no hay caso.  Que puede estar pasando?

Desde ya muchas gracias. 

Saludos,

Ezequiel

---

### Post by ezequiel5 on 2015-11-18
Bueno gente, lo resolví con esto:


[LIST=1]
[*]sudo gedit /etc/rc.local
[*]Añade la siguiente linea a rc.local antes de la linea exit 0
    iwconfig wlan0 rate 5.5M fixed
[*]En mi caso como son 2 placas es wlan1.
[*]Reinicia el ordenador
[/LIST]

---

