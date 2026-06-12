---
title: "madwifi"
date: 2010-01-25
forum: Catalan Team
---

### Post by pserra on 2010-01-25
Hola,
fa un parell de dies que vaig mirant al portàtil  compaq de fer funcionar el wifi i de moment no m'ensurto. sembla que tot passa per instal·lar el madwifi
ja que tinc una atheros:
> root@pere-portatil:/home/pere# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
**02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
root@pere-portatil:/home/pere# 


hi ha alguna manera fàcil de instal·lar-lo?? he estat mirant enllaços i no m'ensurto.... per cert arranco amb el kernel 2.6.31.14... no se si te rés a veure.. 
MERCI

---

### Post by drpjkurian on 2010-01-25
Hi
I do not follow your language,I presume that you are looking for instructions to install Madwifi. If it is so please do give a try to my thread.
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

By the way is it Spanish?

---

### Post by papapep on 2010-01-25
> By the way is it Spanish? 

Nopes, it's [catalan]("http://en.wikipedia.org/wiki/Catalan_language") :)

---

### Post by akyra on 2010-01-26
Hola pserra

Jo el que vaig fer, és el que has vist en el link [http://ubuntuforums.org/showthread.php?t=1181204](http://ubuntuforums.org/showthread.php?t=1181204)
però ara no tinc el mateix ordinador i ja no ho necessito.

El madwifi el tenia en els "drivers restringits", com la tarja gràfica, i allà els activava.

Jo vaig activar els "restricted modules" i el "linux-backports" que utilitzen els últims drivers, però a mi no em va funcionar.

Potser això et pot ajudar:
[http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k), però en el kernel que tens ja ho tens actualitzat.

---

### Post by pserra on 2010-01-26
Vaig insta·lar el madwifi seguint el enllaç de  drpjkurian, em va sortir que se'm va instal·lar correctament, però no el visualitzo... ni fent madwifi al terminal... Com es configura?

---

### Post by pserra on 2010-01-30
Hola,
 he trobat un enllaç el qual sembla que m'ha de funcionar, ja que es un aparell COMPAQ i la mateixa wifi  que la meva (la comanda lspci | grep Wireless   retorna el mateix)
 però m'he quedat encallat al final... a veure si algú em pot donar un cop de mà:
l'enllaç esta a 
 [http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)
i el contigut es aquest: (disculpeu, es una mica llarg)
> 
[SIZE="2"]Ya tenia ratos de estar batallando con la wireless en mi laptop una compaq presario F755LA, ya que el manual que esta en la documentación de ubuntu no funciona para este modelo, me pase buscando en foros y blogs en los cuales daban soluciones, pero ninguna funcionaba o si funcionaba funcionaban mal, así que termine buscando en la pagina de madwifi, [http://madwifi.org](http://madwifi.org) y al fin encontré un driver que me ha funcionado bien, hasta logre activar mi tarjeta en modo monitor (Ya tengo pa divertirme jejeje), bueno pues al grano, los pasos para activarla son:

Primero verificamos que sea la wifi sea la correcta para este driver tecleamos lo siguiente en una terminal:

lspci | grep Wireless

(Este comando nos devuelve el tipo de tarjeta Wireless reconocida por el sistema)

La terminal nos tendra que devolver algo como esto:

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Si no les devuelve eso tengan por seguro que este tutorial no les va a funcionar :( , luego de eso tenemos que tener en cuenta que los controladores que trae ubuntu no funcionan así que no tenemos que tener instalados los siguientes paquetes para madwifi:


hostapd

madwifi-tools

Si tienen instalados esos paquetes desinstalenlos, ahora procedemos a descargar el driver, para ello nos dirigimos a [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) allí damos click en madwifi-hal-0.x.x.x donde las ultimas 3 X son numeros que van siendo actualizados con forme las nuevas verciones, en la proxima pagina le damos click al ultimo link que aparece en la lista, el cual contiene la ultima version del driver.

El archivo lo guardamos en el escritorio luego presionamos el juego de teclas alt+F2 y allí escribimos esto:

gnome-terminal

Con eso te abrirá una terminal, (es mas o menos como el cmd de windows), allí escribimos los siguientes comandos:
cd ~
(Ese comando nos ingresa al directorio home)
cd Escritorio
(Con ese comando ingresamos al Escritorio, si utilizan una version antigua de ubuntu el comando es cd Desktop)
tar xvzf madwifi-hal-xxxx.tar.gz
(Con este descomprimimos el archivo, las X las reemplazamos por la version que emos descargado, ejemplo:  tar xvzf madwifi-hal-0.10.5.6-r3861-20080903.tar.gz )
cd madwifi-hal-xxxx/
(con este ingresamos a lo que acabamos de descomprimir, volvemos a hacer el reemplazo de las “x”, ejemplo: cd madwifi-hal-0.10.5.6-r3861-20080903 )
make
(Con este comando compilamos el Driver)
sudo make install
(Con este comando instalamos el driver)
Con esto ya tendremos compilado e instalado el driver, ahora procedemos a probarlo con el siguiente comando:
**sudo modprobe ath_pci**
Si no nos devuelve nada este comando vamos por buen camino :) así que procedemos a cargar los modulos para el arranque escribimos lo siguiente en la terminal:
sudo gedit /etc/modules
y al final del archivo agregamos las siguientes lineas:
#inicia configuracion de wireless
ath_pci
#finaliza configuracion de wireless
Luego guardamos y procedemos a activar la tarjeta, con el siguiente comando, aunque lo mejor seria reiniciar:
sudo ifconfig ath0 up
(Si este comando les da algún error solo reinicien la PC con eso bastara)
Y listo al reiniciar ya tendremos funcionando nuestro wireless Atheros al 100% con posibilidad de usarlo en modo monitor, espero que les sirva el tutorial ;) .
[/SIZE]

el cas es que la instalacio va bé... però quan faig:
> **pere@pere-portatil:~$ sudo modprobe ath_pci**
em retorna:
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

vaig al arxiu en concret i tinc:
> pere@pere-portatil:~$ ls -l /etc/modprobe.d/
total 40
-rw-r--r-- 1 root root 2656 2009-12-03 14:35 alsa-base.conf
-rw-r--r-- 1 root root 2497 2009-10-12 00:07 alsa-base.conf~
[B]-rw-r--r-- 1 root root  136 2010-01-26 01:16 blacklist
-rw-r--r-- 1 root root  323 2009-07-06 15:13 blacklist-ath_pci.conf[/B]
-rw-r--r-- 1 root root 1603 2009-09-15 23:46 blacklist.conf
-rw-r--r-- 1 root root  213 2009-03-18 17:02 blacklist-firewire.conf
-rw-r--r-- 1 root root  662 2009-03-18 17:02 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2009-10-12 00:07 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2009-10-31 05:15 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 1077 2009-09-15 23:46 blacklist-watchdog.conf
-rw-r--r-- 1 root root   16 2009-03-05 19:57 libpisock9.conf


COM HO PUC SOLVENTAR?alguna suggerència??
Merci.

---

### Post by pserra on 2010-02-01
algu em pot orientar??
Merci

---

### Post by pserra on 2010-05-22
Per sort o per casualitat,
al formatejar la partició e instal·lar el Lucid des de el Live el problema s'ha solventat  tot 'sol', el que no fa es canviar de color el botó... però això es el de menys...

---

