---
title: "Dudas antes de instalar Ubuntu Gutsy"
date: 2008-03-06
forum: Argentina Team
---

### Post by Forb.- on 2008-03-06
Buenas, estoy dispuesto a instalar Ubuntu Gutsy en mi PC, en realidad va a ser compartida con Win XP, en un mismo disco duro, y quisiera algunos consejos y si me a tener en cuenta y si me pueden contestar estas dudas:

1. Mi intención es iniciar la PC en Ubuntu con un diskette, y que el inicio directo sea en WinXP (no soy el unico que utiliza la PC), leí por ahí que puedo hacer un diskette de "booteo" con el comando:

grub-install /dev/fd0

Es esto correcto?, porque donde lo leí lo sugerian en caso de no poder iniciar la PC.

2. En caso de que por algún problema deba desinstalar Ubuntu (que espero y quiero que no suceda) cómo debo hacerlo? Algunos sugieren eliminar la partición de Ubuntu con, por ej, Partition Magic, pero la partición para Ubuntu la haré desde la instalación, es exactamente lo mismo? Después de hacerlo, debo ejecutar desde el cd de XP fdisk /mbr o fixmbr?

3. Tengo un modem Huawei SmartAX MT882 de Arnet, como voy a formatear la PC e instalar ambos SO voy a tener que reinstalar el modem por lo que habilitar mi conexión a internet la haré desde Windows, ahora Ubuntu me dará "problemas" con el modem, tengo que "activar" la conexión desde el mismo también?

4. El espacio para Ubuntu serían unos 40gb o 30 gb de un disco de 150 gb, es más que suficiente no?

5. Tengo una unidad externa de disco duro usb, debo instalar algo en Ubuntu para que la detecte o es como Win automatico?

6. Hay alguna forma de pasar archivos o carpetas desde XP a Ubuntu o viceversa?

Espero no causarles problemas, sepan entender que quiero introducirme en esto de Linux, por lo que soy bastante nuevito. Además piensen que es mejor que les pregunte estas dudas antes de tener problemas que cuando los tenga, je

Saludos.-

---

### Post by facundocorradini on 2008-03-06
Hola Forb, y bienvenido a Ubuntu-ar. 


> 1. Mi intención es iniciar la PC en Ubuntu con un diskette, y que el inicio directo sea en WinXP (no soy el unico que utiliza la PC), leí por ahí que puedo hacer un diskette de "booteo" con el comando:


Sí, es correcto. Pero mi consejo es que lo instales normalmete, y configures grub para iniciar XP por default, 
Poner un diskette es algo bastante molesto...
> 
2. En caso de que por algún problema deba desinstalar Ubuntu (que espero y quiero que no suceda) cómo debo hacerlo? Algunos sugieren eliminar la partición de Ubuntu con, por ej, Partition Magic, pero la partición para Ubuntu la haré desde la instalación, es exactamente lo mismo? Después de hacerlo, debo ejecutar desde el cd de XP fdisk /mbr o fixmbr?

Es lo mismo, podés borrar directamente las particiones y luego volver a darle espacio al windows desde partition magic.

> 3. Tengo un modem Huawei SmartAX MT882 de Arnet, como voy a formatear la PC e instalar ambos SO voy a tener que reinstalar el modem por lo que habilitar mi conexión a internet la haré desde Windows, ahora Ubuntu me dará "problemas" con el modem, tengo que "activar" la conexión desde el mismo también?

Hasta donde sé no va a haber ningún problema. La activación no creo que debas hacerla siquiera, solo configurarla en ubuntu.
(llegado el momento pedí ayuda en el foro)

> 4. El espacio para Ubuntu serían unos 40gb o 30 gb de un disco de 150 gb, es más que suficiente no?

Seguramente. De hecho 10gb son más que suficientes. Te recomiendo igual que uses esos 40, como para poder instalar juegos -que los hay y muy buenos-
> 
5. Tengo una unidad externa de disco duro usb, debo instalar algo en Ubuntu para que la detecte o es como Win automatico?

En teoría debería funcionar automáticamente, sin necesidad de instalar drivers siquiera.
> 
6. Hay alguna forma de pasar archivos o carpetas desde XP a Ubuntu o viceversa?

Sí. Desde Ubuntu vas a poder ver y escribir en la partición de windows sin problema.

saludos!

---

### Post by tony_feisty on 2008-03-06
Antetodo felicidades por la decisión de comenzar en Linux....

