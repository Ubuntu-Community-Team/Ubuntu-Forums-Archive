---
title: "Que Dock me aconsejan??"
date: 2007-07-01
forum: Argentina Team
---

### Post by Mauro22 on 2007-07-01
Hace un par de dias, luego de una actualizacion, el Kiba-Dock murió, e instale el avant-window-manager, todo lindo pero no puede entrar  a las preferencias, entonces lo saque.


Alguien usa otra, que sirva como launcher y windowslist ??


Salu2!

---

### Post by valucha on 2007-07-01
[COLOR="DarkOrchid"]http://www.vivalinux.com.ar/desktop/docks.html

fijate ahi si te gusta algunas de esas.[/COLOR]

---

### Post by Mauro22 on 2007-07-01
Gracias! :popcorn:

---

### Post by spg76 on 2007-07-01
Mauro, ¿instalaste la version svn 214 de avant-window-manager?
Te lo pregunto porque mejoró muchisimo en pocas semanas.
Podes encontrar más info en [http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository) y en [http://www.planetblur.org/hosted/awnforum/index.php](http://www.planetblur.org/hosted/awnforum/index.php)
Te adjunto una captura de como me quedó a mí.

---

### Post by jpmorelli on 2007-07-01
SPG76, ya que estamos, yo estoy usando AWN y me gustaría saber si me podés ayudar...
De donde sacaste ese fondo que parece como un estante de vidrio donde se apoyan los íconos y que tema de íconos estas usando porque yo uso uno tipo OSX pero la papelera se sigue viendo con ícono de Tango, thks.

---

### Post by spg76 on 2007-07-02
> **jmorelli said:**
> SPG76, ya que estamos, yo estoy usando AWN y me gustaría saber si me podés ayudar...
De donde sacaste ese fondo que parece como un estante de vidrio donde se apoyan los íconos y que tema de íconos estas usando porque yo uso uno tipo OSX pero la papelera se sigue viendo con ícono de Tango, thks.

El fondo es el mismo de siempre lo que pasa es que en la última versión se le agregó la posibilidad de darle un valor al angulo de los costados. Esto, combinado  a la configuración de colores y a los iconos "reflectivos" da esa onda Leopard. Este valor no se puede modificar desde las preferencias porque todavía no está agregado, así que hay que tocar el valor en gconf-editor. Después si queres te digo donde tocar en gconf-editor porque ahora estoy en el laburo.
En cuanto a los iconos, estoy usando el tema que está en [http://www.gnome-look.org/content/show.php/OSX?content=31618](http://www.gnome-look.org/content/show.php/OSX?content=31618), y otros iconos que le agregué yo.
Me pasaba lo mismo con la papelera y el problema es que el tema este no tiene un vinculo dinamico con el nombre del icono que usa awn. Para hacer esto anta al carpeta del tema (en general esta dentro de la carpeta .icons en el home) y tipea en una terminal:
```
ln -s user-trash-empty.png gnome-stock-trash.png
ln -s user-trash-full.png gnome-stock-trash-full.png
```
Reinicia awn y listo.
Espero que te sirva.
Saludos.

---

### Post by jpmorelli on 2007-07-02
> **spg76 said:**
> El fondo es el mismo de siempre lo que pasa es que en la última versión se le agregó la posibilidad de darle un valor al angulo de los costados. Esto, combinado  a la configuración de colores y a los iconos "reflectivos" da esa onda Leopard. Este valor no se puede modificar desde las preferencias porque todavía no está agregado, así que hay que tocar el valor en gconf-editor. Después si queres te digo donde tocar en gconf-editor porque ahora estoy en el laburo.
En cuanto a los iconos, estoy usando el tema que está en [http://www.gnome-look.org/content/show.php/OSX?content=31618](http://www.gnome-look.org/content/show.php/OSX?content=31618), y otros iconos que le agregué yo.
Me pasaba lo mismo con la papelera y el problema es que el tema este no tiene un vinculo dinamico con el nombre del icono que usa awn. Para hacer esto anta al carpeta del tema (en general esta dentro de la carpeta .icons en el home) y tipea en una terminal:
```
ln -s user-trash-empty.png gnome-stock-trash.png
ln -s user-trash-full.png gnome-stock-trash-full.png
```
Reinicia awn y listo.
Espero que te sirva.
Saludos.

Gracias, cuando lo cambie en casa te digo como me fué, por suerte es el mismo tema que estoy usando yo, y con respecto al valor en el gconf-editor si te acordás, genial !;)

---

### Post by Mauro22 on 2007-07-02
intente instalar el AWN SVN como dijo "spg76" pero tengo un error al hacer:

```
sudo apt-get install avant-window-navigator-svn
```

y es:

```
Desempaquetando libawn-svn (de .../libawn-svn_0.1.2-svn214_i386.deb) ...
dpkg: error al procesar /var/cache/apt/archives/libawn-svn_0.1.2-svn214_i386.deb (--unpack):
 intentando sobreescribir `/usr/lib/libawn.so.0.0.1', que está también en el paquete libawn0
Seleccionando el paquete avant-window-navigator-svn previamente no seleccionado.
Desempaquetando avant-window-navigator-svn (de .../avant-window-navigator-svn_0.1.2-svn214_i386.deb) ...
Se encontraron errores al procesar:
 /var/cache/apt/archives/libawn-svn_0.1.2-svn214_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Alguna sugerencia ??


saludos!!

---

### Post by spg76 on 2007-07-02
jmorelli, los datos que podes cambiar en gconf-editor son:
Para modificar los angulos de los costados: "apps>avant-window-navigator>bar>bar_angle". Yo lo tengo en 25.
Para modificar el tamaño de los iconos: "apps>avant-window-navigator>bar>bar_height". Yo lo tengo en 64.
Tenes que reiniciar awn para notar los cambios.
Después poder jugar un poco con la combinación de colores para que te quede como más te guste.
Saludos.

---

### Post by spg76 on 2007-07-02
> **Mauro22 said:**
> intente instalar el AWN SVN como dijo "spg76" pero tengo un error al hacer:

```
sudo apt-get install avant-window-navigator-svn
```

y es:

```
Desempaquetando libawn-svn (de .../libawn-svn_0.1.2-svn214_i386.deb) ...
dpkg: error al procesar /var/cache/apt/archives/libawn-svn_0.1.2-svn214_i386.deb (--unpack):
 intentando sobreescribir `/usr/lib/libawn.so.0.0.1', que está también en el paquete libawn0
Seleccionando el paquete avant-window-navigator-svn previamente no seleccionado.
Desempaquetando avant-window-navigator-svn (de .../avant-window-navigator-svn_0.1.2-svn214_i386.deb) ...
Se encontraron errores al procesar:
 /var/cache/apt/archives/libawn-svn_0.1.2-svn214_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Alguna sugerencia ??


saludos!!

Me pasó algo parecido y lo arreglé desde Synaptic. Creo que tenes que desinstalar "avant-window-navigator-svn" y "libawn-svn" y volver a instalarlos.
Si mal no recuerdo, Synaptic te avisa algo de un paquete roto cuando lo abrís.
Cuando haya una versión de nueva awn, instalala desde Synaptic porque también tuve problemas con el notificador de actualizaciones.
Espero que te sirva de algo (aunque no fui muy específico) :)

---

### Post by aceki on 2007-07-02
Gente yo la pude instalar y esta linda, ahora lo que no puedo es dejar activa, cuando cierro todas la aplicaciones se me va, hay alguna forma de dejarla activa y de agregarle atajos?

---

### Post by Mauro22 on 2007-07-02
Ya logrè instalar la AWN SVN pero me pasa lo mismo que con la otra, no abre el AWN preferences, entonces no se como modificarla a mi gusto, agregar cosas y eso.

Alguien sabe, si modifica un archivo o algo??

Salu2!

---

### Post by spg76 on 2007-07-02
> **aceki said:**
> Gente yo la pude instalar y esta linda, ahora lo que no puedo es dejar activa, cuando cierro todas la aplicaciones se me va, hay alguna forma de dejarla activa y de agregarle atajos?

Para agregarle lanzadores, arrastra los que quieras desde el menú de aplicaciones y deberían quedarte.

> **Mauro22 said:**
> Ya logrè instalar la AWN SVN pero me pasa lo mismo que con la otra, no abre el AWN preferences, entonces no se como modificarla a mi gusto, agregar cosas y eso.

Alguien sabe, si modifica un archivo o algo??

Salu2!

Mauro, según busqué en el foro de awn ([http://www.planetblur.org/hosted/awnforum/index.php?shard=forum](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum)) hay algunos usuarios que tuvieron el mismo problema. Lo que aconsejan en [este post]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=151") (aunque no dicen si funciona) es desinstalar totalmente awn y volver a instalarlo.
Podés desinstalarlo desde Synaptic, después pones en una terminal:
```
sudo rm /usr/local/bin/avant-preferences
sudo rm /usr/local/bin/avant-window-navigator
```
Y después volves a instalar desde Synaptic.
Insisto, no dicen que funcione pero no creo pierdas nada probando.
Saludos.

---

### Post by jpmorelli on 2007-07-03
> **spg76 said:**
> jmorelli, los datos que podes cambiar en gconf-editor son:
Para modificar los angulos de los costados: "apps>avant-window-navigator>bar>bar_angle". Yo lo tengo en 25.
Para modificar el tamaño de los iconos: "apps>avant-window-navigator>bar>bar_height". Yo lo tengo en 64.
Tenes que reiniciar awn para notar los cambios.
Después poder jugar un poco con la combinación de colores para que te quede como más te guste.
Saludos.

Muchisimas gracias, ya probé lo de la papelera y funcionó perfecto. Ahora estoy desesperado  por llegar a casa y poner el tema de los ángulos. Gracias ! :p

---

### Post by undiaperfecto on 2007-07-03
uy yo no entendi el tema de modificar los angulos, no se donde encontrar el archivo que hay que modificar.

---

### Post by Mauro22 on 2007-07-03
Bueno al final quedo ;)

Les comento lo que hice:

como dijo spg76, eliminè todo pero no paso nada, todo igual

Asi que antes de volverme loco :(, fui a Buscar archivos, puse "avant" y borre todo lo q incluia esa palabra.

Despues si, 
```
sudo apt-get install avant-window-navigator-svn
```


Y ahi si!!

Quedo joya, Gracias!!

---

### Post by Mauro22 on 2007-07-03
> uy yo no entendi el tema de modificar los angulos, no se donde encontrar el archivo que hay que modificar.

Apreta Alt+F2 para abrir la ventana de ejecutar y pone

```
gconf-editor
```

Despues extende apps, extende avant-window-navigator, extende bar y cambia los valores de angle y height


salu2

---

### Post by undiaperfecto on 2007-07-03
Buenisimo, ahi pude hacer lo del angulo y quedo perfecto, ahora me falta lo de que se reflejen los iconos, mas tarde la intento.

---

### Post by spg76 on 2007-07-03
> **undiaperfecto said:**
> Buenisimo, ahi pude hacer lo del angulo y quedo perfecto, ahora me falta lo de que se reflejen los iconos, mas tarde la intento.

Todavía no se pueden reflejar los iconos. Las capturas que ves son de iconos "reflectivos", es decir que simulan el reflejo.
Recién hoy sacaron un patch para agregarle a la próxima svn.
Así es como está quedando:

[[img]http://pix.nofrag.com/96/9e/b7fa3ceffce628fe05800a0d49bft2.jpg[/img]](http://pix.nofrag.com/96/9e/b7fa3ceffce628fe05800a0d49bf.html)

Saludos.

---

### Post by Mauro22 on 2007-07-03
Hay alguna forma de achicar los iconos.??

Salu2

---

### Post by jpmorelli on 2007-07-03
> **spg76 said:**
> Todavía no se pueden reflejar los iconos. Las capturas que ves son de iconos "reflectivos", es decir que simulan el reflejo.
Recién hoy sacaron un patch para agregarle a la próxima svn.
Así es como está quedando:

[[img]http://pix.nofrag.com/96/9e/b7fa3ceffce628fe05800a0d49bft2.jpg[/img]](http://pix.nofrag.com/96/9e/b7fa3ceffce628fe05800a0d49bf.html)

Saludos.

Con razón !!! me estaba volviendo loco leyendo el foro que posteaste al principio y veía que lo habían logrado pero no entendía nada que tenía que hacer, JUA !
Gracias por los consejos, cada vez me está que dando más grosaaa !!!

---

### Post by undiaperfecto on 2007-07-04
> **Mauro22 said:**
> Hay alguna forma de achicar los iconos.??

Salu2

Si, de la manera que pusieron mas arriba o en la pagina anterior, la que es para variar el angulo del dock, hay un valor que es para setear el tamaño de los iconos. Yo lo puse en 48 y me quedo barbaro.

---

### Post by spg76 on 2007-07-04
> **undiaperfecto said:**
> Si, de la manera que pusieron mas arriba o en la pagina anterior, la que es para variar el angulo del dock, hay un valor que es para setear el tamaño de los iconos. Yo lo puse en 48 y me quedo barbaro.

En realidad con ese valor cambias el tamaño de todo el dock. Por ahora, no se puede cambiar solo el tamaño de los iconos sin agrandar o achicar el dock.

---

### Post by spg76 on 2007-07-05
Para los interesados en AWN, acaban de sacar una versión con el patch para que se reflejen los iconos.
No es una svn "oficial" porque todavía lo están probando, asi que no lo van a encontrar en el repositorio svn de Ubuntu.
Si quieren probarlo (tengan en cuenta que puede tener varios bugs) pueden bajar los paquetes "avant-window-navigator-svn_0.1.2-svn214-2_i386.deb" y "libawn-svn_0.1.2-svn214-2_i386.deb" desde [http://download.tuxfamily.org/syzygy42/static/misc/packages/awn214reflect](http://download.tuxfamily.org/syzygy42/static/misc/packages/awn214reflect). Para instalarlo tienen que hacer:
```
sudo dpkg -i avant-window-navigator-svn_0.1.2-svn214-2_i386.deb libawn-svn_0.1.2-svn214-2_i386.deb
```
Y tienen que modificar en gconf-editor el valor de apps>avant-window-navigator>bar>icon_offset por el que más les guste.
Saludos.

EDIT: Estos debs tenían un problema con el consumo de memoria. Si alguno los bajó, puede actualizarlos desde el mismo lugar y solucionar este problema.

---

### Post by undiaperfecto on 2007-07-17
Yo instale la que esta en los repositorios de ubuntu y funciono.
Para que se reflejen hay que setear con gconf-editor
/apps/avant-window-navigator/bar/bar_angle                  45
/apps/avant-window-navigator/bar/icon_offset                 18

Despues reinicias awn y queda de pelos!!!

---

### Post by spg76 on 2007-07-17
> **undiaperfecto said:**
> Yo instale la que esta en los repositorios de ubuntu y funciono.
Para que se reflejen hay que setear con gconf-editor
/apps/avant-window-navigator/bar/bar_angle                  45
/apps/avant-window-navigator/bar/icon_offset                 18

Despues reinicias awn y queda de pelos!!!

Los repositorios de Ubuntu de reocard ahora tienen la última versión svn de awn, así que más actualizados no pueden estar.
Ahora el proyecto tiene varios colaboradores (antes tenía solo un desarrollador), por lo que está avanzando bastante.
Hoy, por ejemplo, pusieron un patch que agrega otros efectos cuando uno pasa el mouse por los iconos (en lugar del rebote).

---

### Post by undiaperfecto on 2007-07-18
Para mi es barbara awn, solo le falta el efecto de cuando le pasas por arriba con el mouse, se agiganten como en mac osx

---

### Post by Ptero-4 on 2007-08-02
Un par de preguntas sobre el AWN:

1) De donde se descargan las fuentes de SVN?

2) Esas fuentes tienen el patch para la reflectividad?

3) Hay un patch para el zoom (que los iconos se agranden al pasar el mouse sobre estos)?

4) Como se agregan los lanzadores, y permanecen estos en el dock después de cerrarlo y volverlo a abrir?

5) Es posible mover los lanzadores?

6) Es posible lanzar URI´s como computer:/// (el icono ´Equipo´ de gnome) desde AWN?

