---
title: "Problemes amb WiFi"
date: 2009-03-01
forum: Catalan Team
---

### Post by AnFoAr on 2009-03-01
Bon dia a tothom,

He instal·lat fa unes setmanes l'ubuntu 8.1 al meu portàtil i per començar ja he tingut uns quants problemes que no sé com resoldre.
El primer i el més importatnt ara per ara és el que us explico:
No puc conectar-me a Internet. Amb l'antic windows xp que tenia, conectava a l'ADSL de casa sense cap problema inalambricament.
Amb l'ubuntu, no em troba la xarxa inalàmbrica, jo diria que no està instl·lat el contrololador de la wifi.
No sé com agafar-mi i estic molt desanimat, si algú pot ajudar-me, li agrairé.

Salutacions

---

### Post by dmartinez116 on 2009-03-01
Necessitem més info per a ajudar-te.

Model del portatil, de la targeta de xarxa.

Executa:
```
lspci
```
i enganxa al forum el resultat.

---

### Post by AnFoAr on 2009-03-02
Gràcies per contestar tant ràpid.

El model del meu portatil és un Fujitsu-siemens esprimo model V5535

He fet un lspci i el resultat ha estat aquest:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Em fa l'efecte que això que posa Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) vol dir que el controlador hi és, el que no sé és doncs com connectar-me a la xarxa wireless.

També suposo que és una tonteria, però no sé com es fa de canviar la resolució de la pantalla, estic treballant a 800 x 600 i voldria canviar-ho a 1024 x 768 i tenir més colors. He anat a "configurar ajustes de pantalla" i només tinc la opció de 800 x 600 o 640 x 480. He mirat de tort i de través per tot arreu, i no ho he trobat enlloc. 

Gràcies una altre vegada.
Salutacions

---

### Post by papapep on 2009-03-02
Hola AnFoAr, mira't aquest fil a veure si t'arregla el problema:

[http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x)

Per la gràfica obre un altre fil, si us plau, i enganxa-hi això que has posat a aquest:

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

---

### Post by dmartinez116 on 2009-03-02
Anim AnFoAr, jo abans tenia el mateix portatil, la wifi funcionava perfectament, però no recorde el fil que vaig serguir per a fer-la funcionar (segurament el de papapep funcione).

La gràfica, també la vaig ficar a algo més de 800x600, però no vaig aconseguir fer funcionar el compiz, ni la resolució màxima que obtenia amb el güindous. Eixe va ser un dels motius per a canviar al compaq que tinc ara que portava una nvidia.

---

### Post by AnFoAr on 2009-03-02
> **papapep said:**
> Hola AnFoAr, mira't aquest fil a veure si t'arregla el problema:

[http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x)

Per la gràfica obre un altre fil, si us plau, i enganxa-hi això que has posat a aquest:

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

He anat a l'adreça 
      [http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x) i allà he troba una informació que m'adreça a aquesta aitre adreça:
      [http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=973286&highlight=AR242x)
i he fet el que diu allà, és el següent:

He obert una finestra i l´hi he posat el següent

AnFoAr@ubuntu:~$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Leyendo lista de paquetes... Hecho
Creando Ã¡rbol de dependencias       
Leyendo la informaciÃ³n de estado... Hecho
Leyendo la informaciÃ³n de estado extendido      
Inicializando el estado de los paquetes... Hecho
Se instalarÃ¡n los siguiente paquetes NUEVOS:
  ndisgtk ndiswrapper-common ndiswrapper-utils-1.9 
0 paquetes actualizados, 3 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/77,1kB de ficheros. DespuÃ©s de desempaquetar se usarÃ¡n 676kB.
Escribiendo informaciÃ³n de estado extendido... Hecho
Cambio de medio: Por favor, introduzca el disco etiquetado 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)' en la unidad '/cdrom/'
y presione [intro].

Cambio de medio: Por favor, introduzca el disco etiquetado 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)' en la unidad '/cdrom/'
y presione [intro].


Llavors, es queda així, i no carrega res del CD. 
És que no tinc el CD correcte ?
Què faig malament?

---

### Post by torracastanyes on 2009-03-02
Probablement és que no hi ha res a carregar.
No ho sé segur, però crec que aquests paquets no estàn al CD.
Per poder-los carregar hauríes d'anar al menú "sistema" => "Administració" => "fonts de programari" (o "orígenes de software"), i a la pestanya "Programari de tercers" desmarca la opció "CD d'Ubuntu".
Això farà que synaptic busqui els paquets al repositori. (Hauràs d'estar conectat a internet per cable, es clar).

---

