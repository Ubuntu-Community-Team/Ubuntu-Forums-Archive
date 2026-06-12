---
title: "problemas en un gps con adaptador serie/usb"
date: 2007-11-12
forum: Argentina Team
---

### Post by alhanduin on 2007-11-12
Buenas!!! Aquí os cuento lo que me pasa:

Me compre un gps modelo garmin etrex vista (de hace unos 3 años) con conector serie para pc, pero mi ubuntu esta en un portatil que no tiene entrada serie para lo que tuve que comprar un adaptador serie/usb. 

Cuando ya lo tenia todo conectado procedí a enchufar el gps al puerto usb mediante el conector y mi sorpresa cuando vi que ubuntu gutsy no reaccionaba!!!!! No me montaba la unidad no hacia nada...

Por favor algun MASTER en ubuntu que me pueda ayudar!!!! pero que lo haga para novatillos!! muchas gracias por adelantado!

---

### Post by User21 on 2007-11-12
Los modulos de Garmin ya vienen en el kernel. Quizas tengas que cargar el modulo de usb serial converter: para hacerlo, en consola:
```
 sudo modprobe usbserial
```y fijate si al enchufar el GPS, es reconocido; para ello, en la consola:
```
lsusb
```y puede que salga el nombre del GPS en alguna de las salidas de los usb.

De no ser reconocido, deberias agregar ademas, el modulo de Garmin:

```
 sudo modprobe garmin_gps
```Si es asi, ya solo resta instalarte algun programa para gestionar los datos GPS, Hay un par en el gestor de paquetes Synaptic. (Sistema > Administracion > Gestor de paquetes Synaptic) y busca alli GPS.

Si todo te funciona, carga el modulo al arranque del sistema. Cómo?
```
 sudo gedit /etc/modules 
```y alli, escribi usbserial y garmin_gps (uno en cada renglon) debajo de todo. De este modo, esos modulos se cargaran al inicio. Guarda el archivo, LISTO.

Mas ayuda [aqui]("http://www.e-oss.net/wordpress/?p=125") o tambien [aqui]("http://plutontech.losplutonianos.net/2005/05/16/262/").

[B] Suerte! Dinos como te fue!
[/B]

---

### Post by alhanduin on 2007-11-12
Ei ya lo he probado y esto es lo que me ha salido:

alhanduin@Tourmix:~$ lsusb (antes de conectar el gps)
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. (raton)
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

alhanduin@Tourmix:~$ lsusb (tras conectar el gps)
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Pero no me monta ninguna unidad.... como lo hago? Xq me he fijado que cuando apago el gps dejando el cable enchufado y hago un lsusb me sale el mismo mensaje! eso es que reconoce el adaptador de serie pero no me reconoce el gpsno??? Que puedo hacer ahora??? 

Siento ser tan torpe... xo soy nuevecilloen ubuntu... muchas gracias por la ayuda! a ver si pasito a pasito llegamos a conectar el gps al ubuntu!!!! OS estaria MMMMMMMMMMMMUY agradecido!

---

### Post by User21 on 2007-11-12
Leete esto a conciencia: puede que parezca dificil, siendo un iniciado a Ubuntu, pero si lo lees con paciencia, y haciendo paso a paso lo que dice, puede que obtengas resultado. Una cosa es segura: se reconoce que algo esta conectado!! :) 

para empezar: 

sudo apt-get install gpsd 

Luego, leyendo que hace, y perseverando...

---

### Post by alhanduin on 2007-11-13
Las soluciones que me ofreciais no me funcionaban así que seguí buscando y al final logré solucionar el problema mediante este howto:

Running OziExplorer under LINUX
(Contributed by an OziExplorer user)

(Note: We do not have a Linux version of OziExplorer but a user has OziExplorer running using this procedure.)
Linux Distribution: Ubuntu Linux 6.06 LTS "Dapper Drake"
OziExplorer version: 3.95.4m
Wine version: 0.9.16

