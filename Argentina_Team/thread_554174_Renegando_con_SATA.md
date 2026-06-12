---
title: "Renegando con SATA"
date: 2007-09-18
forum: Argentina Team
---

### Post by LaHire on 2007-09-18
Saludos terrícolas!

Les comento que tengo una Pc nueva, y tengo un disco rigido SATA de 230 Gb y un AMD Athlon x2

Sin ir mas lejos, cuando le quise meter Ubuntu 7.04 de 64 Bits....

Anduvo perfecto...y en la parte de instalación......

No me detectaba el disco! 

Estoy desesperado! no se que hacer :P

Si bien creo que hay que instalar algunos drivers...no se cuales


Perdón mi ignorancia :/

(y bueno, por si acaso, estaba buscando en los foros...y la mayoría tiene problemas con el GRUB, este disco rígido esta completamente virgen, ni siquiera tener freeDOS)

agradecería cualquier dato que me puedan pasar
muchas gracias! y perdón la molestia :)

---

### Post by Mauro22 on 2007-09-18
hay que ver si el chipset controlador del SATA, te lo reconoce linux...

Que marca/modelo de mother es?


Probaste con la x86?

---

### Post by LaHire on 2007-09-19
> **Mauro22 said:**
> hay que ver si el chipset controlador del SATA, te lo reconoce linux...

Que marca/modelo de mother es?


Probaste con la x86?



Mañana me fijo de instalar la x86...
la placa no me acuerdo la marca (es la pc de un amigo), pero creo q es MSI

Casualmente, recuerdo que el disco SATA esta enchufado a la placa, pero en la BIOS no lo reconoce (reconoce la lectora que está en otro canal SATA)

Puede llegar a ser eso?, cambiando de lugar el disco?

---

### Post by facundocorradini on 2007-09-19
Si el mismisimo BIOS no lo reconoce, entonces es probable que se deba a algun problema de hardware...

Probá poner el rígido en el puerto donde está la lectora... si lo reconoce, mepa que vas a tener que cambiar el mother, pues parece que el otro puerto no anda...

---

### Post by faktorqm on 2007-09-19
hola, vos me parece que tenes el mismo problema que yo el otro dia en la pc de un cliente...... 
fijate cuando entras al bios, en la configuracion del sata, ponerle NON-RAID.
yo el otro dia necesitaba instalar un xp y no me detectaba el disco y empeze a transpirar (lo habia comprado nuevo hacia 20 minutos). agarre el manual de la mother, y decia que lo tenia que poner, en la opcion de hacer RAID, en modo NON-RAID. (si esta con algun numero, 0 ó 1 y tenes un solo disco, esta mal)
no contento con esto, el cd de xp seguia sin reconocerme, habia que poner el diskette feo generado desde otra pc con el cd de los drivers de la placa. asi que todo mal hasta que me lo reconocio.
la verdad no se como funciona este tema en linux, pero es malo (MUY malo) que linux no soporte sata a esta altura del partido............... (linux = grub = coso de la instalacion = XD)
de todas maneras, si el bios no te lo muestra, no quiere decir que no te lo reconozca, por que hay muchos mothers que la comprobacion de los sata la hace despues del bootstrap, y te salta un mensajito tipo "press ctrl + c for configure raid" o algo asi, te muestra los discos que tenes conectados, y sigue para bootear.
la pregunta es: la lectora es sata?!?!? por que en las mothers relativamente nuevas los IDE y los SATA se llaman todos sata. del 1 al 4 los ide (los llaman PATA ó parallel ATA) normales, del 4 a N los SATA (serial ATA).
perdona el choclo, espero que te haya servido de algo. salu2!

---

### Post by facundocorradini on 2007-09-19
> la verdad no se como funciona este tema en linux, pero es malo (MUY malo) que linux no soporte sata a esta altura del partido............... (linux = grub = coso de la instalacion = XD)

Disculpeme colega, pero está usted "razonando fuera del recipiente"...

---

### Post by faktorqm on 2007-09-19
> **facundocorradini said:**
> Disculpeme colega, pero está usted "razonando fuera del recipiente"...

capaz no me exprese bien, lo que quise decir es que tiene poca flexibilidad, en cuanto a que DEBE tener soporte para los nuevos chips manejadores de serial ata, y no tener que andar modificando el cd de instalacion y haciendo malabares simplemente para instalar!! una vez que esta instalado, es otro cantar, pero ni bien lo pones, tanto el particionador de discos como el iniciador de la instalacion y los probe's del hardware tienen que reconocer cuanto menos el 90% de los chips que manejan serial ata, tanto raid como non-raid. salu2!

---

### Post by mpbe on 2007-09-19
Hola a todos:
  Este fin de semana justamente actualice mi maquina y estuve renegan por que no podia instalar Ubuntu por que no me reconocia los discos SATA.

---

### Post by mpbe on 2007-09-19
Y descubri lo siguiente. Los discos SATA se pueden ultizar con 3 drivers distintos que se configuran de las bios. Estos son IDE, RAID y IICH. Por defecto los mother vienen configurados para IDE (compatibilidad con IDE). El driver SATA es el IICH desarrollado por IBM y es abierto por lo que linux tiene un exelente soporte. En resumen entra en la bios cambia el driver de SATA a IICH.
  Con esto lo solucione y funciona exelente.

