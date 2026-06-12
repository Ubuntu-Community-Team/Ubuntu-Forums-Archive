---
title: "HP G62 a35ss és compatible amb ubuntu?"
date: 2011-05-07
forum: Catalan Team
---

### Post by Vanitas_92 on 2011-05-07
Bones a tothom,

Degut que la universitat em demana programes que només són compatibles amb Linux vaig decidir instal·lar ubuntu al portàtil HP G62 a35ss, però he tingut bastants problemes alhora de poder fer-lo anar. 
El primer cop vaig instal·lar la versió 10.04 i bé, sempre instal·lo amb Wubi, però alhora d'instal·lar vaig veure que la retroil·luminació de la pantalla s'apagava i no podia veure res, però al acabar la instal·lació podia executar-lo sempre donant l'error de "failed to get i915 symbols: graphics turbo disabled" pero podia utilitzar-lo mes o menys bé, això si, es posava molt calent i poques vegades s'apagava sol crec que degut a la temperatura que arribava.
Arran de la surtida de Natty, vaig decidir fer-li una instal·lacio neta, o sigui desinstal·lant tot des de windows per aixi tornar instal·lar mitjançant wubi la 11.04. Però veia que no arrancava la instal·lació perquè el vaig deixar tot una nit perquè s'instal·les i veia que em passava el mateix problema de la retroil·luminació, vaig decidir de instal·lar-ho mitjançant el live cd, però tampoc arrenca el live cd. La última mesura de desesperada va ser instal·lar la 10.10 i actualitzar cap a Natty. Per aquí be, pero em passava un problema que tampoc es podia arrencar pero que ho vaig solucionar posant el grub "acpi=off" veia que si podia arrencar. Tot ha anat més o menys be, (excepte el problema de acceleració de gràfics i la temperatura que agafa sense estar treballant) fins avui, que al arrancar l'ubuntu, m'ha sortit el grub dient que no hi havia cap disc per arrencar, i vec que des de windows ha desaparegut. Jo ja no ser que fer mes. M'interessa molt la 11.04 principalment per unity, perquè aixi aprofito més la pantalla per treballar.

Crec que aquests problemes venent per l'acpi i crec que també per la tarjeta integrada grafica intel i la dedicada ati radeon mobility 5470.

Moltes gracies.

---

### Post by blauigris on 2011-10-25
Jo tinc el mateix portàtil que tu. El problema, almenys amb el tema de la pantalla és que porta gràfics hibrids, els quals lamentablement no estan gaire bé suportats. Googlejant un rato vaig trobar un bug al lauchpad que explicava que hi estaven treballant i que aviat treurien una actualització, però almenys a mi em continua petat.

Mirant els logs de les X vaig trobar que deixa que provés amb d'arrancar amb l'opcio "video.allow_duplicates=1", i almenys m'arrenca, tot i que amb només amb l'intel. Prova-ho i en tot cas digues com t'ha anat.

---

### Post by wgarcia on 2011-10-26
Wubi és un mecanisme més que res per a provar Ubuntu, i no és recomanable si es vol fer un ús més o menys continuat. Per aquests casos una instal·lació amb partició pròpia és el més recomanable, fent una doble arrencada si es vol mantenir un altre sistema operatiu.

---