Primero creo que no es necesario que el inicio lo hagas con un diskette, ya que podes modificar el menu del grub para que a un determinado tiempo (ej: 5 seg) levante en XP en forma automatica, para mi gusto te vas ahorrar muchos dolores de cabeza con los dikettes. Para eliminar la partición si queres lo haces desde el mismo CD de instalación del XP, no es problema el tema de la partición... si queres una limpieza óptima de la partición lo podes hacer con el Partition Magic que es muy bueno. Para la conexión de ADSL lo haces desde ubuntu, es muy sencilla la configuración no creo que tengas problemas, hay compatilidad con la mayoria de los ethernet. El espacio es mas que suficiente, lo que si fijate que cuando instales dejale para la parte de swap que te indica en el momento de seleccionar la partición en ubuntu. Con el tema de unidades extraibles no vas a tener problemas ya que te las reconoce como en XP. En ubuntu podes leer particiones NTFS, si bien podes acceder es de solo lectura... si queres vas a poder pasar archivos que tengas en la partición de XP a ubuntu, pero no viceversa. Hay un programa que se instala del lado del XP que lee particiones Linux o también podes crear otra partición FAT32 que podes usar para compartir archivos entre ambos sistemas operativos. 

Espero haberte sacado algunas dudas, igual cualquier problema que tengas exponelo en el foro que te van a dar solución. 

Saludos

---

### Post by leo_rockway on 2008-03-07
> **Forb.- said:**
> 
4. El espacio para Ubuntu serían unos 40gb o 30 gb de un disco de 150 gb, es más que suficiente no?


Además de lo que ya te contestaron, fijate de separar / y home en dos particiones distintas. En caso de tener que reinstalar (que no debería pasar, pero siempre cabe la posibilidad), tener la home en otra partición te va a ahorrar problemas.

---

### Post by faktorqm on 2008-03-07
Hola y bienvenido a la comunidad.

> **Forb.- said:**
> Buenas, estoy dispuesto a instalar Ubuntu Gutsy en mi PC, en realidad va a ser compartida con Win XP, en un mismo disco duro, y quisiera algunos consejos y si me a tener en cuenta y si me pueden contestar estas dudas:

1. Mi intención es iniciar la PC en Ubuntu con un diskette, y que el inicio directo sea en WinXP (no soy el unico que utiliza la PC), leí por ahí que puedo hacer un diskette de "booteo" con el comando:

grub-install /dev/fd0

Es esto correcto?, porque donde lo leí lo sugerian en caso de no poder iniciar la PC.



Mira, para mi esta muy lejos de ser lo correcto por que como vos bien leiste eso se usa solo para emergencias y es un metodo poco practico, todos conocemos lo que dura un diskette.
Existe un programa que se llama grub que es el que inicia la compu, que te permite arrancar entre los sistemas operativos que tengas. Para no tener problemas, lo tenes que instalar en el MBR del disco, NO en la primera particion. (en la instalacion te dice igual).

> **Forb.- said:**
> 2. En caso de que por algún problema deba desinstalar Ubuntu (que espero y quiero que no suceda) cómo debo hacerlo? Algunos sugieren eliminar la partición de Ubuntu con, por ej, Partition Magic, pero la partición para Ubuntu la haré desde la instalación, es exactamente lo mismo? Después de hacerlo, debo ejecutar desde el cd de XP fdisk /mbr o fixmbr?

Es lo mismo escuchar un mp3 con media player, winamp o tu mp3 de bolsillo?
Es lo mismo administrar tu disco con CUALQUIER administrador de particiones. El de ubuntu se llama gparted, uno muy bueno para windows es partition magic, otro el Paragon Partition Manager, mas para discos de rescate y esas cosas es el Ranish Partition Manager.
Lo del fdisk /mbr es solo para windows linea 9X/ME. El NT/2k/xp es fixmbr. Aun asi, es solo cuando instalas el grub en el mbr y no en la primera particion, por eso te lo aconseje arriba.
Ejemplo, si vas a desintalar, limpias el /, el /home y el swap, estiras la particion y cuando arranques o bien el grub solo te va a iniciar windows, o bien no va a funcionar. Ahi  metes el cd del xp, consola de recuperacion y fixmbr y reinicias y todo bien.

> **Forb.- said:**
> 3. Tengo un modem Huawei SmartAX MT882 de Arnet, como voy a formatear la PC e instalar ambos SO voy a tener que reinstalar el modem por lo que habilitar mi conexión a internet la haré desde Windows, ahora Ubuntu me dará "problemas" con el modem, tengo que "activar" la conexión desde el mismo también?