Saludos

---

### Post by rojojuan on 2007-09-19
> **mpbe said:**
> Y descubri lo siguiente. Los discos SATA se pueden ultizar con 3 drivers distintos que se configuran de las bios. Estos son IDE, RAID y IICH. Por defecto los mother vienen configurados para IDE (compatibilidad con IDE). El driver SATA es el IICH desarrollado por IBM y es abierto por lo que linux tiene un exelente soporte. En resumen entra en la bios cambia el driver de SATA a IICH.
  Con esto lo solucione y funciona exelente.

Saludos

Se agradece el dato. Estoy por cobrar un Sata II.

---

### Post by LaHire on 2007-09-19
Bueno, al final lo que se hizo fue cambiarle el lugar donde estaba enchufado en la placa madre; porq había 3 SATA.

Ahora...anda, al menos, pero mi amigo instaló el ubuntu equivocado, el 6.06 :P

No creo que haya problemas al hacer dist-upgrade, no?, no va a explotar nada? :lolflag:

---

### Post by kowal on 2007-09-19
> **faktorqm said:**
> 
la verdad no se como funciona este tema en linux, pero es malo (MUY malo) que linux no soporte sata a esta altura del partido............... (linux = grub = coso de la instalacion = XD)


En mi caso (mother MSI neo2 Platinum) con los discos SATA no tuve nunca problemas de renocimiento en Linux. Sin embargo en Windows XP tuve que usar un diskette con los drivers (si, un diskette.. dispositivo que está en existinción).

---

### Post by facundocorradini on 2007-09-20
> **kowal said:**
> (si, un diskette.. dispositivo que está en existinción).

Y que si no fuera por los discos de inicio de win, ya se hubiera extinguido cuando salió el cd... y ni hablar de cuando salió el ZIP, y menos de cuando salió el pen drive, o las tarjetas de memoria... 

Aún no entiendo como alguien puede seguir usando este dispositivo tan inútil y estropeable... 
Y pensar q las PC siguen trayendo disketera!!

---

### Post by faktorqm on 2007-09-20
> **facundocorradini said:**
> Y pensar q las PC siguen trayendo disketera!!

eeehhhh..... en que mundo vivis men? (no te ofendas ni te lo tomes a mal, pero se nota que no armas compus....) los gabinetes "kit" no traen diskettera desde el año 2003 mas o menos. las compus originales, tipo las hp, ya traian para bootear desde usb en ese año y tampoco tenian diskettera, lo unico que se trae "soporte" para diskettera son las mothers, que por un acuestion de compatibilidad traen el puerto y el cable feo. 

off topic: nunca pensaron que si hubieran usado el mismo sistema de los diskettes para los cd no existirian los cd's rayados? solo serian un poco mas grandes, lo cual tb es un problema, pero no me parece mala idea jajajajajaj
salu2!!

---

### Post by facundocorradini on 2007-09-20
> eeehhhh..... en que mundo vivis men? (no te ofendas ni te lo tomes a mal, pero se nota que no armas compus....) los gabinetes "kit" no traen diskettera desde el año 2003 mas o menos.

vivo en Mar del Plata "men", y cualquier PC q vayas a comprar a cualquier casa de computación, te la presupuestan con disketera.
> 
off topic: nunca pensaron que si hubieran usado el mismo sistema de los diskettes para los cd no existirian los cd's rayados? solo serian un poco mas grandes, lo cual tb es un problema, pero no me parece mala idea jajajajajaj

De hecho, los CDs Regrabables usan un sistema muy similar (aunque mucho menos volátil), el problema viene por el lado de lo que se tarda en grabar y desgrabar. 

Ya está, las memorias flash han resulto ambos problemas: se graban enormes cantidades de información en espacios muy pequeños, y a una velocidad impresionante...

---

### Post by faktorqm on 2007-09-20
hace tanto que no compro una pc armada que ya ni me acuerdo como era..... decile al chabon de la casa de computacion que deje de robar a la gente tratando de sacarse de encima el stock de disketteras que le quedo colgado jajajajajaj salu2!

---

### Post by javier-2714 on 2007-09-24
Hola les comento con respecto a las disqueteras yo armo maquinas y en win xp la única forma de habilitar el sata raid es cargando el driver mediante disquet win xp no te da otra opción en Windows vista lo podes cargar mediante usb, compre una notebook hp pavilion 530 no trae disquetera no hay forma de meterle el driver para habilitar el sata raid  siempre ablando de win xp ,en cambio yo uso Ubuntu 7,04 y reconoce perfecto tengo tres discos sata no hay que agregarle driver no tuve ningún problema saludos.

---

### Post by Mataca on 2007-09-24
Yo también compré una pc nueva, pero el HD me lo reconoce perfectamente, con lo que tengo problemas es con la lectora SATA !! Y no me la reconoce, voy a probar cambiando el driver a ese de IBM y les cuento.

Pd Groso facundo, aguante les luthiers

---

