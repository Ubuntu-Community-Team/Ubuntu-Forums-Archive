---
title: "Software monitorització SAI"
date: 2011-03-16
forum: Catalan Team
---

### Post by carlesbm on 2011-03-16
Hola ha tots

     Desde fa uns dies que he comprat un SAI de la marca Salicru, i tinc un problema amb el programa de monitorització, i els ports USB:

    -Instal·lo el programa Winpower tal i com indica el document
    -sudo ./setup.bin
    -Selecciono les carpetes per defecte, tot correcte
    -Reinicio el ordinador i aqui apareix el primer missatge
    
    -Abans de que aparegui la finestra de selecció de usuari apareix un missatge informant del següent:

        "S'ha produït un error en muntar /proc/bus/usb"
        "prem S per seguir i M per modificar manualment"

     -Premo S i els sistema arrenca normalment
     -Posteriorment intento posar en marxa el software de la següent manera:

     carles@carles-desktop:~$ cd /opt/MonitorSoftware
     carles@carles-desktop:/opt/MonitorSoftware$ 
     carles@carles-desktop:/opt/MonitorSoftware$ sudo ./agent start
     [sudo] password for carles: 
     Starting Agent: 
     Done
     carles@carles-desktop:/opt/MonitorSoftware$ sudo ./monitor
      Starting Winpower Manager: 
      Done
     carles@carles-desktop:/opt/MonitorSoftware$

     En aquest punt el programa ha arrencar i faig que hem cerqui el sai , al cap de un temps apareix elsegüent missatge a la consola:

Broadcast Message from root@carles Desktop            
        (somewhere) at 23:47 ...                     
                                                                          
Winpower Message: Communication Lost: check connection and port setting.

Algú té alguna idea de que pot estar passant?

Moltes gracies per escoltar-me


P.D. En entorn Windows XP funciona perfectament

---

### Post by carlesbm on 2011-03-17
Hola 

   Us copio el resultat de executar lsusb

carles@carles-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 002 Device 003: ID 0665:5161 Cypress Semiconductor USB to Serial[/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carles@carles-desktop:~$ 

     La linia en vermell es el SAI

---

### Post by kimet on 2011-03-17
Has provat NUT?: [http://www.networkupstools.org/](http://www.networkupstools.org/)
I endollar-lo per port de serie?

Salut.

---

