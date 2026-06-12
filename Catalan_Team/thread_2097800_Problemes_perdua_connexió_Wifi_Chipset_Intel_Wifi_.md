---
title: "Problemes perdua connexió Wifi Chipset Intel Wifi Link 5100"
date: 2012-12-24
forum: Catalan Team
---

### Post by akyra on 2012-12-24
Hola a tothom

Tinc un Toshiba Satellite A500-14 amb  chipset Intel® GM45 Express e Intel® WiFi Link 5100.
Tinc Ubuntu 12.04  64 bits i fins fa poc no havia tingut aquest problema que ara us explicaré

Des de fa qüestió d'un mes aproximadament que la meva connexió wifi tipus n des del portatil va fallant de forma intermitent, amb això vull dir que es connecta quan engego l'ordinador (cap problema), però després es desconnecta i em demana la clau d'accés a la wifi, que ja me la mostra la que pertoca.
L'unic que puc fer es desconnectar i connectar l'interruptor de wifi del portatil o reiniciar l'ordinador.

Aquests fallades d'ordinador es van produint d'una forma totalment aleatoria i a vegades triga una hora a produir-se i a vegades 5 minuts després d'engegarse l'ordinador.

El router que tinc és un Cisco que dona ONO i que ja fa un any que tinc i no he detectat cap problema en cap altre dispositiu connectat a la wifi.

Avui, per exemple, em volia connectar a la feina per VPN i no hi ha via manera, de seguida he vist fent un ping al router que em sortia "Destination Host unreacheable". He hagut de reiniciar l'ordinador i ha anat perfectament durant 10 minuts, desp&#341;es ha perdut el senyal i hagut de tornar a reiniciar i ara porta 30 minuts sense cap problema.

Bé una mica desconcertant.

Algú té idea que pot ser (diferents kernels amb drivers nous,....?)

Moltes gracies.

---

### Post by kimet on 2012-12-27
Intentaria concretar exactament a que es degut el mal funcionament.

Mirar a /var/log si troves alguna cosa que et pugui donar una idea.

Provar a canviar el xifratge WPA, WEP inclús pots provar sense xifratge momentaneament. pot ser un error de wpa_supplicant.

Comprovar el driver que estàs usant i si es correspón al que hi ha a la pagina [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads) i mira aquest fil: [https://bbs.archlinux.org/viewtopic.php?id=132079](https://bbs.archlinux.org/viewtopic.php?id=132079)
al post #15.

Desactivar netwrk-manager i intentar conectar manualment o usar wicd, (de vegades he vist reports de mal funcionament amb NM, poc probable)

Comprovar que el canal no sigui sobreutilitzat o hi hagin excesiva distancia dels dispositius al router o aparells o cablejat que pogui provocar interferències.


Salut i bon any.

---

### Post by akyra on 2012-12-28
Hola Quimet,

Sembla que el problema ve realment del router de ONO.
L'altre dia vaig poder provar a la vegada diferents dipositius i tots perdian le conexió.
Vaig parlar amb ONO i em varen dir que haig d'apagar el router dos cops per setmana uns 10 minuts per tal que es descarregui.

Ho vaig fer i pel moment ha anat bé.

He mirat els controladors de wifi que tinc fent:

> jordi@jordi-ubuntu:~$ lsmod | grep -i wifi
iwlwifi               397059  0 
mac80211              506862  1 iwlwifi
cfg80211              205774  2 iwlwifi,mac80211


La distancia al router quan pasava això era de 4 metres no més.

Provaré uns dies, i si veig que tot segueix bé, tancaré el fil.

Gracies per les teves indicacions.

---

### Post by akyra on 2013-01-24
Al final sembla haver estat la configuració del cable modem de ONO, m'han canviat al canal que estava al 13 per el 6 (m'han dit que a partir del 10 és configuració americana, ?????) i han tret el firewall.

Bé seguiré observant per si es repeteix el fallo i és només a l'ordinador.

Gracies

---

