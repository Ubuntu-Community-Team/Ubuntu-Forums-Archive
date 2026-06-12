---
title: "Instalar drivers de NVIDIA"
date: 2007-03-11
forum: Argentina Team
---

### Post by matog on 2007-03-11
Hola gente. De nuevo molestando.

Quiero actualizar los drivers propietarios de nvidia para ver si puedo hacen funcionar beryl.

Me bajé los ultimos drivers de la pagina oficial, y cuando los quiero instalar, me dice que tengo que salir del servidor X. Perfecto.

Buscando con San Google encuentro varios lugares donde indicaban como hacer todo.
Seguí las instrucciones de [este]("http://ubunteroerrante.es/?p=51").

Hay dos problemas:

1- cuando apreto alt-ctrl-f1 no me abre ninguna consola. La tengo que abrir desde mi "acceso directo". Pero no creo uqe sea grave.
2- (este es el problematico) Cuando hago

```
sudo /etc/init.d/gdm stop
```

Se me cierra Gnome, me aparece la pantalla negra y el cursor titilando. Pero en ningun lugar está el 

```
mato@amd64:~$
```

O sea, tipeo pero apreto enter y nada....baja al renglon siguiente....

Gracias!

---

### Post by Mafber on 2007-03-11
Hola. Como estas?
cuando apretás alt-ctrl-f1 te tiene que abrir una consola pero que no es un vantano como la del acceso directo, sino que estas saliendo del modo grafico (de esto no estoy muy seguro que sea asi :(  ) pero que podes hacer lo mismo. 
Para los drivers, Beuno me pasó este [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") lo instalas y listo (son unos pocos pasos, pero faciles) baja los drivers más actualizados.
Suerte!!!

---

### Post by spg76 on 2007-03-11
Tiene razón Mafber, con Ctrl+Alt+F1 te abre el modo consola y no una ventana como en Gnome (para volver al modo gráfico Ctrl+Alt+F7).
Recién ahí tenes que tipear:
```
sudo /etc/init.d/gdm stop
```
Esto detiene el servidor gráfico y de esa manera podes instalar lo drivers.

---

### Post by matog on 2007-03-11
Ok, perfecto.
Pero con ctrl-alt-f1 no me abre nada....Hay alguna otra manera de llegar ahi?

---

### Post by felipelerena on 2007-03-11
> **matog said:**
> Ok, perfecto.
Pero con ctrl-alt-f1 no me abre nada...

¿eh? posta? proba con control + alt + F2

---

### Post by matog on 2007-03-11
Me baje el envy, y como siempre, se me termina cagando el servidor X o no se que cosa.
cuando reinicio, me aparece un cartel grande que dice que el servidor X no está configurado correctamente, y blah blah blah.
Probé todas las opciones posibles, y no pude volver a ver mi hermoso Gnome.

Estoy a punto de reinstalar porque estoy frustrado. Alguna solución?

Gracias!

---

### Post by jpmorelli on 2007-03-11
Podes probar reconfigurando nuevamente X ( que es el servidor gráfico ) y haciendo que te detecte las cosas solas , seguramente te va a poner el driver NV que es el driver para nvidia open source. Corre este comando:

sudo dpkg-reconfigure xserver-xorg

Suerte !

---

### Post by Mafber on 2007-03-12
No te frustre matog!!!! son cosas que pasan al principio (y después también :D )
Hace lo que dice jmorelli para reconfigurar el xorg.conf. Después instalá los drivers de alguna de estas manaras (todas son buenas) y todas te van a dejar usar Beryl:
1- vía automatic2 (la mas fácil)
2- vía el [script]("http://albertomilone.com/nvidia_scripts1.html") que te pasé
3- con la guía que tenés
Lo bueno de tu guía y del script es que te instalan los drivers actualizados.
Un concejo final: cuando te funcione la placa de video, hace una copia de seguridad de tu xorg.conf así en el futuro si se rompe algo del ese archivo vos lo reemplazas por tu backup y listo!!! 
Suerte!!!

---

### Post by matog on 2007-03-12
Funcionó el dpkg-reconfigure!!!! Me había olvidado de eso. Tiré miles de pero no el reconfigure.
Ahora bien.

-Si vuelvo a probar con el script, me volverá a pasar lo mismo? 
-En el automatix2 me fuguran los drivers de nvidia para desinstalar. Supone que los tengo instalados.
-Me olvide de comentar que tengo un Edgy eft AMD64

=============================================================================
=============================================================================
***_EDIT:_*** Desinstalé con el Envy, y volví a instalar, y funciona!!! Hasta funciona el Beryl!!!!

---

### Post by sessionip on 2007-03-12
fijate en[ http://www.argentilinux.com.ar/]("http://www.argentilinux.com.ar/") ahi hay una seccion sobre como configurar hardware NVIDIA

---

