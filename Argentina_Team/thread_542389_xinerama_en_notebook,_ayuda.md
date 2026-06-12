---
title: "xinerama en notebook, ayuda"
date: 2007-09-03
forum: Argentina Team
---

### Post by zspikes on 2007-09-03
Buenas gente!!!
tengo una notebook con salida VGA, y queria saber si puedo usar un monitor extra para tener 2 monitores y dividir la pantalla en ambos monitores.
He toqueteado el xorg.conf hasta el cansancio pero sin resultados. Por eso me surgio la duda si soy yo, o directamente no se puede lo q yo quiero.

```
lgera@ameli:/etc/X11$ lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
```

alguna idea? gracias!!!

---

### Post by faktorqm on 2007-09-04
Hola, en esta pagina, que es de intel oficial digamos, dice que no se puede. 

[http://support.intel.com/support/graphics/intel945gm/sb/CS-022119.htm](http://support.intel.com/support/graphics/intel945gm/sb/CS-022119.htm)

Instalaste los drivers de intel? por que vi que los tipos estos tienen drivers para linux. 

En esta página, dice exactamente cómo se hace, para tu chip, y de dos maneras distintas (dinámica con xrandr y estatica con xorg.conf)

[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

En  otro lado dice:

"Dual head works but no OpenGL on the second display" pero es para edgy esto.

Parece que no hay mucha info, igual me costo encontrar las palabras claves para buscar mejor, pero son dualhead, dual-monitor, video clone. las que mas o menos arrojaron resultados "comprensibles". Salu2!!

---

### Post by zspikes on 2007-09-04
y yo q pensaba q sabia googlear jeje. Muy buena info faktorqm!!! pero algo no me cierra... se puede o no se puede con mi placa??
No recuerdo haber instalado ningun driver, tenia aceleracion grafica por defecto, asiq no toque nada.

La salida del comando xrandr -q me tira

```
gera@ameli:~$ sudo xrandr -q
 SZ:    Pixels          Physical       Refresh
*0   1280 x 800    ( 433mm x 271mm )  *60  
 1   1024 x 768    ( 433mm x 271mm )   60  
 2    800 x 600    ( 433mm x 271mm )   60  
 3    640 x 480    ( 433mm x 271mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

```

Segun el link q me diste, deberian salir las 2 salidas... la del monitor de la notebook y la salida VGA.
Q estoy haciendo mal?

Saludos y gracias!

---

### Post by FlyerDie on 2007-09-04
Mira, yo el dualhead lo he probado bajo windows y FUNCIONO...tanto a s-video como a VGA con ese chip.
En linux no supe como activarlo, ya que cuando conectaba tanto s-video como VGA me anulaba el video de la notebook, y salia por las salidas auxiliares.

---

### Post by faktorqm on 2007-09-05
y.... segun lo que dice la guia que te pase ayer, no te esta detectando el otro monitor, proba de iniciar la pc con los monitores enchufados, y corre el comando. si sigue sin detectartelo, proba de hacerlo por el xorg.conf. suerte con eso y saludos!!

---

### Post by zspikes on 2007-09-05
> **FlyerDie said:**
> Mira, yo el dualhead lo he probado bajo windows y FUNCIONO...tanto a s-video como a VGA con ese chip.
En linux no supe como activarlo, ya que cuando conectaba tanto s-video como VGA me anulaba el video de la notebook, y salia por las salidas auxiliares.

claro, mi duda es si se PUEDE. Porq si se puede, algun dia voy a descubrir como. Pero he intentado tantas cosas sin resultados positivos q me cabe la duda si es posible.
Ahora... a mi no me pasa q se me apaga la pantalla de la notebook... justamente ahora estoy viendo lo mismo en ambos monitores.

> **faktorqm said:**
> y.... segun lo que dice la guia que te pase ayer, no te esta detectando el otro monitor, proba de iniciar la pc con los monitores enchufados, y corre el comando. si sigue sin detectartelo, proba de hacerlo por el xorg.conf. suerte con eso y saludos!!

Como decia mas arriba, estoy con ambos monitores funcionando y el programa me sigue viendo uno solo... y me llegue a hartar de romper el xorg.conf. La verdad q no se q estoy haciendo mal... por eso me cabe la duda si es q de verdad se puede.

Voy a seguir intentando, cualquier novedad les comento, mil gracias a todos por la ayuda!!! :D

ACTUALIZANDO:

Definitivamente el xrandr no me ve la salida de VGA... por ahi me tiraron el dato q es problema de la configuracion de la X, porq lo unico q hace el xrandr es comunicarse con esta. Y me he leido tutoriales hasta el cansancio de como configurar el xorg.conf y no hay forma, no paro de romper... Me dice q no se detecta el screen o algo asi... la verdad q no se q estoy haciendo mal :(

---

### Post by zspikes on 2007-09-05
**ULTIMO MOMENTO!!!**

LO LOGREEEEEEEE!!!!!!!!!!!!!!!!!!! :D:D:D:D jaja, estoy re feliz!!!! en realidad no lo hice yo... tan solo copie y pegue de aqui [http://ubuntuforums.org/showthread.php?t=522233&page=2](http://ubuntuforums.org/showthread.php?t=522233&page=2)
Se siente medio feo q no haya sido esfuerzo propio, pero estoy demasiado feliz como para sentirme mal o como para entender q hice jaja XD ahora voy a jugar un poquito con esto del dual head y despues voy a ver q hice :P

Quedan unas cositas por arreglar... ahora necesito wallpapers mas grandes y configurar el cubo y todo eso jeje... 

Gracias a todos!!! estoy re feliz :P un abrazo!!!

---

### Post by faktorqm on 2007-09-06
te felicito men! ke lo disfrutes.:guitar:

---

### Post by zspikes on 2007-09-06
jeje, q si no lo estoy disfrutando :P le estoy mostrando a mis compañeros de facultad como funciona jeje.
Ahora se viene todo el tema de arreglar las resoluciones y todo eso. **Muchas gracias a todos!!!**

si pasa algun mod por aca q ponga el tema como solucionado, gracias n_n

---

