---
title: "Problemas con SB Live (emu10k1) me hacen trasnochar"
date: 2007-07-08
forum: Argentina Team
---

### Post by SLA_leandrin on 2007-07-08
Buenas noches muchachos... estoy renegando malamente con la placa SB live! que corre con emu10k1 en ALSA... o por lo menos debería correr...

Hacía unas semanas me había resignado a usar la placa onboard de mi PC, que es lamentable, pero hoy me decidí a hacer andar la SB live, sin resultados a la vista.

He seguido paso a paso la guía "Comprehensive Sound Problem Solutions Guide v0.5e", que está muy buena pero no pude solucionar nada...

Puse un par de posts por ahi pero no me respondieron aún, en una de esas como tengo el ubuntu en español no entienden el resultado del make:

En este thread está:

[http://ubuntuforums.org/showthread.php?t=495309]("http://ubuntuforums.org/showthread.php?t=495309")

no puedo compilar desde el source y no tengo los suficientes conocimientos para deducir yo mismo porque, por eso les pido ayuda!!!

Por las dudas:

```
leandro@leandro:/var/cache/modass$ sudo modprobe snd-emu10k1
FATAL: Module snd_emu10k1 not found.
FATAL: Error running install command for snd_emu10k1

```

```
leandro@leandro:/var/cache/modass$ sudo lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
        Flags: bus master, medium devsel, latency 32
        Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [c0] AGP version 2.0

00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Flags: bus master, fast devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
        Flags: bus master, medium devsel, latency 0

00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at cc00 [size=256]
        Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at cffc0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2

00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]

00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] Onboard USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at cffff000 (32-bit, non-prefetchable) [size=4K]

00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Silicon Integrated Systems [SiS] AC'97 Modem Controller
        Flags: medium devsel, IRQ 11
        I/O ports at d400 [size=256]
        I/O ports at d000 [size=128]
        Capabilities: [48] Power Management version 2

00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, VGA palette snoop, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: cde00000-cfefffff
        Prefetchable memory behind bridge: bdc00000-cdcfffff

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs Unknown device 8066
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at c800 [size=32]
        Capabilities: [dc] Power Management version 1

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at d800 [size=8]
        Capabilities: [dc] Power Management version 1

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 5
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at cfef0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 2.
```

```
leandro@leandro:/var/cache/modass$ aplay -l
aplay: device_list:222: no se encontraron tarjetas de sonido...
```

Gracias muchachos,
Saludos desde Salta...

---

### Post by MeduZa on 2007-07-08
hola, yo hice lo mismo que vos, desabilite la onboard y saque mi SB live 5.1 del cajon que le pasa el trapo mal a la otra,
lo que tenes que hacer es esto:

1) bajate los alsa (drivers de sonido pal linux) de alguno de los siguientes link en esta pagina:
[links]("http://www.alsa-project.org/download.php")

[aca te dejo el link de uno que me parecio el mejor (para mi)]("ftp://ftp.silug.org/pub/alsa/driver/alsa-driver-1.0.14rc4.tar.bz2")

2) descomprimis y te paras en la carpeta y ejecutas estas lineas desde consola:

./configure --with-cards=emu10k1 --with-sequencer=yes [COLOR="Red"]--with-oss=yes[/COLOR];

(lo que esta en rojo ponelo si queresm si no da igual pero es para compativilidad con oss)

despues de eso:

make

sudo make install

y listo te tendria que andar todo.

Si por casualidad no te compila porque te faltan librerias dependientes lo que tenes que hacer es leer el nombre y con el synactic installar el lib que te falte, yo te queria pasar el mio pero desde que compile el kernel con los drivers adentro cuando trato de compilar el alsa me dice:
configure: error: You have built-in ALSA in your kernel.
Si alguien sabe algun comando para saltear eso yo te paso el deb para i386 que capas te ande
Suerte

---

### Post by SLA_leandrin on 2007-07-08
Gracias Meduza, he probado tus consejos; 

Se configura y compila correctamente el driver con los comandos
./configure...
sudo make
sudo make install

Al final del install me larga este mensaje:
```

.
.
.
.
/sbin/depmod -a 2.6.20-16-generic
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

```

O sea, por lo que entiendo aparentemente está todo bien, pero cuando quiero cargar el módulo emu10k1 en el kernell con

sudo modprobe snd-emu10k1

me da el siguiente error:

```
leandro@leandro:~/src/alsa/alsa-driver-1.0.14rc4$ sudo modprobe snd-emu10k1
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Invalid argument
FATAL: Error running install command for snd_emu10k1

```

Y estoy en *****, no se que mas hacer...
Por las dudas, que kernell tenés vos??

Saludos..

---

### Post by MeduZa on 2007-07-08
el comando es:
modprobe snd-card-emu10k1

> WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.
eso te dice que cuidado que por defecto todos los controles estan en mute (osea apagados) los tenes que prender, una vez que haces eso no creo que tengas que cargar el modulo, yo creo que solo reinicie la pc o no me acuerdo pero andaba.

yo tengo el 
Linux 2.6.21.5 #2 SMP Wed Jul 4 14:18:49 EDT 2007 i686 GNU/Linux

fijate si abajo al lado de la hora te aparece el indicador de volumen, si te aparece, hace doble click ahi y activa todo lo que necesites.
otra forma es ir a consula y poner: alsamixer y hacer lo mismo.

proba eso y decime, mientras tanto leo a ver si encuentro algo que me olvidó de decirte

suerte

PD: cuando empece tenia los mismos "problemas" que vos, despues me di cuenta que no eran problemas sino que era que necesitaba leer un poco mas o ayuda para entenderlo, despues mas adelante todo te sale al toke y tenes una idea mas clara de donde esta todo, yo llego a desesperarme mal jajajaja leer 20hs un tuturial, pero lo mejor es preguntar aca que normalmente esplicamos como se hace! :)

---

### Post by SLA_leandrin on 2007-07-08
Bueno, siguiendo con este tema;

Luego de reiniciar la PC:

```
leandro@leandro:~$ sudo modprobe snd-card-emu10k1
Password:
FATAL: Module snd_card_emu10k1 not found.

```

ó

```
leandro@leandro:~$ sudo modprobe snd-emu10k1
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Invalid argument

```

Tengo entendido que éste último es el que debería andar, ya que si escribís sudo modprobe snd- y apretás tab me dá estas opciones;

```
leandro@leandro:~$ sudo modprobe snd-
snd-ac97-codec      snd-page-alloc      snd-seq-midi
snd-bt-sco          snd-pcm             snd-seq-midi-emul
snd-emu10k1         snd-pcm-oss         snd-seq-midi-event
snd-emu10k1-synth   snd-rawmidi         snd-seq-oss
snd-emux-synth      snd-rtctimer        snd-seq-virmidi
snd-hwdep           snd-seq             snd-timer
snd-mixer-oss       snd-seq-device      snd-util-mem

```

y alsamixer:

```
leandro@leandro:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

Así es, hay que seguir probando y aprendiendo... por ahora no results!!:confused::confused:

---

