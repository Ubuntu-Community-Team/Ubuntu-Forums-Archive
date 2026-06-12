---
title: "como hago un backu"
date: 2007-10-11
forum: Argentina Team
---

### Post by dj_isaco on 2007-10-11
hola a todos esta es la 1º vez q hago un post aqui y hace 7 dias q instale ubuntu, despues de confi todo y de no entender para q servian las cosas,q por sierto me resulto algo frustant, y estuve a poco de formatear de vuelta todo y olvidarme de sto , bueno con algo de pasiencia y repetirme lo mismo me paso con win,habia q darle una oprotunidad no?.
bueno ya dejando mi tentimonio de mis primeros pasos, les pregunto si hay una manera rapida para realizar un backup ya q lei de una nueva version de ubuntu y q actualizandola ya qdabe listo, otra cosa de q hay q hacer el backup, y como ? desde la teminal o algun soft Gracias...

---

### Post by vk-cdg on 2007-10-11
Desde mi forma de ver las cosas, hay varias maneras de hacer un backup, que terminan siendo la misma operación.

Un backup es en definitiva, copiar aquellos archivos que no querés perder (trabajo, videos, fotos, escritos, etc) a otro lugar, en lo posible fuera de la PC con la que estás trabajando. 
Cuales son las maneras?

Copiar a mano (siempre y cuando te de el espacio) los archivos a un Pen Drive
Grabar un CD/DVD con esos archivos
Con algún soft de backup a alguna ubicación remota
Subirlos a algún sitio FTP
A otro equipo a través de una red
Etc.
Etc.
Etc.

En definitiva, se trata siempre de lo mismo, copiar los archivos que NO querés perder si pasa algo con una actualización, con un problema con el disco, etc.

---

### Post by dj_isaco on 2007-10-11
gracias vk por responder al toq, diculpa no me exprese bien a lo q apunto es cuando actualizo todas las confi qdan igual no?,y si por algun motivo algo no anda bien como puedo volver a como estab antes,como un punto de restauracion comparando con xp (q no es lo mismo) ya se pero para q qde claro

---

### Post by vk-cdg on 2007-10-11
El backup tiene como finalidad resguardar tus datos por si pasa algo

Cuando actualizás tengo entendido que mantiene la configuración, pero (si me equivoco que me corrijan) no hay forma de volver atrás. Si algo sale mal, formatear e instalas la nueva versión y listo.

---

### Post by dj_isaco on 2007-10-11
gracias, nos toca sperar a que salga la final no mas

---

### Post by Oktubre on 2007-10-11
Mira, cuando actualiza el Kernel (corazon del SO) al inicio te quedan dos opciones de booteo (arranque) y podes elegir con cual iniciar. 

Mi recomendacion es, si queres actualizar a 7.10, esperar a que salga la version estable.

Para hacer un backup, por lo general copiando todo lo que este en tu /home alcanza.

Saludos,

---

### Post by sharkg on 2007-10-11
> **Oktubre said:**
> Mira, cuando actualiza el Kernel (corazon del SO) al inicio te quedan dos opciones de booteo (arranque) y podes elegir con cual iniciar. 

hola, mira yo tengo por cada actualizacion, unas varias ya, sus inicios!!! asi q podes tener mas de dos!!!! si alguno sabe como sacar todos los inicios y dejar los ultimos 3 por ejemplo le agradesco me informe!!!! gracias y saludos

P.D: si querias decir q cuando actualizas se suman 2 opciones mas a las anteriores es verdad!!!un inicio comun y otro en modo seguro... ademas del memtest y de Win y otros q tengas en tu pc!!
espero entiendas!! saludos

---

### Post by luchardi on 2007-10-11
sharkg para modificar y sacar de la lista a los "viejos" kernels solo tenes que actualizar el file

/boot/grub/menu.lst

eso si, te recomiendo no borres nada, hagas una copia de seguridad previamente y cada vez que quieras sacar un kernel, le agregues # para comentar la entrada asi las podes volver a recuperar.


otro tema es la entrada default= asegurate que apunte a la nro. de entrada (comenzando con 0) q vos queres tener como default.

Cualquier cosa si no se entiende, te pongo un ejemplo.

Slds.

---

### Post by Oktubre on 2007-10-11
Si, yo tambien tengo una por cada actualizacion. Dije dos en referencia a que dj_isaco no tiene mas que una por ahora. 

Es cierto que te crea una por cada vez que actualizas ;)

Saludos

---

### Post by Hei Ku on 2007-10-11
cada vez que actualiza el kernel te crea una nueva opción.  O sea que son varias por version de Ubuntu. Yo debo tener unas diez en este momento. Lo ironico es que como tengo un teclado en USB y Ubuntu todavía no se decidió a agregar el driver, no puedo seleccionar ninguna tecla :D

Ah, cuando modificas el menu.lst, después tenes que correr sudo update-grub

---

### Post by kowal on 2007-10-11
Diferentes maneras de hacer backups:

- Copiar el **/home** (y otros archivos escenciales) a otra partición, CD, DVD, etc.
- Usar **partimage** para crear una imagen total de la partición
- Utilizar herramientas como **rsync** que sincronizan directorios/archivos buscando de forma "inteligente" los cambios, por lo que tardan muy poco en hacer backups. Yo prefiero **rdiff-backup**, que es similar a rsync, pero que además hace "snapshots" ordenados por fechas/momentos que pueden recuperarse. 

Seguramente existen otras posibilidades, esas son las que puedo aportar.

Saludos!

---

### Post by luchardi on 2007-10-11
Al menos en mi caso nunca corri apt-update grub .. o nada, modifico el archivo .lst que es el que lee el boot loader para decidir que particiones debe bootear.

---

### Post by Hei Ku on 2007-10-11
el comando es sudo update-grub

tengo entendido que si no lo corres, con la siguiente actualizacion de kernel perdes las modificaciones que habias hecho en el archivo, pero alguien me puede corregir en esto.

---

### Post by godzeus on 2007-10-12
Hay una distro que creo que se llama MondoResc, que es livecd, te permite crear backup de tus particiones, comprime las imagenes y despues si lo necesitas, podes reestablecer el sistema como si nada hubiera pasado, similar  al Ghost, pero mucho mejor. Obvio, es Open Source...
Saludos
:)

---

