---
title: "inici Ubuntu"
date: 2009-02-08
forum: Catalan Team
---

### Post by venusfenix on 2009-02-08
bon dia,

desde fa unes quantes actualitzacions, que el temps d'arrancada i apagada, es molt mes gran que d'habitual.

i desde fa molt cop, el temps d'atura, s'ha escurça't practicament a cero.

pero l'inici, continua trigant moltissim. es normal?? es pot minimitzar alguna manera, tranquilament triga unos 5-8 minuts. I quant surt la barra de progres, es queda com parada al 40% aprox.
en camvi, desde fa recentment poc, quan es tanca el sistema, en questions de segons, ja esta apagat.

gracies,

---

### Post by RainCT on 2009-02-09
Que l'apagada sigui ràpida és normal. Pel que fa a l'arrencada, encén l'ordinador, ves al GRUB (gestor d'arrencada) i prem "e" per editar la entrada se&#320;lecionada, torna a prémer "e" per editar la primera línia i d'allà esborra les paraules "quiet" i "splash" (aquest canvi no és permanent, no et preocupis si fas alguna cosa malament que quan apaguis l'ordinador s'oblidarà de tot). Llavors prem Enter i finalment arrenca l'Ubuntu premement "b". Ara en lloc de la pantalla d'arranc sortiran tots els missatges informatius, i pots fixar-te en quin és el problema pel que tarda tant.

---

### Post by venusfenix on 2009-02-11
buenas i merces per l'ajuda, pero res.
no ha funcionat.

quan entro al grub, em trobo amb 4 lines (x2) dels differents kernels que hi han instalats.
edito l'ultima versió, i nomes hi han 4 lineas,
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-11-generic etc....
initrd /boot/initrd.img-2.6.27-11-generic
quiet

he tret l'ultima, pero l'arrancada continua igual de lenta, i a mes, no veig el que passa. Continua sortint la pantalla principal.

alguna cosa que es pogui fer??

moltes gracies!!!!

---

### Post by venusfenix on 2009-02-11
Buenas,

he estat fent probes i he pogut veure que intenta montar una unitat i donar fail, pot ser que es trigui tan de temps nomes perque no trobat una unitat HDD esterna que no esta conectada??

gracies,

---

