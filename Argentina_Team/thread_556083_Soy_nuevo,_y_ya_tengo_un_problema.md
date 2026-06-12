---
title: "Soy nuevo, y ya tengo un problema"
date: 2007-09-20
forum: Argentina Team
---

### Post by agvago on 2007-09-20
hola a todos, antes de nada quiero contarles que hace poco instalé Ubuntu, es más quiero decirles que es mi primera distribución de linux, así que imaginense que estoy re perdido, pero me gusta...

quien me paso este foro es faktorqm, así que le agradezco por la data, aunque ya se lo dije por mail...

ahora a lo feo, tengo un problema: no sé porque ni como empezó pero es asi...cuando intento ejecutar el gestionador de paquetes synaptic o cuando quiero actualizar la version de linux me aparece el siguiente mensaje:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

intenté hacer lo que dice pero no lo logro, ademas no se como configuro el usuario root(que me imagino que viene default) ni como hago para acceder con esta cuenta...

gracias

otra cosa, hay algun post qeu diga como compartir archivos entre win y linux, porque en la misma pc tengo los 2 sistemas y no sé como hacer, tengo una partición para guardar la data, pero desde linux es solo lectura y no la puedo cambiar...

saludos

---

### Post by facundocorradini on 2007-09-20
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

intenté hacer lo que dice pero no lo logro, ademas no se como configuro el usuario root(que me imagino que viene default) ni como hago para acceder con esta cuenta...

En ubuntu no hay usuario root, simplemente hay usuarios con permisos de administrador.

Para ejecutar un comando "como root" debes escribir 
sudo nombredelcomando       
por lo tanto, para arreglar este problema deberías escribir en una terminal 

sudo dpkg --configure -a

------------------------------------------------
Este problema puede averse generado al fallar una instalación... Te recomiendo que trates de usar siempre los repositorios de ubuntu, y mantengas al mínimo posible la cantidad de paquetes instalados mediante archivos .deb, y si puedes, evitar también repositorios externos...

> otra cosa, hay algun post qeu diga como compartir archivos entre win y linux, porque en la misma pc tengo los 2 sistemas y no sé como hacer, tengo una partición para guardar la data, pero desde linux es solo lectura y no la puedo cambiar...

Si es FAT32, supongo que debería montarla en tu home para que tengas permisos. Si es NTFS, entonces debes instalar un par de software adicionales... 
Decime de cual caso se trata así vemos como guiarte...

---

### Post by Montsegur87 on 2007-09-20
> **facundocorradini said:**
> En ubuntu no hay usuario root, simplemente hay usuarios con permisos de administrador.

Para ejecutar un comando "como root" debes escribir 
sudo nombredelcomando       
por lo tanto, para arreglar este problema deberías escribir en una terminal 
No.

```
nagel@desktop:~$ su root
Password: 
root@desktop:/home/andres#
```

---

### Post by agvago on 2007-09-20
GRACIAs!

tengo particiones NTFS,

ejecute el comando como me dijistes y dejo de aparecer ese mensaje, pero ahora no me deja abrir el gestor, ya que me dice que hubo un problema en la instalacion del virtual box(que por cierto quice instalar) y en el cuadro donde me aparece ese mensaje la unica opcion que tengo es de cerrar, y se me cierra el gestor hago eso mil veces y me pasa lo mismo. despues hice doble click en el paquete de virtual box y me dice o que no tengo los permisos o que esta dañado, los permisos los tengo, no sé que hacer porque no puedo instalar nada hasta que no arregle eso, que hago?

otro tema: me podes volver a explicar el tema este:

Te recomiendo que trates de usar siempre los repositorios de ubuntu, y mantengas al mínimo posible la cantidad de paquetes instalados mediante archivos .deb, y si puedes, evitar también repositorios externos...

no entendi nada, se nota que soy nuevo? jajaja, por ejemplo el otro dia me pedia actualizar y actualice todo lo que pedia, 

saludos

---

### Post by agvago on 2007-09-20
quiero comentar que solucioné el problema del gestor y la solucion la saque de esta página :
[http://www.ubuntu-es.org/index.php?q=node/46265](http://www.ubuntu-es.org/index.php?q=node/46265)
y esta es la solución posteada:

sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg - aviso, no se tendrá en cuenta el problema por estar activa
una opción --force:
El paquete está en un estado muy malo e inconsistente - debe reinstalarlo
antes de intentar desinstalarlo.
(Leyendo la base de datos ...
dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`virtualbox', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.
94408 ficheros y directorios instalados actualmente.)
Desinstalando virtualbox ...

en pocas palabras copia y ejecuta este código en la consola sudo dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by FlyerDie on 2007-09-20
> **facundocorradini said:**
> En ubuntu no hay usuario root, simplemente hay usuarios con permisos de administrador.

Para ejecutar un comando "como root" debes escribir 
sudo nombredelcomando     [http://ubuntuforums.org/newreply.php?do=newreply&p=3400406#](http://ubuntuforums.org/newreply.php?do=newreply&p=3400406#)
More  
por lo tanto, para arreglar este problema deberías escribir en una terminal 

sudo dpkg --configure -a


como que no?? =;

en todo linux tenes usuario root, y ubuntu no es la escepcion.
desde consola con "su -" y poniendo la password de root obtenes root :)

EDIT: no vi que montsegur87 ya habia dado respuesta :lolflag:

---

### Post by sajnox on 2007-09-21
Hola, sumando a lo que dijo Flyerdie, en Ubuntu hay un usuario root (sino como que no seria Linux) el tema es que por cuestiones de seguridad no tiene password, pero se lo podes habilitar sin problemas. Si recien empezas con Linux, no lo hagas!!! por algo los de ubuntu lo pusieron asi. El comando sudo alcanza y sobra.

Respecto al tema de la particion en ntfs, te la hago facil. Usa Automatix (instalador de paquetes) ya se que alguno de aca te lo puede insultar y con razon (solo usalo en cosas que otros te aconsejen, no te mandes a instalar todo lo que encuentres ahi, en algunos casos hubo problemas)

En resumen [www.getautomatix.com](www.getautomatix.com) y te lo instalas, ejecutas y buscas la funcionalidad de ntfs, automaticamente te gestiona las particiones ntfs para que las puedas escribir.

Si lo queres investigar y hacerlo mas largo descargate el paquete ntfs-3g con el synaptic e investiga el archivo fstab que es el que carga las particiones en el inicio.

Fijate cual te va mejor y cualquier duda postea.

Otra cosita, si podes editale el titulo a tu post por las dudas puntuales que tengas, por dejarlo asi confundis y ademas te perjudicas por que muchos no van a ver tu post. (esta todo bien !!! son los primeros y bienvenido!!!)

---

### Post by agvago on 2007-09-22
gracias sajnox!!! voy a ver que puedo hacer! jeje

---

