---
title: "[ayuda] - Configuracion Wi-Fi"
date: 2007-11-14
forum: Argentina Team
---

### Post by niko_3100 on 2007-11-14
Bueno getne le digo cual es mi problema ahora. En el laburo se trabaja con ip estatica, hay wifi entonces yo baro el network manager le doy a configuracion manual y en el iconito del wifi configuro todo para ip estatica con la ip, mascara, dns todito todito. Hasta ahi joya pero tengo un problema la contraseña del wifi esta encriptada con WPA-PSK y cuando yo quiero darle a eso en Tipo de Contraseña me aparecen solo dos WEP (hexadecimal) y WEP (asci) probe las dos pero no se me conecta, necesito que me de la opcion para WPA por lo menos, probe el wifi radar pero no anda. Aclaro que los drivers de mi broadcom los instale con wine y el sdriver de windows xp. Alguien me daria alguna ayuda?? Muchas gracias.

---

### Post by margori on 2007-11-14
Se que las placas broadcom no tienen buen soporte en linux (yo tuve un problema parecido)

Que no te salga la posibilidad de usar contraseña WPA puede ser que el driver no lo soporte.

Lo que te recomiendo es utilizar ndiswrapper en vez de wine para cargar el controlador de Windows em Ubuntu. Yo lo tengo asi y funciona muy bien.

---

### Post by niko_3100 on 2007-11-14
Sip use ndiswrapper :P no lo dije, el tema es que wpa me soporta menos cuando quiero asignar por ip statica me sale solo opciones wep.

---

