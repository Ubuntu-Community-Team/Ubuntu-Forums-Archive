---
title: "Problema con servidor DHCP"
date: 2007-05-06
forum: Argentina Team
---

### Post by seba2611 on 2007-05-06
Bueno acabo de armar una red y necesito utilizar un DHCP instale el dhcp3-server y lo configura de esta manera:

subnet 10.0.0.0 netmask 255.0.0.0 {
range 10.0.0.2 10.0.0.25;
#option domain-name-servers 10.0.0.100;
#option domain-name "internal.example.org";
option routers 10.0.0.1;
option broadcast-address 10.0.0.255;
default-lease-time 600;
max-lease-time 7200;
}

La pc q lo tiene instalado tiene una sola placa de red y esta directamente conectada al switch pero despues de realizar toda la configuracion y reiniciar el server me da este error:

May  6 14:09:34 seba dhcpd: Internet Systems Consortium DHCP Server V3.0.4
May  6 14:09:34 seba dhcpd: Copyright 2004-2006 Internet Systems Consortium.
May  6 14:09:34 seba dhcpd: All rights reserved.
May  6 14:09:34 seba dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May  6 14:09:34 seba dhcpd: Wrote 0 leases to leases file.
May  6 14:09:34 seba dhcpd:
May  6 14:09:34 seba dhcpd: Not configured to listen on any interfaces!

En donde le estoy pifiando a la configuracion???puede ser que tenga q asociarlo a la eth0??.
Una cosa mas la opcion de Dns ,gateway y dominio las dejo comentadas ya que es solo para una red local que no va a salir a internet.

---

### Post by clasificado on 2007-05-06
Meparece que te falta definir la interfaz a la que escucha en

```
/etc/default/dhcp3-server
```

fijate que tiene una sola linea (sin comentar)

```
# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
 # Separate multiple interfaces with spaces, e.g. "eth0 eth1".
 INTERFACES="eth0 eth1"
```

asi lo tengo yo.

Clasificado

---

