---
title: "Nueva versión de WINE emula a la perfección Fireworks"
date: 2007-09-18
forum: Argentina Team
---

### Post by facundocorradini on 2007-09-18
Bueno, esta vez para darles una buena noticia:

La nueva versión de Wine vino con muchas mejoras, estos muchachos superan mis expectativas día a día....

Anteriormente había probado Fireworks en Wine y la verdad es que el uso era muy limitado, ya que no se podían retocar los efectos...
Con la última versión de wine (disponible en repositorios propios de wine, aún no en los de ubuntu), ya se han arreglado estos problemas.
Y aún no he probado flash, pero supongo que debe funcionar igual de bien.

Sin dudas una buena noticia, ya que la suite macromedia era hasta hoy una gran traba que mantiene a muchos usuarios con windows...

---

### Post by marianom on 2007-09-18
¿Y Dreamweaver? Mi compañero de trabajo es adicto a ese programa. Capaz que me sirve para intentar traerlo (le mostré como quedaba el vim con syntax on pero no lo convencí...).

---

### Post by facundocorradini on 2007-09-18
Dremweaver anda barbaro desde hace varias versiones ya,

Pero bueno, si es adicto a ese programa, lo siento mucho por él. Dreamweaver genera sitios de **muy** mala calidad... Si quiere hacer las cosas bien q no sea vago y diseñe con algún buen IDE en modo código, como Quanta+ o Bluefish....

BTW: lo que estoy diciendo se aplica a la **versión 8** , tanto de Fireworks como Dreamweaver.

---------------------------------------------------------------------------------------
actualización: Estube tocando un poco el Flash 8 y hasta donde probé también anda de maravillas, pero bueno, no soy diseñador flash y no conozco bien el soft, así que me quedaron muchas cosas por probar (simplemente no se como se usan)

---

### Post by Mauro22 on 2007-09-18
Actualize al version de wine, y en el counter strike 1.6 No Steam, mientas se juega se puede ver el escritorio.


A alguien le pasa esto?

---

### Post by FlyerDie on 2007-09-18
> **Mauro22 said:**
> Actualize al version de wine, y en el counter strike 1.6 No Steam, mientas se juega se puede ver el escritorio.


A alguien le pasa esto?

jeje como???
Podes poner un screenshot para ver cual es el bug?

---

### Post by Mauro22 on 2007-09-18
[img]http://www.pic2up.net/S6QZG2w.jpg[/img]

Ahi esta, 

En el medio se puede ver el ying yang, que forma parte del escritorio, al igual que los dos iconos que tengo en la esquina superior irzquierda.

Siempre me toca lo mas raro.
Esto fue inmediato despues de actualizar wine

---

### Post by FlyerDie on 2007-09-18
veo que no es fullscreen, que te aparece la barra de gnome arriba tambien, no sera que tenes beryl + glx y se te queda activado con alguna de las cualidades?
Ya se que antes no te pasaba, pero me da esa sensacion...

---

### Post by niko_3100 on 2007-09-18
Yo tengo un wine instalado la version 0.9.33 que la baje desde el synaptics que viene en feisty fawn que version salio nueva? Tenes idea? como podria actualizar a esta nueva version queiro probar si puedo instalar mi lexmark x2250 con los drivers del xp jej!!

---

### Post by LaHire on 2007-09-19
> **FlyerDie said:**
> veo que no es fullscreen, que te aparece la barra de gnome arriba tambien, no sera que tenes beryl + glx y se te queda activado con alguna de las cualidades?
Ya se que antes no te pasaba, pero me da esa sensacion...

Más que nada con las transparencias de las ventanas...quizás, claro

y el Compiz-Fusion, no era mejor?, yo no ando en esa onda de el escritorio pimpeado, lo tuve durante 5 minutos y derritió mi gabinete (de veras tengo que pensar en arreglar/limpiar el cooler del micro....)

---

### Post by facundocorradini on 2007-09-19
> Yo tengo un wine instalado la version 0.9.33 que la baje desde el synaptics que viene en feisty fawn que version salio nueva? Tenes idea? como podria actualizar a esta nueva version queiro probar si puedo instalar mi lexmark x2250 con los drivers del xp jej!!

Desde synaptic, vas a configuracion --> repositorios --> software de otros proveedores, y ahí agregas este repo:

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