7) Y es posible desactivar la porción que gestiona los programas abiertos, para que solo queden los lanzadores y la papelera?

---

### Post by spg76 on 2007-08-02
> **Ptero-4 said:**
> Un par de preguntas sobre el AWN:

1) De donde se descargan las fuentes de SVN?

2) Esas fuentes tienen el patch para la reflectividad?

3) Hay un patch para el zoom (que los iconos se agranden al pasar el mouse sobre estos)?

4) Como se agregan los lanzadores, y permanecen estos en el dock después de cerrarlo y volverlo a abrir?

5) Es posible mover los lanzadores?

6) Es posible lanzar URI´s como computer:/// (el icono ´Equipo´ de gnome) desde AWN?

7) Y es posible desactivar la porción que gestiona los programas abiertos, para que solo queden los lanzadores y la papelera?

1) Awn acaba de mudar su código a Launchpad. La página del proyecto es [https://launchpad.net/awn/](https://launchpad.net/awn/) y ahí te dice como compilar desde la fuente (que ahora es bzr por bazaar en lugar de svn).

2) Si ya está integrado. De todas maneras, la forma más sencilla de instalar la versión más reciente es desde el repositorio de Ubuntu de reocard que está muy actualizado (para darte una idea hoy ya se actualizó con la última bzr). Si queres podes ver un pequeño tutorial que puse en mi blog en [http://ubuntu76.wordpress.com/2007/07/18/instalar-y-configurar-awn-en-ubuntu-704/](http://ubuntu76.wordpress.com/2007/07/18/instalar-y-configurar-awn-en-ubuntu-704/)

3) Aún está en desarrollo. Se está discutiendo que tipo de efectos agregarle (además del zoom) así que seguramente en las próximas semanas habrá alguna novedad.

