---
title: "Instalar placa de red?"
date: 2006-12-30
forum: Argentina Team
---

### Post by Hex_Mandos on 2006-12-30
Creo que dije hace un tiempo que una tormenta me quemó la placa de red del mother. Bueno, ahora finalmente instalé una nueva, y no se como hacer para que Ubuntu la reconozca. La placa funciona, me da opciones durante el booteo y si los leds no mienten se comunica con el modem. Pero a la hora de conectarme a internet me da que no tiene conexión. Alguien tiene idea por donde empezar, por lo menos?

---

### Post by beuno on 2006-12-30
> **Hex_Mandos said:**
> Creo que dije hace un tiempo que una tormenta me quemó la placa de red del mother. Bueno, ahora finalmente instalé una nueva, y no se como hacer para que Ubuntu la reconozca. La placa funciona, me da opciones durante el booteo y si los leds no mienten se comunica con el modem. Pero a la hora de conectarme a internet me da que no tiene conexión. Alguien tiene idea por donde empezar, por lo menos?

Esto te puede ser muy util: [http://www.davidpashley.com/articles/network-troubleshooting.html](http://www.davidpashley.com/articles/network-troubleshooting.html)

---

### Post by martin85pmp on 2007-11-30
Hola, a mi me pasó lo mismo, una tormenta me quemó la placa de red de la mother, y no se que hacer, alguien me puede decir algo??? La placa que agregué es una NIC Fast Ethernet PCI Familia RTL8139 de Realtek.
Ubuntu reconoce la placa pero no conecta a internet.

Muchas gracias

---

### Post by kowal on 2007-11-30
Podés pingear otras máquinas o el router? Probaste deshabilitando la quemada editando /etc/network/interfaces?

---

### Post by martin85pmp on 2007-11-30
Gracias por la ayuda, la traté de deshabilitar manualmente,  pero era lo mismo, como se hace para deshabilitarlo vía /etc/network/interfaces ??? es con la terminal? voy a probar, no soy usuario experto!
Si reistalo ubuntu arrancará bien? porque estaba pensando bajarme la versión 7.10

Gracias por tu ayuda!

---

### Post by kowal on 2007-11-30
> **martin85pmp said:**
> Gracias por la ayuda, la traté de deshabilitar manualmente,  pero era lo mismo, como se hace para deshabilitarlo vía /etc/network/interfaces ??? es con la terminal? voy a probar, no soy usuario experto!

Copiá y pegá lo que te tira "ifconfig" y "cat /etc/network/interfaces" en la terminal. 

Si la placa de red del mother es **eth0, **entonces la nueva es **eth1. **Comentando con una almohadilla (o sea con #) en ese archivo deshabilitás la placa. A mi me pasó algo parecido.. mi mother tiene 2 placas de red. y una se me quemó (eth0), entonces la deshabilité y habilité la otra (eth1).

Así quedó mi archivo /etc/network/interfaces (tengo dhcp):

> 
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


[quote=martin85pmp]Si reistalo ubuntu arrancará bien? porque estaba pensando bajarme la versión 7.10[/QUOTE]

Es bastante probable, de hecho podés probarlo en modo LiveCD antes de instalar. Aunque seguramente también se puede solucionar sin tener que reinstalar.

---

### Post by djthree on 2008-01-28
Hola, parece que somos varios a los que se nos quemo la placa de RED del Mother por tormenta.... :(

Yo por mi parte, tambien me compre un tarjeta de RED generica con CHIP REALTEK, que es esta:

**Realtek RTL8139 PCI Fast Ethernet Adapter**

En Win XP funciona OK.

Tengo conectada esta tarjeta a un router wireless Huawei echoLife HG520.

En Ubuntu no puedo lograr hacerla andar, no me la detecta.
les dejo algunos comandos que tire en la terminal a ver si alguien me puede ayudar.

# cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp 
```

# sudo lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
[B]00:13.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
[/B]01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a
```

# sudo ifconfig
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59240 (57.8 KiB)  TX bytes:59240 (57.8 KiB)
```

Gracias por la ayuda, 
Saludos.

---

### Post by guisheca on 2008-01-29
Espero no ofender a nadie, pero trataste de hacer click en el icono de red del panel de gnome? ahí te tiene que dar la posibilidad de elegir entre las placas que tenés, elegís la que funciona y listo.
Para no tener que hacerlo cada ves que inicia el sistema, simplemente podés desabilitar la placa de red directamente desde el bios de la placa.
Te digo porque a mi también me pasó lo mismo, y haciendo eso ahora estoy 10 puntos.
Espero haberte sido de ayuda.

---

### Post by djthree on 2008-01-30
Hola Guisheca,
Gracias por la colaboracion, pero te comento que laplaca de RED interna de la mother la desactive desde el BIOS, por lo cual ya no aparece, y la nueva tampoco aparace en la parte de network de nome. Es decir que noi me la toma de forma automatica.
Cuando tire el comando "lspci" aparece en el listado la tarjeta, pero no se como hacer para que funcione.

Gracias igual por el dato. 
Saludos.

---

