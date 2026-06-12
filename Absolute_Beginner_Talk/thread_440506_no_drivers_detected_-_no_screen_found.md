---
title: "no drivers detected - no screen found"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-05-11
hello,

I'm using a Sony Vaio with nvidia geforce 6400 graphics card
I recently updated from edgy to feisty. I then tried to get beryl to work (despite warnings...) and after I enabled the desktop effects (and thus suposedly getting the newest drivers), upon reboot it said that some drivers were not allowed to be used bacause my pc wouldn't work correctly. On driver permissions in system, the nvidia driver was green and loaded, and another driver was red and unused, while loaded as well. But as the nvidia driver seemed to work just fine,I installed beryl from synaptics. 
trying to get it to work and try it, I followed a thread that I can no longer find (still searching), which said how to make beryl work in feisty following 10 steps. 
Even though i had already installed beryl, I thought I should give it a try in case the red dot mentioned above was the result of a bad installation. 
I followed the first ones, which had to do with erasing the old driver and downloading the new ones and then I followed the command 
**sudo /etc/init.d/gdm stop** to enter the black screen (sorry, forget the name :) )
once there, i wrote 
**sudo sh NVIDIA-Linux-x86-1.0-9xxx-pkg1.run/9746** (I had downloaded the 9746 drivers in theory)
but nothing happened. 
i tried to exit with  **sudo /etc/init.d/gdm start** but still nothing
I rebooted and I am now unable to enter the graphic environment because 
**(EE) failed to start the Xserver - it is not set up correctly,   no drivers detected no screen found**
It seems that I erased my nvidia drivers and while attempting to download the new ones it didn't manage to..
it also seems that the etc/x11/xorg/conf is not there or not set up correctly.

I think I should download the drivers again. However, while I know that I could just follow a thread on how to do it, i'm afraid of just causing more damage in case it has something to do with another thing I do not know of.
If somebody knows what's wrong please give me the commands so as to restore my screen. 

(oh, and if things like my xorg/conf result are needed, as I am now searching about it through xp and have to restart, nor have I a floppy, PLEASE just tell me what exactly I am looking for because I'll have to write it down by hand...) 

please help.. :)

NOTE: this is not a Beryl problem, even though it started attempting to use it. It is a problem of me just trying things without sufficient knowledge (but how else can we learn?)

---

### Post by Foxmike on 2007-05-11
Ok, it seems your xorg.conf is not right.  When booting in CLI (command line interface), try this:
```
dpkg-reconfigure xserver-xorg
```

That should allow you to get back to a graphical environment.

Then, you should try re-installing your video drivers using the Restricted Drivers Manager that can be found with the menus under System->Administration.

Regards,

-FM

---

### Post by Morkhaar on 2007-05-11
thanks for the reply!

I did just that, and then it autodetected the drivers and prechose some answers guiding me through a reconfiguration process. In the beginning everything looked ok, splash screen and loggin, but then when I log in, it only shows my mouse pointer and a white screen or a white square in a black screen. :confused: 
what now?!

---

### Post by Morkhaar on 2007-05-11
if it helps in any way, i used the directions from go beryl go:
the bold ones are the ones I followed and apparrently nothing was happening in shell because i put .run/9746 and not .run /9746...

1 - Instalate los paquetes necesarios para compilar el controlador
**sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev pkg-config**