Luego le das recargar al synaptic, buscas el wine y lo marcas para actualizar

> Actualize al version de wine, y en el counter strike 1.6 No Steam, mientas se juega se puede ver el escritorio.

Yo lo acabo de probar y me anda barbaro, decididamente tu problema tiene que ver con compiz...  (btw: cuanto hace que no jugaba un counter!... el tremulous me consumía el poco tiempo que tengo para distracciones...)


Saludos

---

### Post by Mataca on 2007-09-19
Bueniiisimo la verdad que macromedia me alejaba de Ubuntu.. vamos a ver que onda Flash.

---

### Post by msangil on 2007-09-19
:) Grosssoooooooooo!!
Qué suerte que sigan mejorando!

Ya veníamos bien con la cantidad de programas disponibles para Ubuntu. Dentro de poco si seguimos así vamos a poder usar lo que venga.

Necesitás una milanesa y la emulás desde el Wine. Ha!

(Confieso que mi interés mayor en el Wine son los jueguitos. La verdad que por lo demás tengo todo lo que necesito en el Ubuntu.)

---

### Post by facundocorradini on 2007-09-20
> **msangil said:**
> :) Grosssoooooooooo!!
Qué suerte que sigan mejorando!

Ya veníamos bien con la cantidad de programas disponibles para Ubuntu. Dentro de poco si seguimos así vamos a poder usar lo que venga.


Sin duda, lo acabo de probar con unos aplicativos de gestión comercial que eran la única traba para pasar las maquinas de una empresa amiga, y salió andando a la perfección...

Decididamente, me parece que estamos cerca de la 1.0!!!

> 
Necesitás una milanesa y la emulás desde el Wine. Ha!

En realidad, wine no es un emulador....

> (Confieso que mi interés mayor en el Wine son los jueguitos. La verdad que por lo demás tengo todo lo que necesito en el Ubuntu.)

Eso es justo lo más dificil, sobre todo los juegos que usan directX (lo que usan OpenGL ya corren la mayoría)... pero bueno, tené en cuenta que muchas de las empresas están sacando los juegos nuevos con cliente para linux, y muchos juegos viejos están siendo portados...

---

### Post by por100pre1 on 2007-09-20
Para usar el mas reciente WINE para Feisty:

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 387EE263 && gpg --export --armor 387EE263 | sudo apt-key add -
```

```
sudo su -c 'echo deb http://wine.budgetdedicated.com/apt feisty main >> /etc/apt/sources.list'
```

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by msangil on 2007-09-20
> **facundocorradini said:**
> Sin duda, lo acabo de probar con unos aplicativos de gestión comercial que eran la única traba para pasar las maquinas de una empresa amiga, y salió andando a la perfección...

Decididamente, me parece que estamos cerca de la 1.0!!!


En realidad, wine no es un emulador....



Eso es justo lo más dificil, sobre todo los juegos que usan directX (lo que usan OpenGL ya corren la mayoría)... pero bueno, tené en cuenta que muchas de las empresas están sacando los juegos nuevos con cliente para linux, y muchos juegos viejos están siendo portados...

La verdad va a ser un placer. Al ritmo que viene esto creo que en un par de años más se terminó esto de tener una partición de otro OS por las dudas.

---

### Post by niko_3100 on 2007-09-21
Jaja es verdad espero que asi sea, yo lo tengo porque no me anda la impresora en ubuntu pero es un bajon ir a otro SO para imprimir y despues volver. Encima lo apuro tanto al otro SO que se me empieza a colgar y eso en linux no pasa me re acostumbre a la robustes de Lainux como dirian en el norte jajaj!!!

---

### Post by FlyerDie on 2007-09-21
> **niko_3100 said:**
> Jaja es verdad espero que asi sea, yo lo tengo porque no me anda la impresora en ubuntu pero es un bajon ir a otro SO para imprimir y despues volver. Encima lo apuro tanto al otro SO que se me empieza a colgar y eso en linux no pasa me re acostumbre a la robustes de Lainux como dirian en el norte jajaj!!!

Probaste de cargarle los drivers de la impresora en wine? ;)

---

### Post by niko_3100 on 2007-09-21
Je no estoy corto de tiempo y bastante ******* hoy si puedo lo hago, los drivers de xp supongo que tendrian que ir. Voy a probar, tiene algun cmoando especial apra meter los drivers en el wine?

---

