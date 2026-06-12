---
title: "Wireless: Recomendación de software"
date: 2007-03-14
forum: Argentina Team
---

### Post by marianom on 2007-03-14
Ayer recibí mi primera laptop (una toshiba satellite cuyas teclas están transparentes del uso) y segundos después el xp  procedió a morir. Para mi sorpresa la placa externa de wireless que trae funcionó sin problema y sin configuración adicional desde el primer momento (... y después dicen que linux es complicado). 
El tema es que para poder acceder a cualquier hot spot tengo que saber de antemano el SSID. ¿Alguien podría sugerir -con conocimiento de causa-algún soft que identifique las redes presentes al alcance y me permita seleccionarlas?

Agradecido as usual.

---

### Post by Benji86 on 2007-03-15
Si te sirve con el siguiente comando haces un scaneo de redes:
**iwlist wlan0 scan**

Sino, el que yo uso es Wireless Assistant que viene con Kubuntu (no idea en Ubuntu) y anda muy bien. Por ultimo, averigua por NetworkManager q es el otro muy usado (hasta hay applets para GNOME de este)

---

### Post by beuno on 2007-03-15
network-manager (en fiesty anda mejor) te muestra todas las redes disponibles, y hasta maneja encriptacion y claves wep automaticamente.

---

### Post by jpmorelli on 2007-03-16
Tambien podes bajar wi-fi radar, escanea redes y podés dejar seteadas las configuraciones de cada una.

---

