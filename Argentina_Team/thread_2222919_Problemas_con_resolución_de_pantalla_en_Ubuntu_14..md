---
title: "Problemas con resolución de pantalla en Ubuntu 14.04"
date: 2014-05-08
forum: Argentina Team
---

### Post by tuliobalcaldi on 2014-05-08
Hola a todos, mi nombre es Tulio y escribo desde Bariloche.
Hace muchos años postié alguna que otra vez, dado que estuve usando por un buen tiempo Ubuntu 08.04 a la perfección en la notebook que tenía en ese momento, una Dell Latitude D630.
Ahora vuelvo, después de muchos años, a tocar Ubuntu, esta vez desde una vieja (pero noble) Olivetti serie 520. Instalé (sin probarlo desde el cd) el Ubuntu 14.04 y me corre a la perfección, con una salvedad: no puedo modificar la resolución de pantalla, quedando la misma en 640x480. 
Intenté modificarla siguiendo lo que se menciona aca: [http://blog.desdelinux.net/no-te-aparecen-las-resoluciones-que-quieres-en-la-configuracion-de-pantalla-de-ubuntu/](http://blog.desdelinux.net/no-te-aparecen-las-resoluciones-que-quieres-en-la-configuracion-de-pantalla-de-ubuntu/) sin embargo, no hubo caso. Tampoco encontré una solución en ningun lugar.
Tienen idea cómo modificarla? Recomiendan volver a una versión anterior de Ubuntu? Dado que no se qué hacer.

Aguardo respuesta!

Saludos a todos!

---

### Post by papibe on 2014-05-08
Que tal tuliobalcaldi,

Puedes abrir un terminal, ejecutar estos comandos y responder con los resultados (puedes copiar y pegar el texto del terminal)?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'

xrandr -q 

xrandr -q --q1

[ -f /etc/X11/xorg.conf ] && cat -n /etc/X11/xorg.conf
```
Saludos.

---

### Post by tuliobalcaldi on 2014-05-08
Papibe, gracias por tu respuesta!
Esto es lo que salió al copiar todo el comando que me copiaste:

tulio@tulio-laptop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
	Subsystem: Elitegroup Computer Systems Device [1019:5050]
tulio@tulio-laptop:~$ 
tulio@tulio-laptop:~$ lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'
tulio@tulio-laptop:~$ 
tulio@tulio-laptop:~$ xrandr -q 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
   640x480        73.0* 
tulio@tulio-laptop:~$ 
tulio@tulio-laptop:~$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0    640 x 480    ( 169mm x 127mm )  *73  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
tulio@tulio-laptop:~$ 
tulio@tulio-laptop:~$ [ -f /etc/X11/xorg.conf ] && cat -n /etc/X11/xorg.conf

---

### Post by papibe on 2014-05-08
Gracias.

Solamente se ve la resolución 640x480 :(

Esto está pasando bastante seguido cuando uno conecta el monitor con un cable VGA. Por casualidad lo puedes conectar con un cable DVI o HDMI?

Otra pregunta, durante la instalación también estaba en baja resolución?

Saludos.

---

### Post by tuliobalcaldi on 2014-05-08
Es una laptop :( por ende no lo tengo conectado con ningún cable.
Durante la instalación se veía de la misma manera, pero pensé que era algo normal dado que cuando instalé Windows se veía igual hasta actualizar drivers o bien hasta setearla correctamente.
Qué opciones me recomendás? Volver a alguna versión anterior?

---

### Post by papibe on 2014-05-08
Veamos si podemos obtener más información del monitor usando el paquete read-edid.

Primero instala el paquete:
```
sudo apt-get update

sudo apt-get install read-edid
```
Luego ejecuta esto y postea el resultado:
```
sudo bash -c  'get-edid | parse-edid'
```
Saludos.

---

### Post by tuliobalcaldi on 2014-05-08
Esto es lo que me dice después de haber instalado lo que tenía que descargar

tulio@tulio-laptop:~$ sudo bash -c 'get-edid | parse-edid'
This is read-edid version 3.0.1. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0xc2bf0 "SiS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
Partial Read... Try again
I'm sorry nothing was successful. Maybe try some other arguments
if you played with them, or send an email to Matthew Kern <pyrophobicman@gmail.com>.

Muchas gracias!

---

### Post by papibe on 2014-05-08
No conseguimos información.

Tratemos otra cosa. Me gustaría ver el contenido de este archivo:
```
/var/log/Xorg.0.log
```
Por favor pégalo aquí: [paste.ubuntu.com]("http://paste.ubuntu.com/"), y después publica el link al archivo.

Saludos.

---

### Post by tuliobalcaldi on 2014-05-09
Pongo ese comando en terminal y luego lo pego en ese link?

---

### Post by papibe on 2014-05-09
No exactamente.

Abre el archivo:
```
gedit /var/log/Xorg.0.log
```
Luego seleccionas todo el texto, lo copias y lo pegas en la página: [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

Una vez que pegas el texto, presiona el botón 'Paste'. Una vez que se termine de procesar, copia el URL de la página nueva y lo publicas en una respuesta nueva, para que a través del link podamos ver el contenido del arvhivo.

Saludos.

---

### Post by tuliobalcaldi on 2014-05-09
Este es el enlace:

[http://pastebin.ubuntu.com/7424124/](http://pastebin.ubuntu.com/7424124/)

Mil disculpas por la demora en la respuesta, recién me siento en la notebook.
Muchas gracias!!

---

### Post by papibe on 2014-05-13
Hay varios errores en ese log. Este es el que más me preocupa:
```
(EE) open /dev/dri/card0: No such file or directory
```
He leido varios threads similares (en inglés) y si bien es cierto que había un bug en versiones anteriores, 14.04 debería dar buen soporte a tu tarjeta g&#341;afica. Voy a pedir ayuda a un usuario que sabe un poco más y te contesto en par de días.

Saludos.

---

### Post by papibe on 2014-05-15
Probemos esto.

Crea un archivo que se llame xorg.conf con este contenido (asegúrate de copiar todo el texto):
```

Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
    Busid "PCI:1:0:0"
    Driver "vesa"
    Screen 0
        Option "UseFBDev" "true"
        Option "DPMS"
        Option "ShadowFB"
        Option "MaxXFBMem"
        VideoRam 262016
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
        Option "backingstore" "true"
        Option "AddARGBGLXVisuals" "True"

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    HorizSync 20-107
        VertRefresh 50-185
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
    EndSubSection
EndSection

Section "Module"
    Load "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "GLcore"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "int10"
    Load "vbe"
    Load "speedo"
    Load "record"
EndSection

Section "DRI"
        Mode 0666
EndSection
```
Después cópialo en /etc/X11:
```
sudo cp -v xorg.conf /etc/X11/
```
Finalmente, resetea tu laptop.

Cuantanos como te va con esta prueba.
Saludos.

---

### Post by tuliobalcaldi on 2014-05-15
Excelente, gracias por tu respuesta!
Preguntonta: el archivo lo creo con libreoffice? dónde lo guardo originalmente, en una carpeta de documentos propios y después abro la Terminal y lo copio?

---

### Post by papibe on 2014-05-15
No uses Libreoffice.

El archivo tiene que ser un archivo de texto. Busca 'Text editor', o 'Editor' en el dashboard. También puedes buscar 'gedit'.

El archivo lo puedes guardar en cualquier directorio, pero si lo salvas en tu 'Home', va a resultar más fácil cuando ejecutes el comando para copiar.

Saludos.

---

### Post by tuliobalcaldi on 2014-05-15
GRACIAS!!!! Ahora me aparecen cuatro resoluciónes (640x480, 800x600, 1024x768 y 1280x768), lo selecciono pero no puedo llegar al botón "Aplicar", porque intento correr la pantalla pero me vuelve al mismo lugar.
Hay algún comando con el cual pueda llegar a confirmar el cambio? Voy aprentando la tabulación pero no hay caso!!

---

### Post by papibe on 2014-05-15
Prueba si uno de estos comandos funciona:
```
xrandr --output default --mode "1280x768@60"
xrandr --output default --mode "1280x768"
xrandr --output default --mode "1280x768" --rate 60
```
Avisanos como te va con eso.
Saludos.

---

### Post by tuliobalcaldi on 2014-05-20
Recien me siento en la compu, y al probar me salen estos errores>

tulio@tulio-laptop:~$ xrandr --output default --mode "1280x768@60"
xrandr: cannot find mode 1280x768@60
tulio@tulio-laptop:~$ xrandr --output default --mode "1280x768"
xrandr: Failed to get size of gamma for output default
tulio@tulio-laptop:~$ xrandr --output default --mode "1280x768" --rate 60
xrandr: Failed to get size of gamma for output default
tulio@tulio-laptop:~$

---

### Post by andres15 on 2014-10-03
Buenas, realicé los pasos que explicaste, pero a la hora de reiniciar mi laptop, me salió un mensaje que decía que el sistema esta corriendo en un modo de gráficos bajo. Mi pantalla, tarjeta gráfica y configuraciones del dispositivo de entrada no pueden ser detectados correctamente. Y que necesitaré configurarlos yo mismo . . . Y luego me dan 4 opciones: 
Correr en un modo de gráficos bajo sólo por una sesión.
Reconfigurar gráficos
Solucionar el error
Salir a logearme por consola

Pero probando, todos me dejan la compu en una pantalla tipo consola y no hace nada. Ayuda por favor!!!

---

