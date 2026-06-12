---
title: "Firefox avui no funciona"
date: 2009-07-23
forum: Catalan Team
---

### Post by prostata on 2009-07-23
En arrencar l'ordinador aquest matí el firefox 3.0 no funciona, tampoc el thunderbird, es veu que estic conectat per l'ìcone que surt de connexió de la xarxa, però no conecta el fierefox ni thunderbird. Ara estic a una sessió de Windows i tot va normal.

El fet s'ha produit en arrencar l'equip, no he fet cap mena d'instal-lació nova de programari res de res, he tingut la màquina uns dies per vacances apagada, però ahir en arribar tot anava correcte fins aquest matí...

Em podeu fer un cop de ma...?? gràcies...

Salutacions

---

### Post by oriolsbd on 2009-07-23
Aquest matí em sembla que hi ha hagut una actualització del Firefox (potser ja va arribar ahir al vespre, però jo l'he actualitzat avui). No sé si pot haver estat això. Amb el firefox-3.5 et va?

La resta de coses sí que et funciona? Per exemple, et va bé una actualització dels repositoris?
```
sudo apt-get update
```

Salut!

---

### Post by prostata on 2009-07-23
Doncs ja funciona de nou i sense fer res de res, bé he desconectat el router he tornar a arrencar l'equip i tachín...!!!!

No ho entenc i si fos posible i algú en tinguès alguna explicació ....

gràcies

---

### Post by epages on 2009-07-24
Explicacions poden haver-hi moltes en funció de múltiples paràmetres: com està l'equip connectat al router, com està configurada la tarja de xarxa, ... 

Poder donar-te una explicació raonada del que t'ha passat podria suposar pràcticament el que s'anomena un "anàlisi forense": per què se'm va morir la xarxa?. Si vols practicar el CSI pots comença examinant els fitxers a /var/log

Per sort o per desgracia la solució de reiniciar funciona moltes vegades en [molts sistemes]("http://www.avui.cat/cat/notices/2009/07/l_aturada_de_la_central_nuclear_d_asco_va_ser_causada_per_un_error_huma_66333.php"). En GNU/Linux [hi ha moltes altres opcions]("http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html") que es poden aplicar abans de provar de reiniciar tot el sistema.

Salut!

Eduard

---

