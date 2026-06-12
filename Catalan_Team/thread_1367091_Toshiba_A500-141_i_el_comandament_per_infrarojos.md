---
title: "Toshiba A500-141 i el comandament per infrarojos"
date: 2009-12-29
forum: Catalan Team
---

### Post by akyra on 2009-12-29
Hola de nou,
Bé, també estic intentant configurar el petit comandament a distància per infrarrojos que porta el portatil i pel moment no obtinc resultats.

He instal·lat el LIRC i el LIRC-X. El meu comandament no està soportat i haig de fer una configuració manual. El que faig és :

> 
sudo modprobe lirc_serial

i després

sudo irrecord -d /dev/lirc0 lircd.conf


i el resultat que tinc és:
> Press RETURN now to start recording.
irrecord: no data for 10 secs, aborting
irrecord: gap not found, can't continue


Què més puc fer?

Gracies

---

### Post by akyra on 2010-01-03
Bé, he anat navegant i he trobat que el receptor d'infrarojos d'aquest model de Toshiba no està soportat en Linux.

Concretament es tracta d'un Remote controller (RC6ir), i un receptor ENE CIR Receiver, model ENE0200.

He obert un bug ha Launchpad, i a veure si em diuen alguna cosa.

Si algú està interesat li deixo l'enllaç del bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501923](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501923)

Us mantindré informats.

Adeu

---

### Post by Samuels on 2010-04-03
Perdoneu però fa molt temps que no practique el català. Vaig parlar amb Maxim Levitsky (el autor del driver ene0100) i la solució no va ser molt difícil. L'última versió del cvs de lirc suporta el ene0200. Vaig escriure aquestes instruccions per fer-ho funcionar en ubuntu, ho sento però no vaig tenir temps de traduir-les.


Mando a distancia:

[SIZE="3"]**1)Desinstalar lirc y sus módulos si estuvieran instalados**[/SIZE]

```
sudo apt-get --purge remove lirc
sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/lirc
```

[SIZE="3"]**2)Instalar las fuentes del kernel y paquetes para compilar**[/SIZE]
```
sudo apt-get install linux-sources build-essentials gcc-3.4 libtool help2man cvs linux-headers-generic
sudo apt-get remove automake1.4
sudo apt-get install automake1.9
```

[SIZE="3"]**3)Descomprimir las fuentes del kernel y crear un enlace simbolico**[/SIZE]

(cambiar el nombre del tar.bz2 por la versión correcta)
```
cd /usr/src
sudo tar xvfj linux-source-2.6.31.tar.bz2
sudo ln -s linux-source-2.6.31 linux
```

[SIZE="3"]**4)Instalar paquetes adicionales para poder descargar y compilar la última versión disponible de Lirc**[/SIZE]
```
sudo apt-get install libtool help2man cvs
sudo apt-get remove automake1.4
sudo apt-get install automake1.9
```

[SIZE="3"]**5)Descargar LIRC desde el repositorio (cuando pida password simplemente darle a return)**[/SIZE]
```
cd
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
cvs update
```

[SIZE="3"]**6)Configurar LIRC**[/SIZE]
```
./autogen.sh
./setup.sh

```

Tenemos que elegir la opción 6 IRDA/Cir Hardware > 4 ENE KB3926 B/C/D (ENE0100) CIR Port

Luego elegimos "Save configuration and Run Configure" (Puede tardar un poco)
 
[SIZE="3"]**7) Compilamos e instalamos LIRC**[/SIZE]
```
make
sudo make install

```

[SIZE="3"]**8)Configurar el sistema para que se active automáticamente el receptor de infrarojos al reiniciar**[/SIZE]

```
sudo gedit /etc/init.d/lirc
```

Copiamos el siguiente texto, guardamos y cerramos gedit.

```
#!/bin/bash
### BEGIN INIT INFO
# Provides:          lircrc
# Required-Start:    $local_fs $syslog
# Required-Stop:     $local_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Script para ejecutar lirc para el driver ene0100, ene0200 y ene0201.
# Description:       Lirc permite utilizar el mando a distancia por infrarojos.
### END INIT INFO

case "$1" in
  start)
    echo -n "Iniciando lirc..."
    ARGS=' --output=/var/run/lirc/lircd --permission=666 --device=/dev/lirc /etc/lirc/lircd.conf'
    if [ ! -e /dev/lirc ]
    then
        /bin/mknod /dev/lirc c 61 0
    fi
    if [ ! -d /var/run/lirc ]
    then
        mkdir /var/run/lirc
    fi
    start-stop-daemon --start --exec /usr/local/sbin/lircd -- $ARGS
    echo " Hecho"
    ;;
  stop)
    echo -n "Parando lirc..."
    start-stop-daemon --stop --exec /usr/local/sbin/lircd
    echo " Hecho"
    ;;
  *)
    echo "Modo de uso: /etc/init.d/lircd {start|stop}"
    exit 1
esac

exit 0
```


Damos permisos al script que acabamos de crear

