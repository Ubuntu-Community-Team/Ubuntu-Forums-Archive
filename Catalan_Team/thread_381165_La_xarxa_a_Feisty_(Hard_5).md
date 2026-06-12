---
title: "La xarxa a Feisty (Hard 5)"
date: 2007-03-10
forum: Catalan Team
---

### Post by sianeu on 2007-03-10
Soc molt notillo i potser diré tonteries, peró  he trobat una solució a un problema del que no he trobat cap referencia. La poso aqui per si algú més s'hi troba.

 Feisty (Hard 4 i 5) em dona un error en la conexió a xarxa que no tenia amb les versions Dapper i Edggy.
Tinc dues conexions Lan (una Gigabit Marvell i una Nforce) en la placa base de Asus A7N8X-E de luxe.


Al iniciar el sistema, el network-manager, que ara ve preinstl·lat i mostra una icona a dalt al costat dels altaveus, em diu que estic connectat. No es veritat i a més es impossible perque tinc deshabilitat el DHCP en el router. El curiós es que quan el configuro com a ip fixe, en acabar de fer-ho, surt un altre lletreret que ara diu que he perdut la connexió. A més la connexió es per cable, no inalambrica. 

Aquest es el arxiu interfaces que tinc:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.23
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.23
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Recordant una mica la configuració que tenia en les instal·lacions al Dapper i al Edggy, he provat a comentar les tres últimes entrades.... I ha funcionat!!!. Es a dir, la forma del arxiu /etc/network/interfaces que fuciona amb el Feisty per aquesta placa (o per a totes les ip's fixes, no ho se) es:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.xxx 
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

   *substituir les xxx per la ip corresponent (la teva)

Ara la icona del network-manager de la barra superior diu "no hi ha cap conexió de xarxa". Peró hi es i funciona perfectament. Si algú que sàpiga anglès vol reportar l'errada a l'equip de Ubuntu......

Salut

---

