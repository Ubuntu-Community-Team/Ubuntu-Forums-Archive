---
title: "Testeando Gutsy gibbon"
date: 2007-09-10
forum: Argentina Team
---

### Post by DuckMan on 2007-09-10
bueno, acabo de pasarme a gutsy en mi maquina de escritorio, osea la q no uso para cosas serias (?). Solo tuve problemas con un paquete llamado libgpod2 , y por ende no puedo tener el amarok funcionando, pero el resto anda perfecto. Para que funcione el compiz, saque todos los paquetes q tenia antes y los volvi a instalar con los repositorios que vienen de gutsy y anda al pelo.

Como cosas interesantes que encontre mirando asi nomas, veo q agruparon la parte de "temas" en una sola aplicacion, agrupando letra, fondos, ventanas, iconos y Efectos de Escritorio :O

Todavia no veo donde puedo editar el XORG de manera grafica, si alguien lo sabe q lo diga :P

La experiencia para actualizar fue.. normal, no muy amigable pero no espero q lo sea a esta altura todavia .. ya q tuve q ejecutar varios dist-upgrades y demases para q me tome todos los paquetes, por alguna razon misteriosa

si alguien actualizo q ponga sus opiniones, y las cosas lindas q le encontro

---

### Post by tzulberti on 2007-09-11
Yo lo probe este finde, y tuve un par de problemas:
-> Las fonts no se veian bien
->M habia detectado mal la resolucion de la placa de video..

Me habia bajado Gutst Tribe 5.

Saludos,
TZ

---

### Post by facundocorradini on 2007-09-11
Yo lo probé hace tres días, directamente desde el live CD. 

Me andubo increiblemente bien, las características nuevas están muy buenas, y el reconocimiento de hardware es mil veces superior, al menos en mi experiencia.

Lo probé en la laptop de mi hno, conocida por su máxima incompatibilidad: en feisty no detectaba la placa de red, la de video, la de sonido ni el touchpad (q grandes los de dell...) y tubimos que hacer mil malabares para que andubieran.

En Gutsy todo andubo automáticamente...

---------------------------------
En fin, todo esto no hizo más que ponerme aún más ansioso para la final release de gutsy..

---

### Post by spg76 on 2007-09-11
> **DuckMan said:**
> Todavia no veo donde puedo editar el XORG de manera grafica, si alguien lo sabe q lo diga :P

Está en el menú "Sistema > Administración > Screen and Graphics Preferences".
Esta opción la agregaron en "Tribe 5" hacia que si tenés alguna versión anterior, no la vas a ver.

---

### Post by DuckMan on 2007-09-11
en teoria tengo lo "ultimo" , actualice desde apt , cuando este en mi casa la busco, gracias spg76

el unico tema q tuve con las fonts, esq las cambio mas grande, fui al menu de fuentes y las achique, y quedo como antes

---

### Post by Gideon26 on 2007-09-11
Yo estoy usando la gutsy y anda al pelo 0 problemas, hasta con el amarok cero problemas lo instale de una y anduvo  no tuve que copilar nada de drivers como los de alsa y eso anduvieron de una salvo los de nvidia que tuve que instalar yo lo drivers privativos pero despues joya. Otra cosa hoy me di cuenta que en gutsy me deja escribir en la particion NTFS, y yo en eso no toque nada se ve que ya lo hace de default. 

tampoco pude colocar avant-window-manager lo instale (svn) pero no me corre al  igual que kibadock


Saludos!!

---

### Post by vk-cdg on 2007-09-11
Que tal anda la escritura en NTFS?
La pregunta viene a que en el trabajo, como es un entorno corporativo todas las estaciones son XP y por ende la mia tiene los dos operativs instalados. No quise nunca probar de escribir en la particion NTFS por temor a romper el archivo o algo del filesystem, pero me imagino que si Gusty lo trae de serie debe estar lo bastante estable como para confiar no?

Hiciste alguna prueba de grabar algún archivo y luego verlo desde Win?

---

### Post by Mauro22 on 2007-09-11
Una pregntita de novato, ya que abrieron el tema del Gusty Gibbon


Como la mayoria estoy usando Feisty Fawn, el mes que viene cuando salga Ubuntu G.G, si yo la quiero tener, hay que bajarla e instalar todo de cero o Feisty Fawn se actualiza a la nueva version 


:confused::confused:

---

### Post by beuno on 2007-09-11
> **Mauro22 said:**
> Una pregntita de novato, ya que abrieron el tema del Gusty Gibbon


Como la mayoria estoy usando Feisty Fawn, el mes que viene cuando salga Ubuntu G.G, si yo la quiero tener, hay que bajarla e instalar todo de cero o Feisty Fawn se actualiza a la nueva version 


:confused::confused:

Podes actualizar a Gutsy desde Feisty, han hecho mucho trabajo esta version para que sea lo mas seguro posible actualizar.

---

### Post by niko_3100 on 2007-09-11
Y si se actualiza asi se pierden las configuracion de los usuarios? o la carpeta home/miUsuario?? La verdad que el feisty fawn me encanto tenai antes el 6.06 y la version 7.04 me parecio realmente muchisimo mejor.

---

### Post by marianom on 2007-09-11
> **niko_3100 said:**
> Y si se actualiza asi se pierden las configuracion de los usuarios? o la carpeta home/miUsuario?? La verdad que el feisty fawn me encanto tenai antes el 6.06 y la version 7.04 me parecio realmente muchisimo mejor.

Yo ya hice algunos upgrades con el home sin particionar y en mi experiencia fue un proceso bueno, no perdí nada de info (igual me preparé un buen backup just in case).

---

### Post by DuckMan on 2007-09-11
se conservan todas las configs.. no pasa naranja

---

### Post by Apipote on 2007-09-11
Y en xubuntu sera igual de piola y seguro?

---

### Post by DuckMan on 2007-09-11
> **spg76 said:**
> Está en el menú "Sistema > Administración > Screen and Graphics Preferences".
Esta opción la agregaron en "Tribe 5" hacia que si tenés alguna versión anterior, no la vas a ver.

lo tengo en castellano, pero ensima no tengo nada de pantalla en ese lugar :( q pasara?

---

### Post by clasificado on 2007-09-14
> **Apipote said:**
> Y en xubuntu sera igual de piola y seguro?

en mi experiencia:
Al ubuntu es al que mas pelota le dan
Al Kubuntu, un poquito menos
y al Xubuntu, un poco menos que al kubuntu.

Siempre hubo un poco de Ripio cuanto màs abajo.

pero nada grave, che

clasificado

---

### Post by vk-cdg on 2007-09-14
Anoche estuve probando el 7.10 desde el CD Live con algún que otro inconveniente de reporte de fallos. Creo que se debe a que lo estaba corriendo del CD.
En primer lugar, no me instalaba los drivers privativos, daba un error de que no encontraba el paquete. Inicie de nuevo y no volvió a pasar.
En segundo lugar, no pude instalar el Compiz-Fusion, no se por que (en el 7.04 puedo instalar Beryl y usarlo a full aun usando el Live CD).
No me detecta el segundo monitor, aunque creo que es porque luego de instalar los drivers de video solo reinicio las X y no toda la máquina.
Como errores de menor importancia, en diferentes pantallas da un error de que se ha colgado y me ofrece reportar el error cosa que hago al instante para que tengan mas data.

Vere de instalarlo pero para eso quiero conseguir otro disco para no tocar el disco de producción.

---

