---
title: "Instalacio driver USB Airlive WL1600 USB"
date: 2010-06-13
forum: Catalan Team
---

### Post by kioni on 2010-06-13
Hola, fa poquet que he posat l'Ubuntu a un pc i no tinc massa experiencia en tema de compilar drivers, concretament tinc problemes al intentar instalar el drivers del llapis USB wifi Airlive WL1600 USB.
Obro el Terminal em poso al directori on he descomprimit el fitxer i poso make, el resultat es el seguent:

root@Ernest:/home/ernest/ci# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/ernest/ci/ieee80211/ieee80211_softmac.o
  CC [M]  /home/ernest/ci/ieee80211/ieee80211_rx.o
  CC [M]  /home/ernest/ci/ieee80211/ieee80211_tx.o
  CC [M]  /home/ernest/ci/ieee80211/ieee80211_wx.o
  CC [M]  /home/ernest/ci/ieee80211/ieee80211_module.o
/home/ernest/ci/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/ernest/ci/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/ernest/ci/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ernest/ci/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2
root@Ernest:/home/ernest/ci# 

No se perque surt aquests 2 errors :(

Si algu vol veure els drivers els he baixat de la web oficial seguent:

[http://www.airlive.com/support/support_3a.jsp?pdid=PD1223473034861](http://www.airlive.com/support/support_3a.jsp?pdid=PD1223473034861)

Espero que algu em pugui donar un cop de ma ? Actualment no em funciona correctament el dispositiu i ja se sap, sense internet el linux es una mica limitat ...

Moltes gracies per avançat :)

---

### Post by kioni on 2010-08-12
Al final he amulat el driver del windows amb el Ndiswrapper :)

---