```
sudo chmod 775 /etc/init.d/lirc

```
Lo activamos para que se inicie siempre
```
sudo update-rc.d lirc defaults
```

[SIZE="3"]**9)Configurar mando a distancia**[/SIZE]
Hay que desactivar lirc para poder utilizar irrecord
```
sudo /etc/init.d/lirc stop
sudo irrecord --disable-namespace lircd.conf
```

Seguimos las instrucciones para configurar al mando a distancia (a veces hay que intentarlo varias veces para que lo detecte bien)

Una vez hecho copiamos el archivo de configuración al directorio correcto

```
sudo cp lircd.conf /etc/lirc/lircd.conf
```

**[COLOR="Red"](Añadido)[/COLOR]**
Este es el lircd.conf para mi mando a distancia (IRC6 Media Center Modelo G83008A110). En principio debería funcionar para otros mandos tipo Windows Media Center de Toshiba
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.7-CVS(default) on Sat Apr  3 11:49:40 2010
#
# contributed by Sami Racho
#
# brand: Toshiba
# model no. of remote control:  G83C0008A110 
# devices being controlled by this remote: Thosiba Qosmio F50-10Q (ene0200 ir receiver)
#

begin remote

  name        Toshiba_G83C0008A110
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

	Blue	      0x00007ba1
	Yellow	      0x00007ba2
	Green	      0x00007ba3
	Red	      0x00007ba4
	Teletext      0x00007ba5

        RecTV         0x00007bb7
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote

```

[SIZE="3"]**10) Configurar programas para que usen el mando a distancia**[/SIZE]
Dentro de la carpeta home del usuario (en mi caso /home/sam) hay que crear un archivo que se llame .lircrc

La forma de configurarla es la siguiente, en "button" hay que poner el nombre del botón que hayamos usado durante la configuración del mando mediante irrecorder.
Por ejemplo, si al botón de volumen lo hemos llamado "volumen+" la configuración quedaría de la siguiente manera

begin
     button = volumen+
     prog = mplayer
     config = volume 1
     repeat = 1
end


Esta lista no está configurada, la pongo con los comandos para Rythmbox, mplayer y VLC.
Hay que editarla para hacer coincidir los nombres de los botones con los que se hayan utilizado durante la configuración del mando mediante irrecord

```
###################
# mplayer
###################

begin
     button = VOL+
     prog = mplayer
     config = volume 1
     repeat = 1
end
begin
     button = VOL-
     prog = mplayer
     config = volume -1
     repeat = 1
end
begin
     button = MUTE
     prog = mplayer
     config = pause
end
begin
     button = CH+
     prog = mplayer
     config = pt_step 1
end
begin
     button = CH-
     prog = mplayer
     config = pt_step -1
end
begin
     button = FULL_SCREEN
     prog = mplayer
     config = vo_fullscreen
end
begin
     button = 1
     prog = mplayer
     config = seek -10
end
begin
     button = 4
     prog = mplayer
     config = seek -60
end
begin
     button = 3
     prog = mplayer
     config = seek 10
end
begin
     button = 6
     prog = mplayer
     config = seek 60
end
#begin
#     button = MINIMIZE
#     prog = mplayer
#     config = quit
#end

begin
     button = 7
     prog = mplayer
     config = audio_delay +0.1
end
begin
     button = 9
     prog = mplayer
     config = audio_delay -0.1
end

###################
# Rhythmbox
###################

begin
        prog = Rhythmbox
        button = arriba
        config = playpause
end
begin
        prog = Rhythmbox
        button = abajo
        config = playpause
end
begin
        prog = Rhythmbox
        button = izquierda
        config = stop
end
begin
        prog = Rhythmbox
        button = derecha
        config = seek_forward
end
begin
        prog = Rhythmbox
        button = Slow
        config = seek_backward
end
begin
        prog = Rhythmbox
        button = Next
        config = next
end
begin
        prog = Rhythmbox
        button = Previous
        config = previous
end

###################
# Irexec
###################
#ejemplo uso irexec con un script acpi
#begin
#  prog=irexec
#  button=mute
#  config=/etc/acpi/mutebtn.sh
#end

###################
# VLC
###################


# Show OSD 
begin 
prog = vlc 
button = MENU 
config = osd 
end 

# Pause playback 
begin 
prog = vlc 
button = PAUSE 
config = key-play-pause 
end 

# Play 
begin 
prog = vlc 
button = PLAY 
config = key-play 
end 

begin 
prog = vlc 
button = Rewind 
config = key-jump-short 
end 

begin 
prog = vlc 
button = Forward 
config = key-faster 
end 

# Stop playback and exit 
begin 
prog = vlc 
button = STOP 
config = key-quit 
end 

# Volume Down 
begin 
prog = vlc 
button = VolDown 
repeat = 3 
config = key-vol-down 
end 

# Volume Up 
begin 
prog = vlc 
button = VolUp 
repeat = 3 
config = key-vol-up 
end 

# Faster 
begin 
prog = vlc 
button = ChanUp 
config = key-faster 
end 

