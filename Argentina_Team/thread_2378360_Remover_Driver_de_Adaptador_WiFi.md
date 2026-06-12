---
title: "Remover Driver de Adaptador WiFi"
date: 2017-11-22
forum: Argentina Team
---

### Post by Vero1 on 2017-11-22
Buenos días,

Uso Ubuntu 16.04- 64 bits.
Al cambiar de Mother el equipo dejó de reconocer mi conexión inalámbrica, que es del Módem. No tengo tarjeta WiFi.  Cuando abro nm-applet, solamente aparece la red cableada.
Como soy Administradora de una Fan-Page y trabajo con fotos y videos, tenía problemas de cuelgues muy seguido así que opté por comprar un Adaptador de Wi-Fi. Se trata de un TP-Link- TL-WN722N, cuyo Driver hubo que descargarlo de TP-Link. Lo descargué, lo descomprimí pero no sabía como instalarlo porque no trae ninguna indicación.
Opté por pedir ayuda. Me enviaron estos comandos :

sudo apt-get install git dkms
git clone [https://github.com/lwfinger/rtl8188eu.git](https://github.com/lwfinger/rtl8188eu.git)
sudo dkms add ./rtl8188eu
sudo dkms install 8188eu/1.0
sudo modprobe 8188eu

Lo instalé con los comandos pero nunca logré que conectara. Se me ocurrió mirar en la Caja de qué versión se trataba y dice V2.

La persona que me mandó los comandos le puso 1.0, que sería V1,  como puede verse, razón por la que pienso que no funciona y quiero eliminar este driver para poner la versión que corresponde y que ya tengo descargado.

Les agradeceré indicarme la forma de eliminar los comandos listados.

Saludos

---

