---
title: "Maldecaps amb driver NVIDIA, xorg.conf .. 10.04"
date: 2011-03-04
forum: Catalan Team
---

### Post by ephramdoyle on 2011-03-04
Hola a tothom! 
Ja porto gairebé 4 dies gastant un munt d'hores a realitzar proves,  consultar per la xarxa i escriure en diferents fòrums, però no  aconsegueixo solucionar-ho..
A veure si em podeu ajudar, crec que la solució és la configuració del  fitxer **xorg.conf** però no sé com a de ser el seu contingut per la meva gràfica...

Abans tot funcionava correctament però una de les actualitzacions ha desconfigurat els drivers de la gràfica.

[B]Model Portàtil: N51V 
Característiques: intel CORE Duo 2 - NVIDIA GEFORCE GT 240M
Versió Ubuntu: 10.04 LTS - la versió Lucid Lynx -[/B]

**_Problema:_**
Instal·lar correctament els drivers de la gràfica. 
Si instal·lo els drivers, a l'inici entra en un bucle abans d'arribar al login (alternant entre codi i el logo de nvidia).

Com a "parche" per carregar el SO. He eliminat el contingut de la carpeta /etc/X11 i li he copiat les dades d'un live cd.
Això  em permet accedir directament gairebé "correctament" però la  resolució màxima no és la veritable i no tinc acceleració 3D.
A més una vegada inicio sessió, durant la càrrega de l'escriptori es veu el següent missatge:

[http://img232.imageshack.us/i/malaconf.jpg/](http://img232.imageshack.us/i/malaconf.jpg/)

_Mètodes que he provat:_

**1. Desinstal·lo tot el que creo relacionat amb *nvidia**
    - En synaptic desinstal·lo tot el que comença per nvidia.
    - En consola:
                sudo apt-get --purge remove xserver-xorg-video-nouveau
        sudo apt-get --purge remove nvidia*
        sudo nvidia-uninstall
        sudo sh NVIDIA-Linux-x86-260.19.36.run --uninstall

    - En el directori /etc/X11/ elimino el xorg.conf

**2. Descarrego de la web oficial el driver de "NVIDIA GEFORCE GT 240M per Linux32"**
       - NVIDIA-Linux-x86-260.19.36.run
    
**3. He intentat instal·lar els drivers de 2 formes:**
_    A. - Tanco sessió. En la pantalla de login premo Ctrl + Alt + F1._
    - En consola:
            sudo service gdm stop
            su - (entro como root)
            sudo sh NVIDIA-Linux-x86-260.19.36.run
    - Instal·lació sense errors
    
_    B. - Creo un fitxer "instalar_NVIDIA" i dins escric:_
            ```
            #!/bin/sh
            nvidia-uninstall
            stop gdm
            bash NVIDIA-Linux-x86-260.19.36.run
            start gdm
```            
            Reinicio el SO. Entro amb la segona opció (recovery) escullo netroot.
            I escric: 
    sh instalar_NVIDIA
    - Instal·lació sense errors
    
    En acabar la instal·lació diu:
        > "Would you like to run the nvidia-xconfig utility to update your X configuration Automatically 
That file so the NVIDIA X driver will be Used When you restart X? 
Any pre-existing X configuration file will have backed up. 
[YES] [NO]     Selecciono "YES" perquè es configuri automàtic:
        > "Your X configuration file has Been Successfully updated. 
Accelented Installation of the NVIDIA Graphics Driver for Linux-x86 (version: 260.19.30) is complete. "     Si selecciono "NO":
        > "Installation of the NVIDIA Graphics Driver for Linux Accelented-x86 (version: 260.19.30) is complete. 
Please update your XF86Config or xorg.conf file as Appropriate; 
see the file usr/share/doc/NVIDIA_GLX-1.0/README.txt for details. "     El fitxer xorg.conf que generen: [http://paste.ideaslabs.com/show/605hylwyjb](http://paste.ideaslabs.com/show/605hylwyjb)
    
    En qualsevol cas en reiniciar quan es mostra el logo de nvidia torna enrere..
     Entra en bucle mostrant aquestes 2 captures:
     [http://img46.imageshack.us/g/24314766.jpg/](http://img46.imageshack.us/g/24314766.jpg/)
     bucle: [http://img717.imageshack.us/i/bucle1.jpg/](http://img717.imageshack.us/i/bucle1.jpg/) i [http://img638.imageshack.us/i/bucle2.jpg/](http://img638.imageshack.us/i/bucle2.jpg/)
    
**Què puc fer per instal·lar-ho correctament? gràcies**

---

### Post by wgarcia on 2011-03-05
Dos suggeriments senzills que no sé si s'has provat:

1) provar d'usar el mòdul lliure "nouveau"

2) provar si des de l'opció "recovery" del grub et reconfigura el sistema gràfica (et dóna accés a un pantalla amb diverses opcions algunes d'elles relacionades amb el sistema gràfic). 