I succeeded in making OziExplorer work, apparently with all features...

Full Procedure:

Step 1. Install "Wine" (I followed the instructions in the "ubuntu user documentation" to get the latest version):
First, in Synaptic, add the following repository 

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Then, reload, update, and install wine
When you first run wine, it will create a .wine directory in you home dir. Inside it, will be a "drive_c" that simulates the windows environment.

**If you're using another linux distribution, download the software from [http://www.winehq.com](http://www.winehq.com) and follow the instructions)

Step 2. copy the file "oziexp_setup. exe" to ~/.wine
I tried running it from another location, but it failed (I don't know why)

Step 3. In the terminal, change to the "~/.wine" directory, where oziexp_setup.exe is.

Step 4. Run the OziExplorer installation file with wine. In the terminal, type:

wine oziexp_setup.exe

The setup will install OziExplorer under ~/.wine/drive_c/OziExplorer/
(if you have any trouble here with permissions, try running wine with "sudo". type: "sudo wine oziexp_setup.exe"
If you use another distribution without "sudo" run the command as "root")

The program won't run just yet ...

Thanks to Stephen B, in the "WineHQ" (on Tuesday November 8th 2005) the initial crash problem is solved:
Under ~/.wine/drive_c/OziExplorer/, edit the file "oziexp.ini", adding the following lines (It disables the tooltips at the start):

[Help]
Show Start=0
Getting Started=0

Now it works! (at least it should...)
We just have to setup the gps... Apparently, serial communication works fine, but I can't guarantee it because my GPS connects through USB.
If your GPS connects through serial COM, you must only remember that in linux, COM1=/dev/ttyS0, COM2=/dev/ttyS1, etc.
Step 5. (Additional step required for Garmin USB GPS's)
In the case of USB connection, I use a "Garmin GPS60". Gamin drivers are already built into Ubuntu kernel, so Linux should recognize the device.
After connecting the GPS, run "dmesg" to find out: you should see lines like these:
.....
[17193444.360000] usb 1-3: new full speed USB device using ohci_hcd and address 4
[17193444.560000] garmin_gps 1-3:1.0: Garmin GPS usb/tty converter detected
[17193444.560000] usb 1-3: Garmin GPS usb/tty converter now attached to ttyUSB0
.....

The problem is OziExplorer doesn't recognize "/dev/...", so we can get around the problem making a "sym link" from "COM to USB". I chose COM3 to avoid interference with other things (COM3=/dev/ttyS2).
In the terminal, type:

sudo ln -sb /dev/ttyUSB0 /dev/ttyS2

(the "b" option makes a backup copy of ttyS2 in case you want to "get back")
After that, you must start OziExplorer by typing: 

wine ~/.wine/drive_c/OziExplorer/OziExp.exe

In "Ozi", go to the menu "File" > "Configuration" > "GPS" and choose your GPS make and model.
Then, under "COM" choose COM3, leave the "Garmin USB" or other UNCHECKED (this way, the software "thinks" the GPS is under COM3...)
SAVE the configuration and exit.

Step 6. ITS DONE!!! By now, you must be able to communicate to and from the GPS, and have OziExplorer working just fine!

I hope this will help someone...

---

### Post by User21 on 2007-11-13
Básicamente es lo mismo que aparece en los anteriores links, sólo que en este caso usa un programa nativo de win, ejecutado via wine. Redirecciona el origen de la conexión  (sudo ln -sb /dev/ttyUSB0 /dev/ttyS2) y logra hacer funcionar el GPS a través de eso. 

De todas formas, si esto te funciona, pues, bienvenido sea! Aparte aportaste información para todos aquellos quienes deseen usar GPS Garmin, por estos pagos... 

Aún así: El desafío del software libre, es encontrar las soluciones, para dejar de depender de tu antiguo sistema (léase "maldito win"); y hay muy pocas cosas que no tienen solución en Linux/Ubuntu. Solo es necesaria una actitud curiosa y perseverante!

Exitos!!! :)

---

