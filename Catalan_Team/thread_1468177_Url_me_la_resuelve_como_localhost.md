---
title: "Url me la resuelve como localhost"
date: 2010-05-01
forum: Catalan Team
---

### Post by obi1wan on 2010-05-01
Buenas,

tengo el problema que cuando intento acceder a una web, por ejemplo http:/google.es me la resuelve como si fuese en mi propia máquina.

He mirado en el archivo de hosts y logicamente no esta definido  y menos como 127.0.0.1...

Ya no se que hacer, a ver si alguien puede decirme por donde mirar.

Gracias.

---

### Post by wgarcia on 2010-05-02
Hauries de donar més detalls, com ara tens connexió a Internet? De quin tipus?

---

### Post by obi1wan on 2010-05-02
Tinc una conexión wifi, pero estigui on estigui em pasa el mateix. He porvat em posarme en windows y no em dona aquest error, aixi que descarto un problema del router.

---

### Post by wgarcia on 2010-05-02
Dóna la instrucció:

ifconfig

des d'una terminal de comandes, i enganxa aquí el resultat.

---

### Post by obi1wan on 2010-05-02
eth0      Link encap:Ethernet  direcciónHW e0:cb:4e:4a:dc:0c  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:33 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  direcciónHW 70:1a:04:c1:94:b8  
          Direc. inet:192.168.1.144  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::721a:4ff:fec1:94b8/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3246 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3225 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3419562 (3.4 MB)  TX bytes:424833 (424.8 KB)
          Interrupción:17 Memoria:f83f8000-f83f8100

---

### Post by wgarcia on 2010-05-02
Sembla que tens alguna cosa configurada diferent, perquè habitualment el "wifi" queda assigant a "eth1" i no a "wlan0" com es veu en el teu resultat de ifconfig. 

Ara seria útil que tornessis a la terminal, i enganxessis els resultats que et donen les següents comandes:

cat /etc/resolv.conf

cat /etc/udev/rules.d/70-persistent-net.rules

---

### Post by akyra on 2010-05-03
Hola,

A mi també sempre m'ha sortit el wifi com a WLAN0.

També, has mirat si a la conexió wifi no tens posada la porta d'enllaç o el servidor de DNS automàtic? Això podria donar el problema.

---

### Post by Rubunter on 2010-05-03
> **akyra said:**
> Hola,

A mi també sempre m'ha sortit el wifi com a WLAN0.

De fet és lo normal. El eth és per ethernet. A mi, no obstant, amb una targeta de xarxa broadcom, la wifi me la detecta com a eth1.

---

### Post by papapep on 2010-05-03
No oblideu mirar l'encaminament de paquets:

```
route -n
```

---

