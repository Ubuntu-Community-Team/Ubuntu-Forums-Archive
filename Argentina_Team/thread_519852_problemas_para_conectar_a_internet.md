---
title: "problemas para conectar a internet"
date: 2007-08-07
forum: Argentina Team
---

### Post by ccp on 2007-08-07
hola estimados,
vamos por la segunda pc con Ubuntu y tenemos nuevos problemas.
Esta vez creo que el problema se debe a que la pc tiene una placa de red onboard que dejó de funcionar un día de tormenta (yo vivo en el campoy pasan esas cosas...). Luego, le puse otra placa que andaba bien bajo win XP.
Hice la migración a Ubuntu hace unos días y al instalar me pareció que conectó a internet para bajar paquetes de español, pero una vez finalizada la instalación de Ubuntu FF no me pude conectar más.
Internet está provisto en este lugar (mi oficina) mediante Banda ancha de speedy, y conectada a un router D-link que provee a las otras pcs y una mac.
Supongo que tal vez Ubuntu trata de conectar por la placa que no anda y ese es el problema, o que yo lo configuré mal al instalar.
Paso el contenido de dos archivos que supongo pueden ser de utilidad para ver la situación
ifconfig y lspci

```

claudio@ubuntuserv:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:AD:70:48:B8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:952990 (930.6 KiB)  TX bytes:2034 (1.9 KiB)
          Interrupt:12 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:C0:DF:0D:C9:AD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45288 (44.2 KiB)  TX bytes:45288 (44.2 KiB)

usb0      Link encap:Ethernet  HWaddr 62:B7:C3:D0:40:E0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:986 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:98 (98.0 b)

usb0:avah Link encap:Ethernet  HWaddr 62:B7:C3:D0:40:E0  
          inet addr:169.254.10.14  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


************************

claudio@ubuntuserv:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:02.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)


```

Ni idea de por donde agarrar.
Gracias por la ayuda
CCP

---

### Post by aceki on 2007-08-07
a mi me paso lo mismo, consejo tonto (yo pienso que es tonto), desabili ta la placa de red desde el bios (o jumper en su defecto en el mother), y ahi fijate que placa te toma, se que hay un comando en unix que te dice los datos de las placa eth, por ahi con eso sacas cual plata te esta tomando

---

### Post by ccp on 2007-08-07
Hola, gracias por responder.
Mi idea era ver si podía hacer algo desde la terminal, sin tener que meter mano en el hardware (ya que me parece más riesgoso cuando uno no sabe).
Lamentablemente no se cómo deshabilitar la placa desde la línea de comandos, si es que se puede.
ABrazo
CCP

---

### Post by zspikes on 2007-08-07
con el comando ifconfig te tira todos los datos de la placa/s de red
y el comando lspci te lista todos los dispositivos q estan conectados por pci. (con el comando ls... podes ver lo q hay conectado en cualquier tipo de puerto)

espero q sirva de algo

---

### Post by ccp on 2007-08-07
Hola Zspikes,
justamente esa es la información que puse en el primer post. La info está ahí pero no se qué hacer con ella. Es decir, dentro de mi imaginación se me ocurre que probaría deshabilitando la placa que no anda y dejando sólo la otra disponible, el problema es que no se cómo hacerlo desde la línea de comados de terminal.
Tampoco se si es correcto mi razonamiento.
Saludos
CCP

---

### Post by Hei Ku on 2007-08-07
postea el contenido del archivo /etc/network/interfaces

por lo que tira el ifconfig, ninguna de las placas tiene direccion IP, asi que vamos a ver que esta configurado que tomen.

---

### Post by faktorqm on 2007-08-08
una pregunta, la interfaz usb0, que es? por que tiene muchos errores y nada transmitido. 

Par deshabilitar una placa de red:

```
sudo ifconfig eth0 down
```

En el caso que quieras deshabilitr eth0, ahi podes poner cualquiera de las interfaces que te muestre ifconfig solo.

Par habilitar una placa de red:

```
sudo ifconfig eth0 up
```

Salu2!

---

