---
title: "wired Network card macbook 1.1"
date: 2008-12-19
forum: Apple Hardware Users
---

### Post by saarakura on 2008-12-19
Hi!! 
 i have ubuntu on my macbook 1.1, and i loveee this but one thing is 
missing , my networkcard... wont apper, its like dont have any networkcard...
any help ? this same card works normaly on windows under bootcamp and
to work on mac os x i have to put de device id on kext appleyukon2.kext...
dont ask why because i dont know hahhahaaahha

well... i need a little help with this thanks for all!

---

### Post by cyberdork33 on 2008-12-19
what does 'ifconfig' show?

---

### Post by saarakura on 2008-12-19
ath0      Link encap:Ethernet  Endereço de HW 00:17:f2:3f:dd:18  
          inet end.: 192.168.1.109  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::217:f2ff:fe3f:dd18/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:4479 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:2949 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:5903955 (5.6 MB) TX bytes:296424 (289.4 KB)

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:1842 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1842 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:92100 (89.9 KB) TX bytes:92100 (89.9 KB)

wifi0     Link encap:Não Especificado  Endereço de HW 00-17-F2-3F-DD-18-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:9541 erros:0 descartados:0 excesso:0 quadro:4276
          Pacotes TX:2984 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:199 
          RX bytes:6512108 (6.2 MB) TX bytes:386544 (377.4 KB)
          IRQ:16

---

### Post by saarakura on 2008-12-21
Plz people i need help!! is there any way to this network card works ?

---

### Post by cyberdork33 on 2008-12-22
You are right, it does not show... try 
```
sudo modprobe sky2
```
in a terminal and see if it works.

If this fixes it then you need to add "sky2" to the bottom of your /etc/modules file.

---

### Post by saarakura on 2008-12-22
well... thks for help but the network dont work now in any OS, and when i put the cable on macbook and plug it on my router the led still off... i think the network is dead.... :(:(:(
i dont know what to do....

---

### Post by saarakura on 2009-02-23
well.. good news! i have formated my macbook and come back to MAC OS X, the network card wont apper and the airport take the en0, but under bootcamp its work!:o so i take the id and vendor of the card and put on the kext and its now works on OS X !!!!:p but the mac address is 00:00:00:00:00:00, any one can help me ? i need to know what the model of the networkcard on macbook 1.1 plz if anyone have this macbook help me!!!


thanks

---

### Post by saarakura on 2009-04-18
Hi people me again! i have triple boot on my macbook windows xp , mac os x , ubuntu.

But the wired network dont work only on ubuntu!!!! =/ i dont know what to do..there is any way to edit the id and vendor on "driver" for linux ?


thanks

---

### Post by saarakura on 2009-04-19
Output from  lshw -C network


  *-network DISABLED      
       description: Ethernet interface
       product: 88E8052 PCI-E ASF Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 00
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:f2:3f:dd:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.109 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

:confused:


nobody ? =/

---

### Post by saarakura on 2009-04-25
i have install 8.10 still not work..
and now 9.04 and the same... =/

plz people! :cry::cry:

---

### Post by cyberdork33 on 2009-04-25
I really don't know what the issue is. Maybe you could try resetting the SMC?
[http://support.apple.com/kb/HT1411](http://support.apple.com/kb/HT1411)

---

### Post by saarakura on 2009-04-25
don't work too =/, stranger is wired works on xp and macosx (with id device edit on .kext ) but on linux no =/

---

### Post by cyberdork33 on 2009-04-25
> **saarakura said:**
> don't work too =/, stranger is wired works on xp and macosx (with id device edit on .kext ) but on linux no =/
I just got the gist of what you are doing here... Sorry IDK know how to help you. Maybe some other forums that address your hardware setup more specifically might be able to help you.

---