4) Para agregarle lanzadores, los podés arrastrar desde el menú "Aplicaciones" o desde cualquier lanzador personalizado que tengas. También podés arrastar programas desde "/usr/share/applications".
Si, los lanzadores permanecen en el dock si lo cerras y volves a abrir.

5) Si, se pueden mover desde el menú de lanzadores (que accedes con el botón derecho) aunque la idea es que proximamente se haga arrastrando y soltando.

6) La verdad que no sé, pero creo que si. Ahora estoy en el laburo (lease en Windows) pero si después puedo, lo pruebo y te comento.
EDIT=Recién lo probé y un lanzador de "Equipo" de Gnome se puede poner. Lo único es que, como cualquier lanzador que abra Nautilus no se puede controlar desde el lanzador sino que te abre otra tarea.
Para otros lugares, siempre podes crear una carpeta con lanzadores y arrastar hasta el dock. Por ejemplo uno que diga nautilus "/home/usuario/documentos/" te abriría esa carpeta en Nautilus. 

7) Por ahora, no. Pero como  es algo que muchos lo piden pronto se podrá.

Espero que te sirva.

EDIT=Recién subieron al repositorio la última versión con el nuevo applet llamado "Stack" basado en Mac OS X Leopard. Dejó una captura.
Saludos.