No te va a dar problemas, pero ahi te tendria que ayudar la gente que lo tiene, asi te dice exactamente que hacer para instalarlo sin pasarte por 500 tutoriales y que recien el ultimo te ande. Si es ethernet (NO USB) te digo como es, debe ser una papa.
Post relacionados: [http://ubuntuforums.org/showthread.php?t=688286&](http://ubuntuforums.org/showthread.php?t=688286&)
[http://ubuntuforums.org/showthread.php?t=511535](http://ubuntuforums.org/showthread.php?t=511535)
[http://www.adslzone.net/tutorial-46.2.html](http://www.adslzone.net/tutorial-46.2.html)
[http://guisheca.wordpress.com/?s=huawei+SmartAX+mt882](http://guisheca.wordpress.com/?s=huawei+SmartAX+mt882)

> **Forb.- said:**
> 4. El espacio para Ubuntu serían unos 40gb o 30 gb de un disco de 150 gb, es más que suficiente no?

Bueno, esto es un tema que tenes que tratar bien. La onda, es asi: Podes tener hasta 4 particiones por disco, si? entonces lo que te recomiendo es que hagas, una de 10gb, para el "/", que vendria a ser la particion de sistema, inmediatamente despues de la particion del windows (si tenes ocupado los 150gb achicala). Despues, una de 20gb  o 30gb que la tenes que montar en "/home", PERO al final del disco, tenes que dejar APROXIMADAMENTE el doble de tu memoria RAM para la particion de swap, que la montas como swap.
Te va a quedar algo parecido a esto (me baso en un disco de 150gb):

Windows, primera particion, 110gb, NTFS, montada en "/media/windows"
Linux, segunda particion, 10gb, EXT3, montada en "/"
Linux, tercera particion, 28gb, EXT3, montada en "/home"
Linux, cuarta particion, 2gb, SWAP, montada como swap.


> **Forb.- said:**
> 5. Tengo una unidad externa de disco duro usb, debo instalar algo en Ubuntu para que la detecte o es como Win automatico?

Mira, si es windows te la detecta SIN drivers, Ubuntu te la va a reconocer sin ningun problema. En algunas ocasiones, ocurre que Ubuntu te reconoce cosas sin dirvers que en windows necesitan drivers, y en otras ocurre que de cosas que en windows no llevan drivers, ubuntu no las toma. 
Como probas esto? facil! pones el cd live de ubuntu, cuando arranco, enchufas el disco. Y ahi tenes la prueba fehaciente de si anda o no ;)

> **Forb.- said:**
> 6. Hay alguna forma de pasar archivos o carpetas desde XP a Ubuntu o viceversa?

Si, desde ubuntu, existe un programa que se llama NTFS-3G, que lo instalas y listo. Se porta CON LA MISMA VELOCIDAD que si fuera un windows. 
Desde windows, existen drivers para manejar sistemas de archivos EXT3, PERO NO CON LA VELOCIDAD que lo maneja linux, es decir, si intentas copiar un archivo de 4gb, tarda 30 minutos o mas. El por que es muy largo de contestar, lo dejamos para otro post ;)

> **Forb.- said:**
> Espero no causarles problemas, sepan entender que quiero introducirme en esto de Linux, por lo que soy bastante nuevito. Además piensen que es mejor que les pregunte estas dudas antes de tener problemas que cuando los tenga, je
Saludos.-

Exacto, vos pregunta, que nosotros con la mejor onda intentamos responderte. Lo que si no abuses de nuestra bondad :D y si son cosas "de facil resolucion" digamos, promero busca en google, LUEGO EN NUESTRO FORO, luego aca: [http://ubuntu-ar.org/soporte/comos/](http://ubuntu-ar.org/soporte/comos/) y en los enlaces que te pasaron antes. Si seguis con problemas, o alguna de las guias que seguiste por algun motivo no te funcionan, pregunta tranquilo DETALLANDO bien el problema, asi te podemos ayudar mejor.
Espero que tu experiencia con ubuntu sea la misma que con todos nosotros: UNA MASA!!
Salu2 y suerte con eso!!

---

### Post by facundocorradini on 2008-03-07
faktorqm: Muy buena tu respuesta, pero te quedaste en el tiempo. 

Ubuntu hace rato trae integrado soporte directo para escritura sobre NTFS, no hace falta instalar nada para eso

---

### Post by Radiobuzz on 2008-03-07
Estoy de acuerdo con Facundo, de hecho mientras leía el primer post pensaba justamente que no es necesario usar un disquette para bootear. En mi caso, mi familia también usa la PC y usan Windows. Imagínense que una vez reemplacé Microsoft Office con Open Office y poco más me tiran a la hoguera porque "no sabían cómo usarlo" (por más que el manejo es exactamente igual). Además, también me gusta que ellos usen Win y yo Ubuntu porque ya no tengo por qué estar todo el tiempo haciendo mantenimiento en el otro SO. En fin, a lo que iba es que en mi caso, lo que hice fue modificar Grub para que tenga a WinXP como opción determinada y que sólo tarde 2 segundos entre que muestra las opciones y lo bootea, que para mí es es tiempo suficiente si quiero elegir Ubuntu y por otra parte a mi familia no le molesta (de hecho es probable que ni lleguen a leer las opciones). Digo todo esto porque, aunque nunca booteé de un disquette, creo que sería más seguro hacerlo desde Grub directamente.

Y por cierto, también doy fe del soporte para escritura sobre NTFS, de hecho en la partición de Windows tengo mis carpetas encriptadas y así y todo puede leerlas perfectamente.

---

### Post by pante on 2008-03-07
Varias de las cosas que necesitas saber las apliqué cuando instalé mi Xubuntu (ahora Ubuntu).

El módem Huawei mt810 es USB. Yo lo tengo y funciona perfectamente con Ubuntu. Instalarlo es un poco tedioso, pero no es difícil. En este foro hay por ahí un tutorial que explica todos los pasos. Hay un par de links en ** [http://ubuntuforums.org/showthread.php?t=626881](http://ubuntuforums.org/showthread.php?t=626881) **

Para que inicie por defecto Windows y no Ubuntu (también por la familia) hice lo siguiente, que encontré [**por ahí**](http://www.yoreparo.com/foros/linux/configurar-grub-para-que-arranque-windows-t102930.html):

> Bajo Ubuntu solo debés editar el archivo menu.lst en /boot/grub 
Código:$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
$ sudo gedit /boot/grub/menu.lst 

Buscá la línea: 
... 
default 0 
... 
Y cambiala por 2 o 3*****. 
Guardá los cambios y reiniciá. Después contanos. 

Si también querés darle más tiempo a grub para elegir con que bootear cambiá el parámetro que dice timeout y ponele 30.
*Hay que cambiarlo por 4, creo recordar; es el número en que aparece en el menú inicial: Ubuntu, Ubuntu recuperación, memtest, otros sistemas operativos (esta línea también cuenta) y Windows. Probá un número y reiniciá. Si está bien estará resaltado Windows; si está mal estará resaltada otra cosa y tendrías que entrar a Ubuntu y volver a modificarlo por un número más o menos.

Saludos:)

---

### Post by Forb.- on 2008-03-07
Muchisimas pero muchisimas gracias a todos! La verdad que me han iluminado mucho y me han hecho sentir más seguro a la hora de instalar Ubuntu.

Mañana a la tarde me dispondré a hacerlo, si todo sale bien a la noche estaré posteando mi primera impresión desde Gutsy :)

Saludos y nuevamente muchas gracias.

---

### Post by faktorqm on 2008-03-09
muchachos muchachos muchachos, por supuesto que ya sabia que trae integrado soporte ntfs, solo que el soporte ese NO es el paquete ntfs-3g (Aclaro que uso 7.04). Este paquete no viene instalado por defecto, si viene otro (en realidad es desde el kernel) que soporta escritura sobre ntfs. Yo ahi puse ntfs-3g por que la velocidad de escritura y algunas yerbas mas como podran apreciar en este enlace:

[http://es.wikipedia.org/wiki/NTFS-3G](http://es.wikipedia.org/wiki/NTFS-3G)

CITO: "NTFS-3G es un driver estable de NTFS para Linux, con licencia GNU GPL y de código abierto. Al contrario que el driver NTFS incluido en el kernel de Linux, tiene muy pocas limitaciones en cuanto a la escritura de archivos: permite crear, renombrar, mover o borrar ficheros de cualquier tamaño en particiones NTFS, con la excepción de ficheros comprimidos por NTFS o cifrados pero todavía no puede modificar ACLs ni permisos."

noticia de julio de 2006: [http://www.vivalinux.com.ar/soft/ntfs-3g.html](http://www.vivalinux.com.ar/soft/ntfs-3g.html)

pagina del proyecto: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

Antes de decirme que soy un anticuado, podrian informarse mejor, no les parece? Salu2!!

---

