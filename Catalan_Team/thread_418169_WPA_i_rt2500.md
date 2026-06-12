---
title: "WPA i rt2500"
date: 2007-04-22
forum: Catalan Team
---

### Post by sianeu on 2007-04-22
Tinc un ordinador conectat per wifi (no puc fer-hi arribar cable sense fer destrosses), i no hi ha menera dTe que funcioni bé.

Te una tarjeta Linksys amb el controlador rt2500. La seguretat es wpa amb el ssid amagat i filtrat mac.

He provat un fotimer de tutorials, guies i receptes sense éxit. He aconseguit que funcioni correctament la conexiò deshabilitant el network-manager (crec que es això, la recepta estava en alemany) i configurant el arxiu  /etc/network/interfaces, però aleshores el ordinador es queda penjat a l'arrancada, desprès de posar l'usuari i la contrasenya; es queda mostrant un color marrò-clar-ubuntu uniforma a tota la pantalla. Llavors tinc d'entrar a terminal (ctrl+alt+f1), borrar una part del arxiu interfaces i reiniciar. Si torno a reconstruir interfaces, ja puc tornar a intermet.

Pas per pas, això es el que he fet:

*Deshabilitar network-manager
   sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

   sudo /etc/dbus-1/event.d/25NetworkManager stop

   sudo sh -c "echo 'exit' > /etc/default/NetworkManagerDispatcher"

   sudo sh -c "echo 'exit' > /etc/default/NetworkManager"  

*/etc/network/interfaces queda així:

   auto lo

   iface lo inet loopback

   

   # The WLAN interface

   auto ra0

   iface ra0 inet static

   address 192.168.1.3

   netmask 255.255.255.0

   gateway 192.168.1.1
   
   pre-up iwconfig ra0 mode Managed
   pre-up iwpriv ra0 set Channel=2

   pre-up iwpriv ra0 set AuthMode=WPAPSK

   pre-up iwpriv ra0 set EncrypType=TKIP

   pre-up iwconfig ra0 essid meu-essid

   pre-up iwpriv ra0 set WPAPSK=mev-contrasenya

Crec que el que provoca  la fallada es la linea "pre-up iwconfig ra0 mode Managed" dons posant-hi una configuració molt semblant que anava amb la recepta alemanya, no puc conectar pero el ordinador arranca bè:



 
auto ra0

iface ra0 inet static

address 192.168.1.3

netmask 255.255.255.0

gateway 192.168.1.1

dns-nameservers 192.168.1.1



pre-up ifconfig ra0 up

pre-up iwpriv ra0 set AuthMode=WPAPSK

pre-up iwpriv ra0 set EncrypType=TKIP

pre-up iwconfig ra0 essid YOURESSID

pre-up iwpriv ra0 set WPAPSK="YOURWPAPSK"



He de afegir que a més he hagut de posar les dns a Sistema/Administracio/Xarxa (però sense activar cap mès parametre. Posar la dns del router com fa l'alemany tampoc em servia. La linea "pre-up ifconfig ra0 up" no pot ser-hi, dons fa que no conecti encara que el demés estigui  com a dalt.

Avans, amb el Dapper, fent-ho d'aquesta manera però sense desactivar el network-manager (que crec que no va activat com en el Eddgy i Feisty) podia entrar i conectar-me, però tardava entre 3 i 5 minuts a entrar a l'escritori desprès de posar usuari i contrasenya.

Viam si algù pot ajudar-me !!  Si calen més dades dieu-ho.

Salut

---

### Post by patrickfromspain on 2007-04-22
Jo tambe tinc una tarjeta amb l'rt2500 i el que et recomano: sudo dpkg --purge netwok-manager network-manager-gnome... treu el network manager del tot. Total, si no el fas servir, per a que el vols? ;)

Despres.. de lo demés.. has probat a posar mode Auto en ves de managed? Igual et serveix d'ajuda. També, al synaptic trobarás un paquet que es diu rt2500, es el programa de ralink per configurar les seves tarjetes i potser et serveix t'ajuda.

salut!

---

### Post by sianeu on 2007-04-22
Gracies.Si no funciona lo de auto, provaré el driver de ralink.

La sintaxis seria aixi:

pre-up iwconfig ra0 mode Auto

correcte?. en majuscula la A?

salut

---

### Post by patrickfromspain on 2007-04-22
Hem sembla que si, la A majuscula. Aqui tens 2 cosetes, per si et serveixen d'ajuda:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)
[http://ubuntuforums.org/showthread.php?t=78250&highlight=rt2500+wpa](http://ubuntuforums.org/showthread.php?t=78250&highlight=rt2500+wpa)

---

