---
title: "pregunta basica sobre copiar archivos"
date: 2007-02-05
forum: Argentina Team
---

### Post by undiaperfecto on 2007-02-05
resulta que estuvetratando de cambiar el aspecto del grub con este tutorial
[http://www.cesarius.net/como-cambiar-la-imagen-del-grub-en-ubuntu/](http://www.cesarius.net/como-cambiar-la-imagen-del-grub-en-ubuntu/)
pero no hay manera de copiar el archivo message.ubugry en el directorio /boot/grub/
probe con el comando sudo cp y me salto esto:

sudo cp message.ubugrey /boot/grub/
cp: no se puede efectuar `stat’ sobre `message.ubugrey’: No existe el fichero ó directorio

en ese mismo tutorial recomiendan hacerlo con el modo grafico, cosa que tampoco me deja porque no tengo permisos para escribir en esa carpeta.

se que no es laaaaa pregunta dificil, pero me comio la cabeza toda la mañana y no pude resolverla. gracias gente.

---

### Post by marianom on 2007-02-05
¿Estas en el lugar indicado para copiarlo? Que yo sepa ese error solo puede ser porque el archivo no existe.

Si hacés un ls message*, que devuelve?

---

### Post by spg76 on 2007-02-05
`message.ubugrey&#8217; se refiere al archivo del tema que queres instalar.
Tenes que tener ese archivo (o del tema que elijas) y abrir una terminal en su ubicación y ejecutar ahí el comando:
```
sudo cp message.ubugrey /boot/grub/
```
Tenes que cambiar 'message.ubugrey' por el archivo que tengas.
El tema al que se refiere el  HOWTO que nombras lo podes bajar desde [http://www.gnome-look.org/content/show.php?content=43166](http://www.gnome-look.org/content/show.php?content=43166)

---

### Post by undiaperfecto on 2007-02-05
si eso mismo hice, me baje el tema, lo descomprimi en el escritorio y abri un terminal en esa ubicacion y me tira ese error.
el tema es como que no tengo acceso al directorio /boot/grub/

otra cosa, probe un ls message* y me sale que no existe el archivo, pero esta ahi en el escritorio, eso es lo que no entiendo.

---

### Post by marianom on 2007-02-05
Hace un post con el código completo donde haces un ls del desktop y el error. Vamos a verlo más detenidamente.

---

### Post by undiaperfecto on 2007-02-05
me sale esto:

[IMG]http://img251.imageshack.us/img251/4097/logxc5.jpg[/IMG] [[IMG]http://img251.imageshack.us/img251/9533/pantallazokm7.th.png[/IMG]](http://img251.imageshack.us/my.php?image=pantallazokm7.png)

---

### Post by marianom on 2007-02-05
Raro, yo tengo Desktop como subdirectorio de home:

```
mariano@mishima:~/Desktop$ pwd
/home/mariano/Desktop
mariano@mishima:~/Desktop$ ls
bar-001a1a806f.desktop  frobate-00eada1cb9.desktop  JDeveloper.desktop
bar-00bfb4eeaa.desktop  gegl-00448b352b.desktop     Sql Developer.desktop
foo-00a6345842.desktop  gegl-00a70f33cb.desktop

```

Supongo que vos no, es correcto?

---

### Post by undiaperfecto on 2007-02-05
ahi pude solucionarlo.
lo que hice fue copiar el archivo message.ubugrey en la carpeta personal, no en el escritorio
y desde el terminal fui a mi carpeta, hice un ls y me salia el contenido de esa carpeta, la copie con sudo cp y se copio sin problemas.
gracias por la magia!!!

---

