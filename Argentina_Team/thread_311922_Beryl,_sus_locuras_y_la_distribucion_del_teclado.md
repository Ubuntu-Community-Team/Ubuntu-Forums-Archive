---
title: "Beryl, sus locuras y la distribucion del teclado"
date: 2006-12-03
forum: Argentina Team
---

### Post by felipelerena on 2006-12-03
Tengo Beryl instalado y funcionando en Edgy con los drivers beta de nvidia y me pasa algo muy loco que hoy descubri por que pasa.

solo me funciona cuando arranco poniendo
```
gdm
```
y no me funciona cuando arranco con 
```
startx
```
cuando arranco con startx me aparece un mensaje de "su teclado esta configurado diferente del de X" y si le doy que lo cambie para ponerlo igual que el de X beryl arranca perfectamente y se cuelga solo una vez cada CINCO dias, eso es muy poco tiempo, hay gente que tiene un problema por hora (me dijeron que es gracias a los drivers beta de NVIDIA (que son muy buenos!!!!) ).

El problema esta cuando le digo que quiero conservar mi configuración actual (que curiosamente, y esto no lo había aclarado, es la misma cponfiguracion...) que beryl directamente no arranca.

En resumen VA PERFECTO, pero tiene algunas locuras raras...

Les cuento todo esto por que me gustaría arrancar un thread (y de hecho lo hice) donde los que estamos "experimentando" con beryl (y disfrutándolo) compartamos nuestras experiencias y podamos ayudar a los demás a instalarlo.

Estoy muy contento con Beryl, VA "como trompada"... aunque como todo lo experimental... tiene sus locuras.

Un saludo.

---

### Post by QUASAR_FREAK on 2006-12-03
lo mas seguro es que estes iniciando beryl sobre XGL, y tengas hecho el arreglo para iniciarlo dentro de gdm.conf-custom

yo te rekomendaria ke dejes de usar los drivers betas e instales los 9626 estables y uses beryl bajo aiglx. de esa forma se irian esos problemas.

---

### Post by felipelerena on 2006-12-03
no no, estoy usando AIGLX... y los drivers beta son los mas... tiene un manejo grafico muy interesande del !multimonitor! (para mi que cambio mucho del segundo monitor a la tele me viene barbaro) ese problema no tiene nada que ver con los drivers beta.

de todos modos ese mismo problema pasa sobre XGL con los estables...

---

### Post by Nemesis Teufel on 2006-12-03
y quien usaria xgl con una nvidia, si tenes ati.. we.. ahi si.

---

### Post by felipelerena on 2006-12-03
> **Nemesis Teufel said:**
> y quien usaria xgl con una nvidia, si tenes ati.. we.. ahi si.

coincido... pero... ¿quien se compraria una maquina con ATI?

---

### Post by ariel on 2006-12-04
> **felipelerena said:**
> Tengo Beryl instalado y funcionando en Edgy con los drivers beta de nvidia y me pasa algo muy loco que hoy descubri por que pasa.

solo me funciona cuando arranco poniendo
```
gdm
```y no me funciona cuando arranco con 
```
startx
```cuando arranco con startx me aparece un mensaje de "su teclado esta configurado diferente del de X" y si le doy que lo cambie para ponerlo igual que el de X beryl arranca perfectamente y se cuelga solo una vez cada CINCO dias, eso es muy poco tiempo, hay gente que tiene un problema por hora (me dijeron que es gracias a los drivers beta de NVIDIA (que son muy buenos!!!!) ).

El problema esta cuando le digo que quiero conservar mi configuración actual (que curiosamente, y esto no lo había aclarado, es la misma cponfiguracion...) que beryl directamente no arranca.

En resumen VA PERFECTO, pero tiene algunas locuras raras...

Les cuento todo esto por que me gustaría arrancar un thread (y de hecho lo hice) donde los que estamos "experimentando" con beryl (y disfrutándolo) compartamos nuestras experiencias y podamos ayudar a los demás a instalarlo.

Estoy muy contento con Beryl, VA "como trompada"... aunque como todo lo experimental... tiene sus locuras.

Un saludo.

Yo estoy usando Beryl desde 0.1.0, sobre nvidia. Lamentablemente desde Beryl 0.1.2 surgio un bug en placas de 128MB incluida mi GeForce 6200, cuando abris muchas ventanitas, de repente se pierde contenido de las ventanas. Nvidia reconocio que el bug es en el driver.

Tengo instalado  activo 0.1.3 (svn) y el ultimo beta de nvidia y los problemas siguen, espero que los pibes de nvidia se pongan las pilas pronto y lo arreglen. El sistema es usable activando aiglx rendering en lugar de 'nvidia rendering' pero la performance de la maquina se cae. 

Por ahora Beryl esta bueno para mostrar a los amigos pero para el uso diario 'en produccion' me parece que le faltan algunos meses de desarrollo. Al menos yo me doy cuenta de que cada vez que tengo que trabajar, termino switcheando a metacity. Seguramente beryl va a llegar muy estable  al release de feisty y va a estar buenisimo.

---

### Post by cocotapioca on 2006-12-04
Beryl es lo mas y anda joya con los ultimos drivers...los probaste y depsues vovliste a los beta o ni los probaste? 
El unico problema que tuve y tengo con beryl es que tener las maquina prendida un par de dias, la reproduccion de video se ve ultra lenta, sobretodo los mkv ... pero todos engenreal , cuando cambias de window manager y volves a metacity , la velocidad de reproduccion se normaliza ,salvo los mkv q se ven un toq lento ... sera problema de codecs?, y ahi es donde reinicio..... con los drivers beta no me pasaba esto .... deberia tratar de probar lo beta nuevamente y fijarme ... pero me da fiaca y no tengo mucho tiempo...

---

### Post by kalel on 2006-12-04
hablando de beryl, aca estoy yo jugando un ratito





[http://www.youtube.com/watch?v=qM1DlvFSSYM](http://www.youtube.com/watch?v=qM1DlvFSSYM)

---

### Post by Nemesis Teufel on 2006-12-04
> coincido... pero... ¿quien se compraria una maquina con ATI?
Los gamers x ejemplo o los que no sepan el poco soporte que hay en linux, ya que en la serie 5xxx a 7xxx la Ati le pasa el trapo.

---

