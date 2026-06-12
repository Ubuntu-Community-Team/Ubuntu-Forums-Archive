---
title: "problemes amb l'adaptador serie/usb"
date: 2007-11-12
forum: Catalan Team
---

### Post by alhanduin on 2007-11-12
Bones!!! us explico el meu problema a vere si algú de vosaltres m'el sap solucionar xq sinó haure de tornar a windows!!!

Vaig comprar un gps garmin etrex vista (un model de fa un 3 anys) que te un cable serie per conectar-se a l'ordenador. El que passa és que jo tinc l'ubuntu en un portàtil i clar no te port serie. Llavors vaig comprar un adaptador serie/usb per palms, modems i coses així. Quan ho vaig tenir tot llest, ho vaig conectar al port usb amb el gps ences i no va passar res, 0, l'ubuntu gutsy no em va muntar cap unitat nova... suposo que no veu al gps... Què puc fer????? si us plau ajudeume!!!!

Si ho sabeu fer, si us plau explique-m'ho però com si fos x a un nen de primaria!!! k sóc nou en el linux i la veritat que entre el gps i la tarjeta grafica ati em te fregit!!!!

Moltes gràcies per adelantat!

---

### Post by CarlesOriol on 2007-11-12
Cada dispositiu serie a USB és un mon diferent per tant hauries de començar per dir-nos quin aparell és. ( i afegir les darreres linies del dmesg (des de el terminal) quan connectes l'aparell)
 
També aniria bé que ens diguessis quin és el programa tan important que necessites pel gps a veure si algú hi té experiència.

El tema de la targeta ATI crec que està molt covert en d'altres fils.

En el pitjor dels casos sempre pots usar el virtualbox per tal d'usar aquest programa en una màquina virtual en windows... que com que no tindrà ni anivirus ni antispyware ni antimicrosoftupdates ni totes aquestes coses et correrá molt més que el mateix windows (això si... sempre que tinguis prou memòria per fer-ho)

---

### Post by alhanduin on 2007-11-12
Ei carles!

L'aparell és un GPS, com ja dic és el model garmin etrex vista (diria que el c que és el model blanc i negre).

El que em passa és que jo el vull conectar a l'ubuntu en un port usb (xq el portatil no te ports serie) mitjançant un cable adaptador de serie a usb i l'ubuntu no el reconeix és com si no haguès enxufat re!

Necessito que l'ordenador m'el detecti i em pugui relacionar amb el gps per poder baixar i pujar tracks de les rutes que faig mitjançant un programa emulat que es diu oziexplorer (xq linux està una mica verd en aquest tipus de programes).

(respecte la tarjeta gràfica ja m'he instalat els drivers oficials i tal xo no m'acaba de funcionar com ho hauria de fer, m diu que tot stà b l'acceleració 3d i tot xo m surten ratlles, m va + lent... xo és igual això no em preoucupa! el que realment necessitaria solucionar és el problema del gps).

---

### Post by CarlesOriol on 2007-11-12
Pots escriure-ho correctament. No entenc res

---

### Post by alhanduin on 2007-11-12
A veure he evolucionat una mica he fet això:

alhanduin@Tourmix:~$ lsusb (sense el gps enxufat)
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

alhanduin@Tourmix:~$ lsusb (amb el gps enxufat)
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

M'he fixat però que si desenchufo el gps i fiag un lsusb em surt el mateix missatge així que suposo que em detecta el cable convertidor del port serie a usb pero no em reconeix el gps... vaig be??? algú em podria dir que puc fer ara???? Si us plau?

Moltes gràcies per adelantat

---

### Post by CarlesOriol on 2007-11-12
connecta l'aparell escriu dmesg i copians el resultat (sols el final)

---

### Post by alhanduin on 2007-11-12
Això es el que em surt:

[   24.888000] apm: BIOS not found.
[   25.092000] Failure registering capabilities with primary security module.
[   25.284000] Bluetooth: Core ver 2.11
[   25.284000] NET: Registered protocol family 31
[   25.284000] Bluetooth: HCI device and connection manager initialized
[   25.284000] Bluetooth: HCI socket layer initialized
[   25.304000] Bluetooth: L2CAP ver 2.8
[   25.304000] Bluetooth: L2CAP socket layer initialized
[   25.396000] Bluetooth: RFCOMM socket layer initialized
[   25.396000] Bluetooth: RFCOMM TTY layer initialized
[   25.396000] Bluetooth: RFCOMM ver 1.8
[   25.548000] Clocksource tsc unstable (delta = -137727411 ns)
[   27.140000] [drm] Initialized drm 1.1.0 20060810
[   27.192000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[   27.192000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   28.528000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   28.528000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   28.528000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   29.732000] [drm] Setting GART location based on new memory map
[   29.732000] [drm] Loading R300 Microcode
[   29.732000] [drm] writeback test succeeded in 1 usecs
[   66.044000] NET: Registered protocol family 17
[   82.492000] NET: Registered protocol family 10
[   82.492000] lo: Disabled Privacy Extensions
[   82.492000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   93.076000] eth1: no IPv6 routers present
[  112.136000] ipw2200: Firmware error detected.  Restarting.
[  685.296000] usbcore: registered new interface driver usbserial
[  685.296000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  685.296000] usbcore: registered new interface driver usbserial_generic
[  685.296000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  720.508000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  720.668000] usb 2-1: configuration #1 chosen from 1 choice
[  720.808000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[  720.808000] pl2303 2-1:1.0: pl2303 converter detected
[  720.808000] usb 2-1: pl2303 converter now attached to ttyUSB0
[  720.808000] usbcore: registered new interface driver pl2303
[  720.808000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[  780.244000] usb 2-1: USB disconnect, address 3
[  780.244000] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  780.244000] pl2303 2-1:1.0: device disconnected
[  843.484000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[  843.644000] usb 2-1: configuration #1 chosen from 1 choice
[  843.648000] pl2303 2-1:1.0: pl2303 converter detected
[  843.648000] usb 2-1: pl2303 converter now attached to ttyUSB0
[B][ 1149.324000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Garmin GPS usb/tty
[ 1149.324000] usbcore: registered new interface driver garmin_gps
[ 1149.324000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/garmin_gps.c: garmin gps driver v0.28[/B]
[ 2416.252000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2416.252000] : Add. Sense: Medium not present
[ 2416.252000] end_request: I/O error, dev sr0, sector 0
[ 2416.252000] Buffer I/O error on device sr0, logical block 0
[ 2416.252000] Buffer I/O error on device sr0, logical block 1
[ 2416.252000] Buffer I/O error on device sr0, logical block 2
[ 2416.252000] Buffer I/O error on device sr0, logical block 3
[ 2416.252000] Buffer I/O error on device sr0, logical block 4
[ 2416.252000] Buffer I/O error on device sr0, logical block 5
[ 2416.252000] Buffer I/O error on device sr0, logical block 6
[ 2416.252000] Buffer I/O error on device sr0, logical block 7
[ 2416.256000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2416.256000] : Add. Sense: Medium not present
[ 2416.256000] end_request: I/O error, dev sr0, sector 0
[ 2416.256000] Buffer I/O error on device sr0, logical block 0
[ 2416.256000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2416.256000] : Add. Sense: Medium not present
[ 2416.256000] end_request: I/O error, dev sr0, sector 4
[ 2416.256000] Buffer I/O error on device sr0, logical block 1

---

### Post by papapep on 2007-11-12
Jo diria que te'l detecta correctament.
En aquesta pàgina:

[http://www.gpsbabel.org/htmldoc-development/fmt_garmin.html](http://www.gpsbabel.org/htmldoc-development/fmt_garmin.html)

hi ha una pàgina d'un programa que diuen que funciona correctament amb el teu model (i un munt més), per a llegir i escriure tracks, rutes, etc.

---

### Post by CarlesOriol on 2007-11-13
Sembla correctament connectat a  /dev/ttyUSB0

---

### Post by alhanduin on 2007-11-13
Jo crec que em reconeix el cable serie/usb pero no el gps, però bueno. Al final em vaig baixar el gpsbabel i llegint el manual vai veure que he d'escriure a la terminal per a baixarme els traks i tal, i em va sortir el següent:

alhanduin@Tourmix:~$ gpsbabel -i garmin -f usb: -o gpx -F blah.gpx
Found no Garmin USB devices.

Si faig un lsusb em surt:

alhanduin@Tourmix:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

i si faig un dmseg:

[  896.024000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[ 1585.692000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1585.852000] usb 2-1: configuration #1 chosen from 1 choice
[ 1586.276000] usbcore: registered new interface driver usbserial
[ 1586.276000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1586.276000] usbcore: registered new interface driver usbserial_generic
[ 1586.276000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 1586.296000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[ 1586.296000] pl2303 2-1:1.0: pl2303 converter detected
[ 1586.296000] **usb 2-1: pl2303 converter now attached to ttyUSB0**
[ 1586.296000] usbcore: registered new interface driver pl2303
[ 1586.296000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[ 1634.212000] ADDRCONF(NETDEV_UP): eth1: link is not ready
alhanduin@Tourmix:~$ 

Si li especifico la unitat usb en la que està conectada que és la 0 em torna a sortir el mateix:

alhanduin@Tourmix:~$ gpsbabel -i garmin -f usb:0 -o gpx -F blah.gpx
Found no Garmin USB devices.

Teniu alguna idea de com ho puc fer??? Moltes gràcies per la vostra ajuda cada cop ens apropem més a la solució!!!

---

### Post by alhanduin on 2007-11-13
MMMM... a veure m'han dit que potser amb el convertor l'usb es converteix en un port serial i ho he intentat d'aquesta manere.. xo no se si ho faig be.. (suposo k no xq soc Korki):

alhanduin@Tourmix:/dev$ gpsbabel -i garmin -f com: -o gpx -F blah.gpx
[ERROR] XSERIAL: Cannot open serial port 'com:': No such file or directory
[ERROR] Cannot open serial port 'com:'
GARMIN:Can't init com:
alhanduin@Tourmix:/dev$ gpsbabel -i garmin -f ttySL:0 -o gpx -F blah.gpx
[ERROR] XSERIAL: Cannot open serial port 'ttySL:0': No such file or directory
[ERROR] Cannot open serial port 'ttySL:0'
GARMIN:Can't init ttySL:0

---

### Post by CarlesOriol on 2007-11-13
Si us plau. Si vols que t'ajudem escriu correctament.

---

### Post by alhanduin on 2007-11-13
Ho he solucionat gràcies a aquest howto que m'ha anat com anell al dit! Moltes gràcies a tot per l'ajuda i sento la meva ignorància!!!! Fins un altre problema!!!! jejejej

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