---

### Post by Ptero-4 on 2007-08-03
spg76: cuando dices que los lanzadores que abren nautilus no se controlan desde el lanzador sino que abren otra tarea. que significa en terminos simples?

P.d: la pregunta 4 era porque la última version de awn que probé traía un bug que inutilizaba el dialogo de agregar lanzadores y hacía que los lanzadores desaparecieran cuando cerrabas awn.

---

### Post by spg76 on 2007-08-03
> **Ptero-4 said:**
> spg76: cuando dices que los lanzadores que abren nautilus no se controlan desde el lanzador sino que abren otra tarea. que significa en terminos simples?

P.d: la pregunta 4 era porque la última version de awn que probé traía un bug que inutilizaba el dialogo de agregar lanzadores y hacía que los lanzadores desaparecieran cuando cerrabas awn.

Te pongo un ejemplo, si tenes un lanzador de tu Carpeta Personal te abre Nautilus en ese lugar, pero te agrega una tarea al costado, es decir que para minimizar esa carpeta tenes que hacerlo desde la tarea que te abrió y no desde el lanzador. Si presionas nuevamente el lanzador te abre otra vez la carpeta y te agrega otra tarea, y asi sucesivamente.
La diferencia con los otros lanzadores es que por ejemplo si tenes uno de Firefox lo podes abris, minimizar, maximizar y cerrar desde el propio lanzador. Espero no haberte mareado :)
En cuanto a lo otro, lo único que te puedo decir es que Awn mejoró mucho en estabilidad y funcionalidades en las últimas versiones, asi que la única manera de saberlo es probándolo.
Saludos.

---

### Post by Ptero-4 on 2007-08-03
No importa lo de las tareas, de todas maneras no puedo usar AWN hasta que el modulo de tareas sea opcional.

---

