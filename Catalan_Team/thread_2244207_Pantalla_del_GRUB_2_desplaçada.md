---
title: "Pantalla del GRUB 2 desplaçada"
date: 2014-09-14
forum: Catalan Team
---

### Post by skywalk on 2014-09-14
Hola,
Us comento un problema estètic i no pas de funcionament. Quan vaig instal·lar de nou l'Ubuntu 12.04 i intentava instal·lar els controladors privatius de la targeta ATI, una de les vegades d'instal·lar-desinstal·lar-reiniciar se'm va quedar la pantalla d'inici del GRUB 2 desplaçada del monitor. O sigui, que em queden 5 o 6 cm a l'esquerra en negre. Quan s'inicia el sistema operatiu està centrada, i si vull corregir la pantalla d'entrada de GRUB ho puc fer a través de les tecles de funció del monitor, però després és el sistema operatiu el que queda desplaçat. Com és lògic, prefereixo iniciar amb la pantalla de GRUB desplaçada, però cada cop que engego em fa ràbia. Fa poc vaig actualitzar al 14.04 però continua igual. M'imagino que és una tonteria i que algú de vosaltres em donarà la solució, però jo no sé pas com fer-ho. Si algú m'ajuda, encantat de la vida. 
Gràcies.

---

### Post by wgarcia on 2014-09-16
El primer que  es pot provar és tornar a configurar el Grub a veure si s'arregla. Per això es pot obrir una terminal i entrar l'ordre:

```

sudo update-grub

```

---

### Post by skywalk on 2014-09-20
Wgarcia, gracies per el teu interès. Avui ho he solucionat de casualitat. Llegint un article sobre targetes gràfiques, explicaven que si tens connectat el monitor i la targeta amb un cable VGA amb un adaptador a la sortida de la targeta de DVI a VGA no es massa bo perquè ha de convertit dos cops la senyal etc. He recordat que feia temps que ho havia posat així per fer unes proves i així es va quedar. He canviat el cable per un DVI i he tret el adaptador. Quan he reiniciat el ordinador, miracle, la pantalla del Grub estava be. 
De totes maneres esta solucionat però sense saber perquè succeïa aquest problema.
Marco com ha solved.

---

