---
title: "no me reconoce 2da placa de red"
date: 2007-06-25
forum: Argentina Team
---

### Post by katon on 2007-06-25
Tengo un problemita tengo instalado en una maquina Ubuntu Dapper server estoy haciendo unas pruebas con Freeradius y Chillispot y algun que otro router Linksys que soporta open source.
El tema es que le agregue una segunda placa de red al server identica a la que estaba (eth0) marca 3com las dos.
La segunda placa la reconoce porque con *lspci* las veo a las 2 pero nose como activarla para que sea (eth1) en las interfaces... osea, la agregue ahi en /etc/network/interfaces pero no funciona.
Que debo hacer?
esto es lo que me da el lspci en naranja las placas 3com

[I]mati@dapper-server:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev 81)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
[COLOR="SandyBrown"]0000:00:0f.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)[/COLOR]
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
mati@dapper-server:~$ 
[/I]

---

### Post by guillermolisi on 2007-06-25
Katon

Te paso como tengo configurado en mi Ubuntu Server 7.04 el /etc/network/interfaces para que lo compares con el tuyo.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth1
iface eth1 inet dhcp

iface eth0 inet static
address 90.0.0.1
netmask 255.255.255.0

auto eth0

```

---

### Post by katon on 2007-06-26
la cosa es que yo le escribi ahi la eth1 con la configuracion que le quize dar a la segunda placa y despues reinicio el network interfaces y me da error

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static                     [COLOR="SandyBrown"]  // ESTA ANDA[/COLOR]
 address 192.168.150.207
 netmask 255.255.255.0
 gateway 192.168.150.1

 auto eth1                             [COLOR="SandyBrown"]   // ESTA NO ANDA ES LA QUE AGREGUE AHORA[/COLOR]
 iface eth1 inet static
 address 10.0.0.1
 netmask 255.255.255.0

---

### Post by guillermolisi on 2007-06-26
Te fijaste que dice /var/log/messages ?

Como es el error que te da cuando reinicias el servicio ?

---

