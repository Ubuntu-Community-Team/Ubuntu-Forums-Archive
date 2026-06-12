---
title: "Desactivar wifi per defecte"
date: 2009-10-03
forum: Catalan Team
---

### Post by klonner on 2009-10-03
Hola, 

fins la versio anterior de l'ubuntu, el wifi s'engegava només si jo apretava el botó del portàtil, però ara cada cop que engego l'ordinador l'ubuntu me l'engega, i he d'apretar el boto per parar-lo, com ho puc desactivar, es que normalment estic a casa i el tinc connectat per cable.

Gracies!

---

### Post by anna_marti_gomez on 2009-10-03
Hola Klonner,

has provat de fer:
```
sudo ifconfig wlan0 down
```?
Per saber si tens wlan0 o wlan 1 o el què sigui fes un: ```
ifconfig
```.

No sé, és el primer que jo faria.

Salut!!
anna

---

### Post by akyra on 2009-10-05
Sí el que vols es que no es connecti, podries deixar-lo engegat i en el network-manger desactivar la xasella que hi ha a dalt de "Connectar-se automaticament"

Adeu

---

### Post by jinglada on 2009-10-06
Jo sóc al·lèrgic al wifi i una solució dràstica me la va donar PatrickVogeli ([http://ubuntuforums.org/showthread.php?t=1110363):](http://ubuntuforums.org/showthread.php?t=1110363):) Anar a la BIOS i desactivar-la permanentment.

---

### Post by klonner on 2009-10-07
merci per les respostes!

el que vull es que el Hardware no s'engegui automàticament, com em feia abans.

i desactivar-lo a la BIOS.... home es una opció però a la universitat em seria una mica dificil de fer anar xDD

ara provaré.

Salut!

---

