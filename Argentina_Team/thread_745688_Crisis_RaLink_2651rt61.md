---
title: "Crisis: RaLink 2651/rt61"
date: 2008-04-04
forum: Argentina Team
---

### Post by Mauro22 on 2008-04-04
Buenas!!


Un problema!!


Hasta ahora venia usando mi adaptador USB wireless pero al parecer murio. Se cae cada 1 o 2 minutos.


Compre una Edimax que tiene el chip:

RaLink 2651 rt61


A veces anda a veces no y cuando lo hace, va a la increible velocidad de: 300 Bits por segundo (0.3Kbps) 



San google me esta fallando, ndiswrapper da error. 
Baje unos drivers de la pagina de ralink y logro esa velocidad.




Alguien tiene esta placa ??
Alguien que le sobre una mano para darmela ??

OS: Ubuntu hardy heron 32 bits

:guitar:

---

### Post by odiseo77 on 2008-04-04
Hola. No te puedo dar una ayuda precisa porque no uso una tarjeta basada en el chipset rt61, sino una rt2500 (y tampoco uso Hardy), pero he probado y configurado la rt2500 en varias distros, asi que en algo puedo ayudarte ;)

OK, si estás en Hardy me imagino que estarás usando el kernel 2.6.24, que ya trae soporte nativo (aunque defectuoso) para las tarjetas con chipsets rt*. ¿Podrías postear los resultados de los siguientes comandos?:

```
uname -r
```

Si la tarjeta es usb:
```
lsusb
```

Si es pci:
```
lspci
```

```
lsmod | grep -i rt
```

```
sudo lshw -C network
```

Saludos :)

---

### Post by Mauro22 on 2008-04-04
Gracias por responder! Paso tu pedido:

uname -r
> 2.6.24-14-genericlspci
> 
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
**00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI**
00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

lsmod | grep -i rt
> 
exportfs                7040  1 nfsd
snd_mpu401_uart         9600  1 snd_via82xx
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
gameport               16776  2 snd_via82xx,analog
[B]rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci[/B]
rfkill                  8208  1 **rt2x00lib**
snd                    54660  18 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,saa7134_alsa,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              171016  4 rc80211_simple,**rt61pci,rt2x00pci,rt2x00lib**
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
input_polldev           5896  1 **rt2x00lib**
crc_itu_t               3072  1 **rt2x00lib**
eeprom_93cx6            3200  1 **rt61pci**
agpgart                35016  2 nvidia,amd64_agp

sudo lshw -C network
> 
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:42:d9:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.104 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g

Ahi esta todo. igual te comento que desde synaptic instalé algo como rt2500 o algo asi. ahora anda pero muy lento. Lo corrobe con windows y anda a 1/4 de velocidad.

Te marque en negro lo que me suena conocido!!

EDIT 2:
Con este kernel: 2.6.22-14-generic anda el video e internet anda lento
Con este kernel: 2.6.24-14-generic no anda el video pero internet va un poco mas rapido

mil gracias!

---

### Post by odiseo77 on 2008-04-04
No es necesario que instales el paquete rt2500-* porque ese es el driver para la rt2500 y tu estás usando una rt61. 

No sé qué tal funcionen estos pasos en Hardy con la rt61, pero esto fue más o menos lo que yo hice en Gutsy con la rt2500. Para empezar, vamos a instalar los headers del kernel que estás usando y el paquete build-essential, que necesitarás luego para compilar el driver:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Ahora hay que poner en lista negra el módulo del kernel que viene por defecto en Hardy para esa tarjeta, de manera que no se cargue. Para esto, abres el archivo /etc/modprobe.d/blacklist y añades las siguientes líneas al final:

```
blacklist rt61pci
blacklist rt2x00lib
blacklist rt2x00pci
```

El siguiente paso sería remover el módulo rt61pci del kernel que estás usando:

```
sudo modprobe -r rt61pci
```

Luego descargas el driver apropiado desde [este enlace]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz"). Y ahora viene la parte mas divertida: la compilación del driver:

```
tar zxvf rt61-cvs-daily.tar.gz
cd rt61-cvs-2008*/Module
make
sudo make install
```

Si todo va bien, no deberia haber ningún error. Ahora cargas el modulo rt61 en el kernel de la siguiente manera:

```
sudo modprobe rt61
```

Y luego configuras tu conexión de la manera acostumbrada.

Son un montón de pasos y puede resultar tedioso, pero espero que te funcione. (Las instrucciones generales están sacadas de [aquí]("http://ubuntuforums.org/showthread.php?t=584657")).

Saludos :)

Acabo de leer el el archivo README que esta tarjeta necesita un firmware (incluido en el driver), quizás tengas que seguir algunos pasos extra para poner a funcionar la tarjeta. Lee en el archivo README la sección "Firmware files" y cualquier duda avisas.

---

### Post by odiseo77 on 2008-04-04
> EDIT 2:
Con este kernel: 2.6.22-14-generic anda el video e internet anda lento
Con este kernel: 2.6.24-14-generic no anda el video pero internet va un poco mas rapido

No había visto lo ultimo que añadiste después. Bueno, si puedes hacer que te funcione el entorno gráfico en el kernel 2.6.24-14 sería lo ideal. Probablemente no tienes el driver de tu tarjeta de video instalado para ese kernel (prueba iniciando con ese kernel, luego vas a una terminal virtual con ctrl-alt-F2 e y lo inistalas con apt-get o aptitude desde alli) :-)

---

### Post by Mauro22 on 2008-04-05
Gracias, Odiseo77 pero sigue sin funcionar....

Se queda en conectando... desde win2 anda muy bien y desde mandriva excelente.

Hago todo, no hay errores ni nada. Pero no conecta.


Parece que hardy heron no es lo prometido. (Hay que ver porque tengo un update de 200 mb que no puedo descargar)


Pero sin duda por ahora me quedo con mandriva. Me ha reconocido TODO sin hacer nada.

---

### Post by odiseo77 on 2008-04-05
Qué mal que no te haya funcionado. Por lo que veo [aquí]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660"), parece ser un problema común de las tarjetas con chipset Ralink en Gutsy y Hardy (sin embargo, la mia -rt2500- funciona a la perfección depsues de poner en lista negra el driver que viene en Gutsy e instalar el driver "anticuado", como lo llaman en la página de serialmonkey. 

Lo que te puedo sugerir es que pruebes con [wicd]("http://wicd.sourceforge.net/") o [rutilt]("http://cbbk.free.fr/bonrom/") a ver si alguno de los dos te da resultados (rutilt está creado especificamente para tarjetas ralink, asi que podría funcionar).

También puedes pegar aquí el error que recibes al tratar de conectar; no sé mucho de redes, pero quizas otra persona pueda diagnosticar mejor el problema.

Saludos.

---

