---
title: "Nmap"
date: 2008-04-10
forum: Argentina Team
---

### Post by ramiro_md on 2008-04-10
Buenas ubunteros,mi problema es el siguiente, cuando le doy a escanear al nmap una ip me sale la siguiente leyenda :

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-04-10 21:39 ART
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.014 seconds

y al agregarle le parametro -P0 me sale esto:

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-04-10 21:49 ART
All 1697 scanned ports on XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX (190.xxx.xxx.xx) are filtered

Nmap finished: 1 IP address (1 host up) scanned in 356.622 seconds

hasta ahí todo bárbaro...pero yo sé que esta persona tiene programas p2p activados y corriendo...por qué no aparecen esos puertos abiertos ?
Desde ya muchas gracias.

---

### Post by Hei Ku on 2008-04-10
hacele un scan completo, de todos los puertos. lo mas comun es que los p2p hagan saltos de puerto para evitar los bloqueos de firewalls, proxys, etc.
lo otro es que es en modo leecher. en ese caso, efectivamente tiene todos los puertos cerrados.

---

### Post by ramiro_md on 2008-04-10
gracias por la data pero como hago el scan completo ?? así: "nmap ip" ?? porque de ese modo ya lo hice :(

---

### Post by Hei Ku on 2008-04-10
fijate con:

man nmap

---

### Post by ramiro_md on 2008-04-10
bueno gracias...veo lo que hago..

---

### Post by sergiom99 on 2008-04-10
hola, yo uso

```
$ nmap host.com -p 10-66500
```

donde el parametro -p es el rango de puertos. puede ser solo uno.

inclusive en XP y me funciona bien.

Espero te sirva.

---

### Post by ramiro_md on 2008-04-11
muchas gracias..voy a ver si sale, después te aviso si anduvo =)

---

### Post by ramiro_md on 2008-04-11
no anduvo :S me sale esto:

Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.000 seconds

---

### Post by Hei Ku on 2008-04-11
no tiene ports abiertos. seguro que la maquina no esta prendida, pero en modo leecher, o sea que baja pero no manda?

---

### Post by faktorqm on 2008-04-12
capo, vos necesitas un front end para nmap. busca el paquete "nmapFE" o "PE" si me llegue a equivocar el nombre perdon, pero era algo asi. ahi tenes todo grafico para seleccionar tranquilo las opciones que queres, y aparte t muestra que comando es el que elegiste asi lo aprendes a usar por consola.
observacion: te pone links en 2 lugares, hay uno que no te lo deja usar por que sos root, y se pone en otro lugar que te pide contraseña justamente para ejecutarse como root. sino a mas tardar andate hasta preferencias -> menu principal y le agregas "gksudo" al comando y se acabo. Salu2!!

---

### Post by sergiom99 on 2008-04-12
sabes si tiene un router, firewall o algo? 
no es raro que tenga todo cerrado.

como GUI yo uso Knmap, que es el que viene en KDE, pero seguro debe haber algo para Gnome.

---

### Post by ramiro_md on 2008-04-12
Gracias muchachos, ya lo hice andar en el "front end", hasta ahora me estoy guiando bastante bien...si tengo alguna consulta posteo de nuevo.
Saludos

---