2 - Remove el residual del driver open source o drivers viejos que detecto ubuntu por default.
**sudo rm /etc/init.d/nvidia-***
[B]sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo gedit /etc/default/linux-restricted-modules-common[/B]
edita la unica linea que viene por default y que dice
DISABLED_MODULES=""[/B] y agrega nv (el driver open source de nvidia que carga por default ubuntu si detecto bien la tarjeta
Te quedaria asi
**DISABLED_MODULES="nv"**

3 - Descargate los drivers privativos de NVIDIA F-Corporation :P
Si tu placa es viejita tipo GeForce 440 MX si o si debes usar los 9631 o si queres un poco de mejor framerate porque los 9631 siguen siendo los de mejor rendimiento mas alla de alguna molesta pantalla negra
wget [http://us.download.nvidia.com/XFree8...-9631-pkg1.run](http://us.download.nvidia.com/XFree8...-9631-pkg1.run)

Si tu placa es de las mas nuevas descarga los drivers mas recientes:
1.0-9746
**wget [http://us.download.nvidia.com/XFree8...-9746-pkg1.run](http://us.download.nvidia.com/XFree8...-9746-pkg1.run)**

o los nuevitos 1.0-9755 (al fin!!)
wget [http://us.download.nvidia.com/XFree8...-9755-pkg1.run](http://us.download.nvidia.com/XFree8...-9755-pkg1.run)
Elegi el que te guste o el que necesites para download. No descargues todos eh!!!! No seas lammer jaja

4 - CUIDADO! Alarm! uuuUUUUuuu (onomatopeya de una sirena LOL) :P
Ahora hay que dar de baja el servidor grafico X o X server asi que te vas a quedar sin iconitos y todo eso y vas a ir a la oscuridad de la pantalla negra donde solo hay horrorosas letras y nada mas.. más conocido como Shell.. Uhhh! Que miedito
Asi que anota en papel el los proximos 3 pasos.
Control+Alt+F1
La forma mas sencilla de cerrar el servidor grafico en Ubuntu es ejecutar el script de apagado del servicio Gnome Display Manager
Lo realizas con este commando:
**sudo /etc/init.d/gdm stop** (anota en papel)

5 - Ahora instala los controladores de nVIDIA
sudo sh NVIDIA-Linux-x86-1.0-9xxx-pkg1.run / 9631, 9746 o 9755 segun cual hayas bajado (anota en papel)
Si estas con Ubuntu EE o FF y estas siguiendo esta guia "paso a paso" (como diria Reinaldo "Mostaza" Merlo) no necesitas el path al codigo fuente del kernel ni nada. Con solo esto anda perfecto! iiiupi!

Cuando el programejo de Instalacion de Nvidia te dija que te va a modificar el archivo original de configuracion (xorg.conf) decile que si.. despues guardate el backup que crea en algun lugar porque a veces en cuanto a configuraciuon de raton teclado o alguna wacon que tengas te van a servir mejor esos parametros detectados por Ubuntu, a nvidia solo le interesa la parte grafica y no le importa mucho el tema teclado y demas y te pone cualquier verdura generica a veces

6 - Reinicia el servidor X con:
sudo /etc/init.d/gdm start (Anota en papel (ultimo))

Arrancan de nuevo las X. Ahhh! se hizo la luz. Abandonaste a Darth Vader en el Shell y volviste de la mano de la Princesa Leia al colorido entorno grafico
Y si pudiste ver el logo de Nvidia descorchate un champucito (trad: Destapa una botella de Champagne) porque ya casi estas listo para que Beryl te ande per-fec-to!

7 - Ahora editate el xorg.conf (archivo de configuracion del servidor X)
sudo gedit /etc/X11/xorg.conf
y agrega solo estos dos parametros al archivo de configuracion de las X.

Busca algo como esto:
Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
y abajo del 24 agrega:
Option "AddARGBGLXVisuals" "True"

Al final de todo como nueva seccion
Section "Extensions"
Option "Composite" "Enable"
EndSection

8 - Carga los repos oficiales de Beryl y ejecuta el correspondiente apt-get para traerte los paquetes e instalar el mejor manejador de ventanas de todos los tiempos a.k.a. Beryl

##Beryl para edgy
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

##Beryl para feisty
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

Incorpora la llave publica (si aun no la tenes)
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

9 - Instala desde repos al fabuloso Beryl:
sudo apt-get update
sudo apt-get install beryl emerald

10 - Abri una consola o terminal y tipea el comando magico, llave a la diversion infinita :P
beryl-manager

---

