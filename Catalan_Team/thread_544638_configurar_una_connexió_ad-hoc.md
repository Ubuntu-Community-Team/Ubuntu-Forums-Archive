---
title: "configurar una connexió ad-hoc"
date: 2007-09-06
forum: Catalan Team
---

### Post by mesmerize on 2007-09-06
Tinc un Pc amb Ubuntu i un portàtil amb WinXP. El PC està connectat a Internet a través d'un cable-modem (ethernet), i m'agradaria fer servir la targeta wifi del PC per poder accedir a Internet amb el portàtil. La targeta porta un xip Realtek RTL8187 i l'Ubuntu sembla que la reconeix, però el Networkmanager no em dóna l'opció d'establir una connexió Ad-hoc i em sembla que s'ha de fer a través de l'arxiu /etc/network/interfaces. Algú em podria donar un cop de ma?

---

### Post by muzzol on 2007-09-07
algunes targes wifi no estan plenament suportades.

a la pràctica això vol dir que funcionen però que tenen part de les seves capacitats retallades degut a que els mòduls que les controlen no suporten totes les característiques.

desconec com està el suport d'aquesta tarja en concret, jo de tu cercaria una mica per sant google a veure que es diuen.

sort

---

### Post by mesmerize on 2007-09-21
En el CD de la placa base ve el driver per Linux de la targeta wifi i segons el readme.txt la connexió adhoc si que està suportada. El problema que tinc es que no puc instal·lar el driver:
> < Installation >

Runing the scripts can finish all operations of building up modules 

from the source code and start the nic.

	1. Build up the drivers from the source code

	  ./makedrv
Quan faig ./makedrv surten molts errors:
```
david@david-desktop:~/linux26x-8187/rtl8187_linux_26.1010.0622.2006$ ./makedrv
ieee80211/
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/ieee80211.h
tar: ieee80211/.tmp_versions: Cannot utime: Operation not permitted
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_wx.c
ieee80211/license
ieee80211/Makefile
ieee80211/Modules.symvers
ieee80211/readme
tar: ieee80211: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors
beta-8187/
beta-8187/r8180_hw.h
beta-8187/r8187.h~
beta-8187/r8180_rtl8225.h
beta-8187/license
beta-8187/.tmp_versions/
beta-8187/.tmp_versions/r8187.mod
beta-8187/Makefile
tar: beta-8187/.tmp_versions: Cannot utime: Operation not permitted
beta-8187/r8180_93cx6.c
beta-8187/tags
beta-8187/authors
beta-8187/r8187_core.c~
beta-8187/r8180_pm.h
beta-8187/r8180_rtl8225.c
beta-8187/copying
beta-8187/r8180_wx.h
beta-8187/Modules.symvers
beta-8187/r8180_rtl8225z2.c
beta-8187/readme
beta-8187/r8187_core.c
beta-8187/ieee80211.h
beta-8187/r8180_93cx6.h
beta-8187/changes
beta-8187/r8187.h
beta-8187/r8180_pm.c
beta-8187/install
beta-8187/ieee80211_crypt.h
beta-8187/r8180_wx.c
tar: beta-8187: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/tmp
make -C /lib/modules/2.6.20-16-generic/build M=/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:391: avís: ISO C90 forbids mixed declarations and code
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:412: avís: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_stop_scan’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:486: avís: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_abort’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:885: avís: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1360:4: warning: #warning CHECK_LOCK_HERE
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1400:2: warning: #warning CHECK_LOCK_HERE
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1471: avís: ISO C90 forbids mixed declarations and code
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_stop_protocol’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2060: avís: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: (Each undeclared identifier is reported only once
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: for each function it appears in.)
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2169:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2170:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2171:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2173:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_free’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2192: avís: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
make[2]: *** [/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/tmp
make -C /lib/modules/2.6.20-16-generic/build M=/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o
In file included from /home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:64:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:700: avís: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1428: avís: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_init’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625: error: (Each undeclared identifier is reported only once
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625: error: for each function it appears in.)
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_ioctl’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2298: avís: ISO C90 forbids mixed declarations and code
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8187_usb_probe’:
/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2421: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
make[2]: *** [/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/david/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2
david@david-desktop:~/linux26x-8187/rtl8187_linux_26.1010.0622.2006$ 


```

Alguna idea?

---

### Post by pespin on 2007-09-21
De vegades els drivers que venen per defecte a l'Ubuntu encara els hi falta teca i els hi manquen algunes opcions.

Googlejant així ràpid pel que veig la solució és desactivar els moduls que porta el Ubuntu per defecte i instal·lar-los mitjançant el ndiswrapper. :) 

LLegeix tot el topic aquest, potser t'ajuda: [http://ubuntuforums.org/showthread.php?t=314352]("http://ubuntuforums.org/showthread.php?t=314352")

---

### Post by mesmerize on 2007-09-22
El ndiswrapper ja està instal·lat. El que no ser fer es desactivar els mòduls que venen per defecte. Sembla que s'han d'afegir a una llista (blacklist) els mòduls rtl, r8187 i rtl8187.

---

### Post by Ferri on 2007-09-22
Un parell de preguntes:
Quan fas ./makedrv ho has fet com a sudo (o root)?
Tens instal·lat els kernel-headers?

---

### Post by mesmerize on 2007-09-22
Ho he fet com a usuari i com root amb el mateix resultat. I els linux-headers ja están instal·lats. De totes maneres sembla que el driver "oficial" de Realtek no funciona pel que he pogut deduïr a Ubuntu forums i s'ha de fer amb el ndiswrapper i el driver de win98.

---

### Post by Ferri on 2007-09-22
Teòricament el primer error que et surt (cannot utime operation not permitted) passa quan l'usuari que està intentant fer l'operació no té els privilegis necessaris, però si ja ho has intentat com a root, no se m'acut res més.

---

### Post by mesmerize on 2007-09-22
Efectivament els errors "cannot utime: operation not permitted" no surten com a root però els del make si.

---

### Post by Ferri on 2007-09-23
Potser et falta algun dels paquets necessaris per compilar la kernel. Inenta:
```
sudo apt-get install sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```
Que són els que són necessaris segons [aquest fil]("http://ubuntuforums.org/showthread.php?t=311158")
Després, seguint els mateixos consells:
```
sudo -s
```
Si et segueix sense funcionar, probablement és un problema del driver.
Com tu mateix ja dius, et queda el ndiswrapper, però en això no et puc ajudar. Tinc la sort que la meva tarja wifi em funciona directament.

---

### Post by mesmerize on 2007-09-30
He avançat una mica. La targeta la reconeix:
```
david@david-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"AP350"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
He fet un sudo iwlist wlan0 scan i troba dues xarxes. Sembla que la targeta funciona bé. Ara em falta canviar el mode Managed pel mode Ad-hoc.
He fet:
```
david@david-desktop:~$ sudo iwconfig wlan0 mode Ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
```
Sembla que s'hagi de deshabilitar la targeta per a poder fer el canvi. Ho he provat amb sudo ifconfig wlan0 down i després sudo iwconfig wlan0 mode Ad-hoc i el resultat:
```
david@david-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
El problema és que no puc tornar a habilitar la targeta:
```
david@david-desktop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not permitted
```

Alguna idea?

---

### Post by homexyz1 on 2007-12-07
Hi 

I am having trouble making the driver work. 
I am getting the same error as listed.

Can you help

Regards

---

