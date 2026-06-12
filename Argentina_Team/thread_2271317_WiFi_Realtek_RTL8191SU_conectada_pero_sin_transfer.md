---
title: "WiFi Realtek RTL8191SU: conectada pero sin transferencia de datos"
date: 2015-03-29
forum: Argentina Team
---

### Post by Einfachlacm on 2015-03-29
Hola,

Escribo porque tengo la all-in-one Acer Aspire Z5751 con la placa WiFi integrada Realtek RTL8191SU. Puedo conectarme sin problemas a la conexion WiFi pero al cabo de unos 5 minutos de funcionar correctamente, ya no hay mas transferencia de datos, aunque la conexion sigue figurando conectada como si todo estuviera bien. Este problema lo tengo con todas las distribuciones posteriores a la 12.04 y derivados (incluidas 14.04.2, la 12.04.5 -actualizada-). 

Pienso que se trata de un problema de driver, que funcionaba correctamente en la 12.04 y en las posteriores fue cambiado.  Lei varios post en internet, ya que varias otras personas tuvieron el mismo problema, pero no logro resolverlo con esas soluciones. Incluso baje del sitio de Realtek el driver para linux, y lo instalé con el install.sh que trae, pero aun asi sigue sin funcionar. No se si ademas tendria que haber bloqueado el driver anterior, pero de ser asi, como se hace?

Aqui los resultados :

lsusb
Carte WIFI = Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

lshw
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 2
       information bus: usb@2:1.6
       nom logique: wlan0
       numéro de série: 1c:65:9d:6e:97:7d
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.10 multicast=yes wireless=IEEE 802.11bgn

Muchas gracias por su ayuda.

Saludos!

---

