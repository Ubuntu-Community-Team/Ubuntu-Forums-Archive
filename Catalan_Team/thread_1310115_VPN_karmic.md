---
title: "VPN karmic"
date: 2009-11-01
forum: Catalan Team
---

### Post by akyra on 2009-11-01
Hola de nou,

També m'he trobat que no em funciona la conexió VPN amb el client de cisco per 64 bits, abans ho podia aplicant un patch en el vpnclient i funcionava sense cap problema, però ara no em funciona, i amb el network-manager no es permeten tunels TCP.

L'error que em surt quan l'instal·lo és:
> hutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/jordi/Documentos/Programes/vpnclient/vpnclient modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/jordi/Documentos/Programes/vpnclient/vpnclient/linuxcniapi.o
In file included from /home/jordi/Documentos/Programes/vpnclient/vpnclient/Cniapi.h:15,
                 from /home/jordi/Documentos/Programes/vpnclient/vpnclient/linuxcniapi.c:31:
/home/jordi/Documentos/Programes/vpnclient/vpnclient/GenDefs.h:221:2: error: #endif without #if
make[2]: *** [/home/jordi/Documentos/Programes/vpnclient/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jordi/Documentos/Programes/vpnclient/vpnclient] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Error 2
Copying module to directory "/lib/modules/2.6.31-14-generic/CiscoVPN".


Alguna idea de com solucionar-ho, o algú sap algun client per 64 bits

Gracies

---

### Post by akyra on 2009-11-03
Hola

Després que el client de cisco no en funciones a karmic, he probat amb el KVpnc.
He importat el perfil del fitxer de Cisco sense problemes, pero quan em connecto em diu
> Host 212.xxx.xxx.xxx could not be resolved

Algú sap que pot ser.
(Jo utilitzu Gnome, no Kde)

Gracies

---

### Post by papapep on 2009-11-03
Akyra,

No cal obrir un fil per a cada intent diferent que fas sobre el mateix tema, sinó es perd el fil, mai més ben dit, de la conversa.

T'està dient que no troba la ip que li dius. El perquè, doncs ni idea. Jo provaria a parlar amb l'administrador de la VPN abans de fer més invents.

---

### Post by akyra on 2009-11-03
Hola Papapep,

Vaig obrir un fil pel client de Cisco que en Karmic ha deixat de funcionar al compilar, i sembla que fa falta un nou patch.

Amb el KVpnc no és un problema de la administració de la VPN ja que fins dissabte vaig conectar i ara mateix i ja persones connectades, sino que és un tema de la configuració del KVpn suposo a que la conexió es fa per TCP i no per UDP, però només tinc la sospita, no sé si el KVPN ho admet.

Però si penses que és millor ja m'està bé juntar-ho amb el mateix fil.

Gracies.

---

### Post by sbenejam on 2009-11-04
Has provat el vpnc? vpnc-connect /etc/vpnc/vpnc.conf per connectar i vpnc-disconnect per desconnectar. La configuració va a /etc/vpnc/vpnc.conf.

Sort

---

### Post by akyra on 2009-11-06
Bé sebla que he trobat una solució, no sé si la millor però com a mínim funciona.

Com m'ha funcionat ha sigut amb el Vpnc que es configura des del network-manager.
He importat l'arxiu de configuració de cisco, em diu que no soporta tunnel per TCP i que pot ser que vagi malament, ho accepto i es carrega.
Després a la pestanya a on es pot seleccionar el tipus de comunicació (CISCO-UDP, NAT-T, None) selecciono NAT-T, i pel moment m'està funcionant perfectament.

Amb la selecció de CISCO-UDP, em funcionava durant un minut i després es penjava.

Amb el KVpnc, que és una GUI del Vpnc, em segueix donant el mateix error que no pot trobar el servidor i no sé perquè pot ser, pero com em funciona des del network manager, per mi millor.

També he lograt compilar el client de Cisco per Karmic, però no m'ha funcionat gaire bé, a vegades entra a la VPN i a vegades no.


Gracies.

---

