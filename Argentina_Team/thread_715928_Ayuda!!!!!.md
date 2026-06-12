---
title: "Ayuda!!!!!"
date: 2008-03-05
forum: Argentina Team
---

### Post by diegoff on 2008-03-05
HOla soy nuevo en el foro y en linux les cueno tengo ubuntu 7.10 i368 y el problema q tengo es q nose como hacerpara conectarme a internet encontre guias pero no para mi kernel q era algo asi como 22.14 no me acuerdo bien pero teia esos numeros asi q nesecito por favor una guia pra mi kernel mi servido de internet es arnet gracias

---

### Post by pol666 on 2008-03-05
datos, datos, datos..............

ADLS o CABLE MODEM?

MODEM ETHERNET o USB?


Si tenes adsl y modem ethernet
abris una terminal y pones

pppoeconf 


lllenas los datos, y despues todo SI
luego, si no inicio internet pones...

sudo pon dsl-provider

y para desconectarte sudo poff dsl-provider

Fijate que la configuracion de la placa de red NO este en modo Roamming, y que este habilitada para DHCP capas que tenes que poner los DNS o capas que no hace falta...

Bueno si tenes USB decinos el modelo del modem

---

