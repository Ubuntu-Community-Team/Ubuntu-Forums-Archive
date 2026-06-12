---
title: "Para Sajnox, reenviar a la lista (problema eth en flisol)"
date: 2008-04-27
forum: Argentina Team
---

### Post by Hei Ku on 2008-04-27
Miguel, en la flisol habia un flaco que tenia un problema que su interfaz eth0 se cambiaba cada vez que reiniciaba. La cosa es que no me acuerdo el nombre, y me dijo que no entraba al foro, sino que estaba subscripto a la lista. Le podes pasar esto? No me acuerdo el nombre, soy de terror para eso. :D

Buscando un poco, encontre que es un problema comun con esas placas. Basicamente lo que hay que hacer es editar unas rules, para que reconozca la placa siempre como eth0.
Aca esta explicado en ingles: 
[http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot](http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot)

Lo que hay que hacer es:

editar el archivo /etc/udev/rules.d/70-persistent-net.rules

Buscar la parte que diga algo asi:
SUBSYSTEM=="net", DRIVERS=="forcedeth", ATTRS{vendor}=="0x10de",
&#10149; ATTRS{device}=="0x054c", NAME="eth0"

y editar el valor de ATTRS con el resultado de lo que diga esto:
cat /sys/class/net/ethX/device/{device,vendor}

reemplazar ethX, device y vendor por el especifico de la placa.
Con eso deberia salir andando.

---

### Post by sajnox on 2008-04-28
Impecable lo suyo, el flaco se llamo Maxi. Ahora paso el mail y te agrego un thanks en su nombre

---

### Post by faktorqm on 2008-04-28
Sos grosso mono! sabelo!!

---

