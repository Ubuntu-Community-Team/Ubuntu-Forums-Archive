---
title: "Espacio libre del disco: ¿Con que lo ven?"
date: 2007-02-27
forum: Argentina Team
---

### Post by clasificado on 2007-02-27
¡Buenas de nuevo a todos! Despues de un par de semanas, vuelvo por estos lares :D

Antes que nada: KUBUNTU. KDE. El lado Konqueror de la vida.

Queria saber su opinion, linuxeros: **¿Como saben cuanto espacio libre les queda en el disco HDD?** ¿Que usan para ver ese numero maldito?

Soy un usuario de disco pequeño (40gb) y recien venido de Windows, Nunca me privé de tener instalados medio millon de boludeces y el emule a todo lo que da. Aunque eso me llevó a tener muy de cerca el espacio libre de mi disco (dia por medio la situacion en crisis).

Desde que llegué a Linux me pareció que me faltaba ese numero en Konqueror: No encontré algo similar a "Disco C" donde darle bton derecho o mirar ahi en la barra de estado.

Encontré tres alternativas a ver cuando explota todo:
1) El comando de consola **df** que hace directamente este trabajo
```

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hdc1             37357096  30779800   4679620  87% /
varrun                  192912        92    192820   1% /var/run
varlock                 192912         0    192912   0% /var/lock
procbususb               10240        96     10144   1% /proc/bus/usb
udev                     10240        96     10144   1% /dev
devshm                  192912         0    192912   0% /dev/shm

```

2) El programa **KDiskFree**, que muestra basicamente lo mismo, aunque bonito. A eso le suma los puntos de montaje del fstab; y si estan montados: el espacio libre de esos recursos (inclusive SMB: Carpetas Windows a traves de la red, cosa que me vino muy bien)
[img]http://serv2.imagehigh.com/imgss/5230267_KDiskFree.png[/img]

3) El **KwikDisk**, de los creadores de KDiskFree, se queda en el tray y me tira un cartelito cuando se está llenado el asunto (cualquiera sea). Tambien al hacer click en el recurso lo monta o lo desmonta, segun el caso (Instruccion que es personalizable por recurso)
[img]http://serv2.imagehigh.com/imgss/5230288_KwikDisk2.png[/img]

Muy lindo, muy util, todo lo que vos quieras. Ahora: ¿Tanto quilombo para saber mi espacio libre? 

Algo tengo que estar pensando mal :D

Clasificado.

---

### Post by beuno on 2007-02-28
En gnome la vida es asi:

---

### Post by kowal on 2007-02-28
Como está señor Clasificado!, siempre tan pintorescos sus posts.

¿Cómo miro el espacio libre? A ver..

1) Cuando estoy en la consola ([yakuake](http://yakuake.uv.ro/), por supuesto :) ) uso efectivamente el comando **df** pero con la opción **-h** (para seres **h**umanos): **df -h**

2) En mi escritorio tengo un applet de [Superkaramba](http://www.kde-look.org/index.php?xsortmode=high&page=0) que muestra varias estadísticas del sistema (entre ellas, el espacio libre de las unidades). Si no se cuenta con mucho hard se puede usar conky, adesklets, etc.

3) Existe una aplicación llamada [Filelight](http://www.kde-apps.org/content/show.php?content=9887) (otra que está en los repos: sudo aptitude install filelight) que muestra de manera gráfica y cómoda como se ocupa el espacio en nuestro rígido.. *muy recomendable y útil*, a pesar de que el autor le da poca bola y quedó con algún que otro bug.

4) Dolphin (el sucesor de Konqueror como gestor de archivos en KDE4) muestra el porcentaje de espacio libre de la unidad que se esté navegando (sudo aptitude install dolphin)

No se me ocurren más por ahora ;)

Saludos!

---

### Post by magicfab on 2007-02-28
df -h me sirve más. Explora sus opciones con man df .

No conozco mucho de KDE, gracias por compartir lo que encontraste. 

A veces me parece más fácil usar particionadores como gparted para ver espacio disco físico disponible por particiones.

En gnome-utils también hay baobab y buscando encontré gtkdiskfree.

---

### Post by joselin on 2007-02-28
> **beuno said:**
> En gnome la vida es asi:

O asi:

---

### Post by clasificado on 2007-02-28
> **beuno said:**
> En gnome la vida es asi:

¡Punto para Gnome!

Clasificado.

---

### Post by zspikes on 2007-02-28
estoy de acuerdo... yo en gnome uso el Gpart q es comodisimo. no se q onda kde.

---

### Post by felipelerena on 2007-02-28
soy gnomero y te recomendaria hacer
> sudo aptitude install ubuntu-desktop
pero qparted es una gran opcion
o hacer la gran
> sudo aptitude install baobab (que viene si instalas gnome)