# Slower 
begin 
prog = vlc 
button = ChanDown 
config = key-slower 
end 

# Mute 
begin 
prog = vlc 
button = Mute 
config = key-vol-mute 
end 

# Seek back 10 seconds 
begin 
prog = vlc 
button = One 
repeat = 3 
config = key-jump-short 
end 

# Seek forward 10 seconds 
begin 
prog = vlc 
button = Three 
repeat = 3 
config = key-jump+short 
end 

# Quit 
begin 
prog = vlc 
button = BACK 
config = key-quit 
end 

begin 
prog = vlc 
button = EXIT 
config = key-quit 
end 

begin 
prog = vlc 
button = LiveTV 
repeat = 1 
config = key-quit 
end 

begin 
prog = vlc 
button = RecordedTV 
repeat = 1 
config = key-quit 
end 

begin 
prog = vlc 
button = Guide 
repeat = 1 
config = key-quit 
end 

# Seek forward 1 minute 
begin 
prog = vlc 
button = Skip 
repeat = 3 
config = key-jump+medium 
end 

# Seek backward 1 minute 
begin 
prog = vlc 
button = Replay 
repeat = 3 
config = key-jump-medium 
end 

# Seek forward 5 minutes 
begin 
prog = vlc 
button = Six 
repeat = 3 
config = key-jump+long 
end 

# Seek backward 5 minutes 
begin 
prog = vlc 
button = Four 
repeat = 3 
config = key-jump-long 
end 

# Position - shows where you are in the video 
begin 
prog = vlc 
button = More 
config = key-position 
end 

# Subtitles 
begin 
prog = vlc 
button = Enter 
config = key-subtitle-track 
end 

# Snapshots 
begin 
prog = vlc 
button = Record 
config = key-snapshot 
end 

# Audio Sync'ing 
# Audio Delay UP 
begin 
prog = vlc 
button = Star 
config = key-audiodelay-up 
end 

# Audio Delay DOWN 
begin 
prog = vlc 
button = Hash 
config = key-audiodelay-down 
end 

# Navigation Menu Up 
begin 
prog = vlc 
button = Up 
repeat = 3 
config = key-nav-up 
end 

# Navigation Menu Down 
begin 
prog = vlc 
button = Down 
repeat = 3 
config = key-nav-down 
end 

# Navigation Menu Right 
begin 
prog = vlc 
button = Right 
repeat = 3 
config = key-nav-right 
end 

# Navigation Menu Left 
begin 
prog = vlc 
button = Left 
repeat = 3 
config = key-nav-left 
end 

# Navigation Select 
begin 
prog = vlc 
button = Ok 
repeat = 3 
config = key-nav-activate 
end 

#DVDMenu 
begin 
prog = vlc 
button = DVDMenu 
config = key-disc-menu 
end 
```


[SIZE="3"]**11)Configurar irexec**[/SIZE]
Irexec permite ejecutar comandos o scripts asociándolos a botones del mando a distancia

```
sudo gedit /etc/init.d/ierexec
```

Pegamos el siguiente script

```
#!/bin/bash
### BEGIN INIT INFO
# Provides:          irexec
# Required-Start:    $local_fs $syslog
# Required-Stop:     $local_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Script para ejecutar irexec.
# Description:       Irexec permite ejecutar comandos mediante lirc.
### END INIT INFO

#ejemplo uso irexec con un script acpi
#esto debe añadirse en el archivo .lircrc dentro de la carpeta home del usuario
#begin
#  prog=irexec
#  button=mute
#  config=/etc/acpi/mutebtn.sh
#end


killall -q irexec;
irexec&
```

Le damos permisos de ejecución
```
sudo chmod 775 /etc/init.d/irexec
```


Lo añadimos para que se ejecute al inicio
```
sudo update-rc.d irexec defaults
```

---

### Post by papapep on 2010-04-04
Moltes gràcies pel teu ajut, Samuels ;)

---

### Post by akyra on 2010-05-02
Hola, fins avui no havia vist aquesta replica!!
He estat seguint aquestes instruccions, bé pel moment m'he saltat el compilar el kernel (em donava un error de no trobar el linux-sources).
Tot el següent ha anat bé fins la instrucció:./setup, surt l'error:
> jordi@jordi-ubuntu:~/lirc$ ./setup.sh
dialog not found!

Saps que pot ser?

Moltes gracies.

---

### Post by Samuels on 2010-08-30
Et falta dialog.

sudo apt-get install dialog

---

### Post by akyra on 2010-09-06
Ostia !!!!
Ni em vaig imaginar en cap moment que Dialog fos un programa, pensava que li faltava alguna altre cosa.

Bé, ja l'instal·lat sense cap problema.

Des d'el juliol que estic en contacte amb en Maxim Levitsky perquà ha fet una nova versió del driver, ja que la versió que tinc jo en el meu comandament es molt nova, i em va dir que per això no funcionava amb el driver que va fer.

Espero aquesta setmana provar el darrer patch que ha fet a veure si funciona.

Gracies.

---

