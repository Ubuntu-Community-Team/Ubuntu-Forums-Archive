---
title: "Cómo veo la Mac Address de la placa Wifi en Ubuntu 8.04?"
date: 2008-04-26
forum: Argentina Team
---

### Post by zeusolimpo on 2008-04-26
En Ubuntu 8.04 no se como ver el hardware de mi nueva laptop!
Tengo configurado el acceso a la red wireless con macaddress y no puedo conectarme!
Otra laptop tambien corriendo Ubuntu 8.04 que ya estaba configurada en el router anda lo mas bien.
Si alguien sabe como ver la mac addresss de las placas wifi (es una Broadcom 4311 de una laptop Lenovo) por favor que me lo diga.
Gracias y saludos

---

### Post by odiseo77 on 2008-04-26
Al ejecutar iwconfig, ¿no te aparece la dirección MAC de la tarjeta de red? Si la tarjeta es reconocida, debería aparecer. Por ejemplo en mi caso iwconfig me devuelve esto:

```
ra0       Link encap:Ethernet  direcciónHW **00:0e:2e:50:a9:25**  
          inet dirección:192.168.1.1  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::20e:2eff:fe50:a925/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:105856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103439 errors:262 dropped:262 overruns:0 carrier:0
          colisiones:11560 txqueuelen:1000 
          RX bytes:131715632 (125.6 MB)  TX bytes:13723648 (13.0 MB)
          Interrupción:21 Dirección base: 0xc000
```

Lo que aparece en letras negras, después de "direcciónHW" es la dirección mac de la tarjeta de red inalámbrica.

Saludos.

---

### Post by zeusolimpo on 2008-04-26
En la que está conectada por wifi no me sale eso. Voy a probar con la otra, mas tarde y comento como me fué.

---

### Post by odiseo77 on 2008-04-26
Disculpa, me equivoqué :redface: el comando apropiado para ver la dirección mac de la tarjeta de red es ***ifconfig*** (es que confundí iwconfig e ifconfig). Prueba con ***ifconfig*** o ***ifconfig -a***

---

### Post by zeusolimpo on 2008-04-26
No hay caso. en la wlan0 no me sale nada, porque no está conectada.
Yo lo que quiero ver es el hardware!

---

### Post by Hei Ku on 2008-04-27
Fijate en el dmesg que seguro aparece la MAC address en el momento que monta los drivers.

probablemente con esto te aparezca:

dmesg | grep wlan

---

### Post by fmsismo on 2008-04-27
Otra opción es desde la consola escribir

lspci |grep wlan

Y lo que te devuelva es la línea con la información de tu placa de red inalámbrica.

Saludos

---

### Post by odiseo77 on 2008-04-27
@zeusolimpo: No entiendo, ***ifconfig -a*** debería decirte cuál es la dirección MAC de tu tarjeta de red en caso de que ésta sea detectada por tu sistema. (A mi me da la dirección MAC de la tarjeta ethernet y la de la inalámbrica). ¿Probaste lo que te dije de ejecutar ***ifconfig -a***?

---

### Post by zeusolimpo on 2008-04-27
Todo funcionando! :)
Gracias a todos, especialmente a odiseo!

saludos

---

