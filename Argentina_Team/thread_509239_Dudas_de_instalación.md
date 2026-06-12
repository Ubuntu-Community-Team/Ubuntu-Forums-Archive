---
title: "Dudas de instalación"
date: 2007-07-25
forum: Argentina Team
---

### Post by Ch4rly on 2007-07-25
Hola amigos, soy novato y estoy tratando de instalar Ubuntu 7.4 y me encontré con varias dudas al final de cada instalación (ya tengo varias :lolflag: )

Mi laptop vino con Vista (oem), en la ultima instalación me aparecieron varias cosas que no logro entender y les agradezco una explicación lo mas sencilla posible.

Al finalizar la recuperación de Vista, me quedo lo siguiente: (HD 140 Gb)
Una partición de recuperación 1.5Gb
Una partición donde se aloja el vista 40Gb
y el resto (habilitada desde el adm de disco del vista) para instalar Ubuntu.

Bien, una vez instalado el Ubuntu, en el escritorio me aparecen la partición de recuperación y la que está el vista y no me deja desmontarla, a que se debe? (aclaro que todavía no use la consola de comandos, no llegué hasta ahí), en la instalación cree las siguientes particiones: donde se aloja el ubuntu / , otra que llamé /home , otra swap y por ultimo una fat32 para compartir con vista.

Y la otra duda es la siguiente, inicio al rato Vista y cuando voy a ver que ocurre con las particiones, me aparece solamente la partición del Vista y otra partición vacía :confused: o sea no veo ninguna de las
otras particiones creadas en Ubuntu (segunda pregunta, a que se debe eso?) y mi ultima pregunta es, que pasa si entro a guardar archivos ahí? no afecta en nada al Ubuntu? la verdad estoy muy confundido.

Desde ya muchas gracias por la ayuda que me puedan dar, ya que es un quebradero de cabeza y no quiero desistir tan rápido!

---

### Post by Mauro22 on 2007-07-25
Bueno, a ver:

* Las particiones las hicistes bien.
Tenes /
Tenes /home
Tenes Swap
Tenes Fat32
Tenes Vista
Tenes Recuperacion vista.


Bueno, el Windows por si solo nunca va a ver las particiones que no sean fat16, fat32 o ntfs. Entonces te aparece la del Vista (c:), y la fat32 (d:). La particion para recuperar el vista, es virtual, aparece oculta, y no lleva letra (por todos los casos que he visto hasta ahora)

Y en el ubuntu, te aparecen:
En el menu "lugares", se montan las ntfs, fat, que apuntan a /media


Ahora bien, las particiones fat32 se pueden usar en los dos sistemas sin problemas, ya que el ubuntu las emula con vfat. Pero para las particiones ntfs, necesitas un controlador aparte (sin esto, solo puedes leer particiones ntfs)


Si quieres sacar los iconos de los discos del escritorio solo haz:

* Alt + f2 
* Pones gconf-editor y enter

ahi te metes en /apps/nautilus/desktop
y de la derecha desactivas el que dice volumes_visible

y listo!


Salu2

---

### Post by Ch4rly on 2007-07-26
Hola gracias por la ayuda, muy claro todo!

Una cosa no me quedó en claro, si yo guardo archivos para compartir en Ubuntu en la partición correspondiente que tiene por ejemplo 10Gb, cuando me paso a Vista solo veo dos particiones (está entendido eso de los formatos), la de Vista y la otra que deje libre donde supuestamente está el Ubuntu pero no veo nada, donde fueron a parar esos archivos?

Y a la inversa si yo guardo por ejemplo mp3 o fotos desde Vista en la segunda partición, donde van a parar cuando trabaje con Ubuntu? 

Espero que no suene medio raro lo que pregunte y se entienda, es para tratar de entender un poco como funciona esto.
Gracias!

---

### Post by Mauro22 on 2007-07-26
Es facil, la particion "vacia" que te aparece en el Vista, es compatible con ambos sistemas. Lo que pongas ahi se puede leer en los dos SO.  Ahora bien, la particion del ubuntu (en donde se instalo el sistema) no la vas a poder ver desde el vista. debe haber algun tipo de plugin para vista, para reconocer particiones, ext2, ext3.


En ubuntu fijate, en la carpeta media ( /media) ahi vas a tener todos los discos, hda1, hda2, etc etc.

Salu2

---

### Post by Ch4rly on 2007-07-26
> **Mauro22 said:**
> Es facil, la particion "vacia" que te aparece en el Vista, es compatible con ambos sistemas. Lo que pongas ahi se puede leer en los dos SO.  Ahora bien, la particion del ubuntu (en donde se instalo el sistema) no la vas a poder ver desde el vista. debe haber algun tipo de plugin para vista, para reconocer particiones, ext2, ext3.


En ubuntu fijate, en la carpeta media ( /media) ahi vas a tener todos los discos, hda1, hda2, etc etc.

Salu2

Totalmente claro muchas gracias!!

---