En principi el fitxer "xorg.conf" no es necessita a no ser que vulguis fer alguna cosa especial.

---

### Post by ephramdoyle on 2011-03-05
Gràcies per respondre **wgarcia**.

He entrat en recovery, he provat les 3 opcions i cap ofereix resultat..
[B]* Utilitzar configuració predeterminada (genèrica)
[/B]- En reiniciar durant la càrrega la pantalla es posa durant uns segons verd, sense el logo animat de "Ubuntu carregant" i després carrega el login. 
En iniciar m'apareix el missatge comentat, conforme una dolenta una configuració.

[B]*Crear una nova configuració per a aquest maquinari.
[/B]- Aquesta si mostra el logo d'Ubuntu durant l'inici encara que amb un tamany una mica gran i amb algun flaix blanc sobre el. Igual que l'anterior login sense problemes però amb la resolució menor.

*Usar la seva configuració de respatller
- No fa res


Pots explicarme una mica en que consisteix el primer mètode nouveau?

salutacions

---

### Post by kimet on 2011-03-05
Estas segur que al fer això:** sudo apt-get --purge remove xserver-xorg-video-nouveau** no t'ha arrosegat tot el xorg? Per que no et carregui el mòdul nouveau només l'has de posar a /etc/modprobe.d/blacklist
En principi el intent 'A' sería correcte, depres es possible que hi hagi alguna incompatibilitat amb el driver nouveau, el poses a blacklist i creas un xorg.conf hon a l a secció device/driver hi ha de posar 'nvidia'.

---

### Post by wgarcia on 2011-03-06
El mòdul "nouveau" és un módul lliure per gestionar les targetes nvidia que hi ha disponible a linux des de fa un temps. No té totes les prestacions dels mòduls privatius ni funciona per a totes les targetes, però si funciona i si no necessites tota la funcionalitat gràfica pot ser una bona opció. 

Al següent enllaç donen solucions per al problema d'inici que t'has trobat:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by ephramdoyle on 2011-03-06
> **kimet said:**
> Estas segur que al fer això:** sudo apt-get --purge remove xserver-xorg-video-nouveau** no t'ha arrosegat tot el xorg? Per que no et carregui el mòdul nouveau només l'has de posar a /etc/modprobe.d/blacklist
En principi el intent 'A' sería correcte, depres es possible que hi hagi alguna incompatibilitat amb el driver nouveau, el poses a blacklist i creas un xorg.conf hon a l a secció device/driver hi ha de posar 'nvidia'.

Ara mateix he obert Synaptic he buscat "nvidia" y he desinstalat tot menys aquests 4:
[B]jockey-gtk
jockey-common
dmraid
conky-all[/B]

En consola:
**sudo apt-get --purge remove xserver-xorg-video-nouveau**

[sudo] password for ephram: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete xserver-xorg-video-nouveau no esta instalado, no se eliminará
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  dkms
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

I amb la resta de comandes:
sudo apt-get --purge remove nvidia*
sudo nvidia-uninstall
sudo sh NVIDIA-Linux-x86-260.19.36.run --uninstall

Comentaris semblants (ja que en principi ara ha no hi ha cap driver instalat).

He eliminat del directori /etc/X11/ xorg.conf però he deixat els seus backups.

Ara edito la **blacklist.conf** (sudo gedit /etc/modprobe.d/blacklist.conf) i he afegit al final:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

I ara provaré amb el gdm stop instal·lar el driver un altre cop.
El descarregaré de nou per si les mosques.
Aquest: [http://www.nvidia.es/object/linux-display-ia32-260.19.36-driver-es.html](http://www.nvidia.es/object/linux-display-ia32-260.19.36-driver-es.html)

. . . Seguint aquest pasos, després d'iniciar sessió em trobu el missatge de:
> No se pudo aplicar la configuración almacenada para los monitores 
X server does not support size requested

A continuació clic en **Sistema > Preferencias > Monitores**
> Parece que su controlador gráfico no admite las extensiones necesarias para usar esta herramienta. ¿Desea usar en su lugar la herramienta del fabricante de su controlador gráfico?
[NO] [SI]
 

Faig click en "Sí" i 
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Un altre cop en consola: **sudo nvidia-xconfig** i em crear un xorg.conf
Dintre de device diu:
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Torno a reiniciar el portàtil i NO VA T.T Mostra el bucle. Entro desde el recovery amb el missatge anterior i ara miraré el teu enllaç **wgarcia**

---

### Post by kimet on 2011-03-06
No m'has entés, **no has de desinstal.lar xserver-xorg-video-nouveau**. Es possible que al desinstalar-lo hagis desinstal.lat altres components de xorg.

---

