---
title: "Arreglando mplayer en Ubuntu Gutsy"
date: 2008-03-22
forum: Argentina Team
---

### Post by nevermind85 on 2008-03-22
Escribo esto porque me pareció interesante como solucion a un par de problemas de mplayer en **Ubuntu Gutsy** .

**Problema:**
Las versiones de Mplayer que se pueden instalar en Ubuntu Gutsy presentan dos errores o bugs:
a) cuando abrimos un archivo de video directamente, mplayer devuelve un error de "**Failed to open file**" y muestra la URI del archivo sin parsear correctamente (ej: file:///home/nevermind/videos/agua%20y%20mar.avi/).
b) cuando pausamos un video o la reproducción se detiene, aparece un cartel de error que dice únicamente "**gnome_screensaver_control()**".

Estos, si bien son dos problemas diferentes y aislados, son los dos bugs que encontramos en el mismo programa en la misma distribución, por lo que les mostraré como solucionarlos a ambos. Desde luego que cada solución puede aplicarse por separado.

**Solución:**
a) Cuando nos ponemos a revisar las versiones, encontramos que el paquete mplayer actualmente instalado es la "**2:1.0~rc2-0ubuntu1~gutsy1 (gutsy-backports)**", en teoría este debería solucionar el problema b) ya que es la versión que vendrá con Ubuntu Hardy Heron, en la cual los bugs del screensaver estarán arreglados.
Vamos entonces a forzar este paquete a una versión anterior: la "**2:1.0~rc1-0ubuntu13.1 (gutsy-updates)**". Con esta podremos abrir nuestros archivos directamente desde Nautilus.

Para forzar la versión anterior, se puede hacer mediante Synaptic (Menú Paquete-> Forzar Versión...); o desde línea de comandos:
```

sudo apt-get install mplayer=2:1.0~rc1-0ubuntu13.1

```Automáticamente nos aparecerá el Notificador de Actualizaciones indicando que existe una nueva versión de mplayer en los repositorios, lógico, pues acabamos de desactualizarlo. Al final les mostraré como evitar que esta notificación nos siga molestando.

b) Esta versión anterior, en realidad no cambia demasiado a la nueva salvo por el hecho de que anda. Pero, seguimos con el otro problema: cada vez que la reproducción del video se detiene, el molesto cartel de error aparece sin muchas más explicaciones.

Hay dos posibles soluciones; la más fácil es desactivando la opción de control del protector de pantalla en las preferencias (Mplayer -> Preferencias -> Misc -> desmarcar "Stop XScreenSaver"), pero con esto, si nos gusta que nuestro monitor deslumbre a nuestros amigos con las bonitas figuras que se generan en períodos de inactividad; es posible que el protector se active mientras estamos cómodamente en la cama viendo una película. Y no da tampoco para estar activando y desactivando el Screensaver por cada video de más de 10 minutos que queramos ver o estar moviendo frenéticamente el mouse durante toda toda la saga del Señor de los Anillos.
Vamos entonces a evitar que mplayer nos muestre esa ?advertencia?. Sin embargo esto resulta un tanto mas complicado de lo que suena.

Tendremos que toquetear el código fuente de mplayer y luego recompilarlo. Pero no se asusten porque es bastante más simple de lo que parece. Vamos paso por paso:

1) Abrimos una terminal nos hacemos root y empezamos a bajar todo lo necesario:
```

sudo -i
cd /tmp/
apt-get -d source mplayer
dpkg-source -x mplayer*.dsc
cd mplayer-1.0~rc1/
gedit libvo/gnome_screensaver.c

```Esto nos bajará el código fuente de la versión de mplayer que tenemos instalada actualmente, lo descomprimirá y por último abrirá Gedit con el archivo que tendremos que modificar.

2) Vamos a la línea 59 y cambiamos:
```
 cookie, G_TYPE_INVALID);
```por
```
 cookie, G_TYPE_INVALID, G_TYPE_INVALID);
```Guardamos y cerramos Gedit.

3) Sólo nos queda recompilar nuestro paquete, por desgracia esto requiere de muchísimas dependencias vamos a instalarlas y luego quitarlas pues no nos harán más falta:
```

apt-get install build-essential sharutils liblzo-dev gawk libsmbclient-dev libxv-dev libcdparanoia0-dev libxvidcore4-dev libdv-dev liblivemedia-dev em8300-headers libdvdread-dev libdts-dev libtheora-dev libxxf86dga-dev libxxf86vm-dev liblame-dev libxvmc-dev libggi2-dev libspeex-dev libfribidi-dev libfaac-dev libaa1-dev libcaca-dev libx264-dev ladspa-sdk libaudio-dev
dpkg-buildpackage -r

```Podemos ir a tomar una taza de café, pues el proceso de recompilado demora unos minutos. Vale aclarar que si obtienen un mensaje de error por dependencias luego de ejectuar dpkg-buildpackage, simplemente instalen las que falten con apt-get install.

4) Terminada la compilación, podemos borrar todas las dependencias que instalamos:
```

apt-get remove sharutils liblzo-dev gawk libsmbclient-dev libxv-dev libcdparanoia0-dev libxvidcore4-dev libdv-dev liblivemedia-dev em8300-headers libdvdread-dev libdts-dev libtheora-dev libxxf86dga-dev libxxf86vm-dev liblame-dev libxvmc-dev libggi2-dev libspeex-dev libfribidi-dev libfaac-dev libaa1-dev libcaca-dev libx264-dev ladspa-sdk libaudio-dev

```Notarán que no quité el paquete build-essential, pueden hacerlo si quieren, pero es realmente útil dejarlo y no ocupa demasiado.

Como resultado de todo esto, tendremos en /tmp un bonito grupo de cuatro archivos .deb listos para instalarse. En realidad solo necesitamos el de mplayer ya que los demás son de mencoder y documentación:
```

cd ..
dpkg -i mplayer_1.0~rc1-0ubuntu13.1_i386.deb

```Listo!, ya tenemos nuestro mplayer perfectamente funcional y sin carteles molestos. Un paso adicional ahora sería necesario para decirle a Ubuntu que no actualice nuestro trabajo y no nos moleste a cada rato con que hay una nueva versión. Para ello simplemente tendremos que bloquear el paquete e la versión actual.

Se puede hacer perfectamente desde Synaptic (Menú Paquete -> Bloquear Versión), pero si quieren es más rápido por línea de comandos:
```

echo mplayer hold | dpkg --set-selections

```Y cuando queramos actualizar a una nueva versión (evidentemente posterior a la que tiene errores):
```

echo mplayer install | dpkg --set-selections

```Eso es todo, espero que les sirva.

---

### Post by Mafber on 2008-03-23
Gracias por la info
Ya no lo usaba más el mplayer porque siempre me tiraba algún error y me molestaba muchísimo.
Voy a seguir los pasos que marcas y veo si puedo volver a usar este gran reproductor.
Muy bueno y muy completo :)

---

### Post by UBUjuan on 2008-03-23
Estuve intentando, ya baje el codigo fuente, pero no tengo el archivo libvo/gnome_screensaver.c a alguien le sucedío lo mismo?

---