---

### Post by clasificado on 2007-02-28
> **felipelerena said:**
> soy gnomero y te recomendaria hacer **sudo aptitude install ubuntu-desktop**

¡Pero que poco tolerante! 

Por otra parte... eso me sacaría de encima todos los problemas que tengo con el KDE (aunque no se porqué tengo la impresión de que me instalaría todos los problemas de Gnome :P)

¿Y como es ese baobab? Ahora me dejaste con la curiosidad...

Clasificado

---

### Post by joselin on 2007-03-01
> **clasificado said:**
> 
¿Y como es ese baobab? Ahora me dejaste con la curiosidad...


Es el screenshot que anjunte en mi mensaje anterior.

Mas info y mas screenshots: [http://www.marzocca.net/linux/baobab.html](http://www.marzocca.net/linux/baobab.html)

---

### Post by Nemesis Teufel on 2007-03-01
No entendi bien o es muy sencilla la cosa? 
Yo para fijarme cuanto espacio me queda selecciono mi disco con el boton secundario y voy a propiedades donde me dice la informacion completa de mi disco.

---

### Post by clasificado on 2007-03-01
> **Nemesis Teufel said:**
> No entendi bien o es muy sencilla la cosa? 
Yo para fijarme cuanto espacio me queda selecciono mi disco con el boton secundario y voy a propiedades donde me dice la informacion completa de mi disco.

:shock: ¿Y como haces eso en un Konqueror? ¿O con qué lo haces? 

¿Lo tuyo es en KDE? (yo hablo de KDE) 
¿Adjuntarias un screenshot? ¡Yo no lo encuentro!

Acá va el Konqueror: El navegador de archivos por defecto en Kubuntu, al cual no le encuentro ese numerito
[[IMG]http://serv2.imagehigh.com/imgss/5240105_konqueror.th.png[/IMG]](http://serv2.imagehigh.com/imgss/5240105_konqueror.png)

---

### Post by Nemesis Teufel on 2007-03-01
> **clasificado said:**
> :shock: ¿Y como haces eso en un Konqueror? ¿O con qué lo haces? 

¿Lo tuyo es en KDE? (yo hablo de KDE) 
¿Adjuntarias un screenshot? ¡Yo no lo encuentro!

Acá va el Konqueror: El navegador de archivos por defecto en Kubuntu, al cual no le encuentro ese numerito
[[IMG]http://serv2.imagehigh.com/imgss/5240105_konqueror.th.png[/IMG]](http://serv2.imagehigh.com/imgss/5240105_konqueror.png)

No, fijate que mi info dice que tengo Ubuntu 6.10. ¿Querés que te pase screen de como lo hago de todas formas?

---

### Post by Tinchio on 2007-03-03
> **clasificado said:**
> :shock: ¿Y como haces eso en un Konqueror? ¿O con qué lo haces? 

¿Lo tuyo es en KDE? (yo hablo de KDE) 
¿Adjuntarias un screenshot? ¡Yo no lo encuentro!

Acá va el Konqueror: El navegador de archivos por defecto en Kubuntu, al cual no le encuentro ese numerito
[[IMG]http://serv2.imagehigh.com/imgss/5240105_konqueror.th.png[/IMG]](http://serv2.imagehigh.com/imgss/5240105_konqueror.png)


En Konqueror muy facil tambien, boton derecho sobre la unidad en cuestion y vas a propiedades, ahi te dice, mira la foto

---

### Post by clasificado on 2007-03-05
> **Tinchio said:**
> En Konqueror muy facil tambien, boton derecho sobre la unidad en cuestion y vas a propiedades, ahi te dice, mira la foto

**¿Sabes que tenés razón?** ¡GRANDE TINCHIOOOOOO!, ¡CAPO TINCHIO!

Al primer momento, pensé "Este salame me muestra su disco montado en [/media/Fat32], ¡y yo quiero saber del disco montado en [/]!"

Ahi fue cuando todo se me conectó: ¡¡Todo el disco está montado sobre [/]!!

Asunto resuelto: puse [/] en la casilla de dirección, le di bton derecho sobre el fondo blando. **y ahi estaba** (¡Punto para Tinchio!)

Mirando un rato mas tu screenshot, apareció un detalle más: Siempre, las propiedades de una carpeta cualquiera perteneciente a un montaje, me informan del espacio libre de dicho montaje.

Mirá.
[img]http://serv2.imagehigh.com/imgss/5288231_konqueror.conespaciolibre.png[/img]

Gracias a todo el equipo ULUGA

---

### Post by Nemesis Teufel on 2007-03-07
De nada! (??)

Al final es igual q en gnome..no?

---

