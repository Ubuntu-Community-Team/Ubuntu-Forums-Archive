---
title: "AYUDA Instalar placa de RED Realtek RTL8139"
date: 2008-01-30
forum: Argentina Team
---

### Post by djthree on 2008-01-30
Hola,

Se me quemo la placa de RED del Mother por tormenta y me compre un tarjeta de RED generica con CHIP REALTEK, que es esta:

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

Desde ya, gracias por la ayuda, 
Saludos.

---

### Post by clasificado on 2008-01-31
¿Seguro que tenes dhcp? Por ahi deberias asignarle una IP fija.

Fijate en las configuraciones de red, que te tiene que dar la opcion

Te diria los comandos de consola, pero no me los se :KS

clasificado

---

