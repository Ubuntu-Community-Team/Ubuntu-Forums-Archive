---
title: "Problema con la webcam"
date: 2007-05-06
forum: Argentina Team
---

### Post by konstantin88 on 2007-05-06
Hola!! 
Todo anda de maravilla en Edgy salvo cuando intenté conectar una cámara digital que viene con una opción para utilizarla como webcam. 
Cuando la conecto estando en cualquier opción menos en Webcam, me reconoce el dispositivo externo y me permite bajar las fotos, pero cuando paso a la opción Webcam:

1) me aparece un cartel que dice
> Extracción insegura de dispositivos
Para evitar graves pérdidas de datos, desactive las unidades extraíbles con la opción "Extraer" del menú contextual del icono de la unidad que aparece situado en el escritorio, el lugar "Equipo" o la miniaplicación de unidades.
Tiene que ver con la webcam o con otra cosa?

2) cuando intento entrar al Visor de cámara web Camorama o activar la webcam en una conversación, se tilda el sistema.
Saben por qué puede pasar?

Gracias

---

### Post by clasificado on 2007-05-06
Me parece que es solo un cartel de advertencia, de que no le gustó nada la camara

Me surgen dos opiniones:
1) Que te asegures de pasarla a modo webcam ANTES de enchufarla a la pc, para que no se confunda.
2) Que revises la documentacion (o en alguna parte) que ese modelo use protocolos estandar de emision de video, o de cual protocolo está usando, para que te instales los drivers correspondientes en tu sistema.

Te explico un poco mas el punto dos: Yo tengo una cybershot dsc-p72 que viene con la misma promesa de webcam, pero incluso en Windows, solamente funcionaba con NetMeeting (lo decia el manual), y que me vaya olvidando de messenger. Segun lo veo yo, un sistema muy limitado y una promesa de marketing nomás.

clasificado

---

### Post by Tinchio on 2007-05-06
Seguramente tu webcam no esta soportada, a mi me pasaba con una Concord 3045 y un dia, kernel nuevo y si la tomaba.  fijate en [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) si esta soportada tu camara

---

### Post by konstantin88 on 2007-05-06
Clasificado
Si la pongo directamente en la opción webcam no sale el cartel pero se sigue tildando. Si Tinchio no me da solución intento con el 2)

Tinchio
Yo tengo la misma cam que la tuya, la Concord 3045; te funcionaba en Edgy? qué hiciste para que ande?

Gracias

---

### Post by Tinchio on 2007-05-07
Estoy casi seguro que de un dia para el otro, cuando se actualizo el kernel, ya me la reconocia, sino de ultima instalale el dirver SPCA5xx desde aca [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by Al_maverick on 2007-05-08
No se si lo probaste, pero a mi me pasaba lo mismo con Breezy y se solucionó reiniciando la maquina con la camara conectada al usb. A partir de ahi me la reconoció bien. 

Si no me equivoco, hasta esa version el driver tuvo problemas por una mala compilacion del kernel, pero no escuche de mas inconvenientes ni en edgy ni en feisty.

Este es un howto para instalar ese driver, pero no sé si está actualizado ni si aplica justo a tu chipset.

[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by konstantin88 on 2007-05-08
Reinicié con la cam conectada y sigue igual.

Cuando intenté hacer lo que me dijeron, me pasa ésto con el segundo paso:
> konstantin@konstantin-desktop:~$ tar xvfz spca5xx-20060501.tar.gz
tar: spca5xx-20060501.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores

Bajé gspcav1-20070426.tar.gz de la página [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html), eso es lo que busca? qué hago con él?

Gracias

---

### Post by jpmorelli on 2007-05-08
Yo bajé ese driver para poder hacer funcionar bien los colores en mi Genius webcam trek , pero nada, se sigue viendo como si estuviera en la peor resolución y con 4 colores... pero tal vez para tu cámara funcione.

Bajás el archivo, lo descomprimís, corres el comando "make" y cuando terminó de trabajar, corrés el comando "sudo make install", si todo funcionó sin darte mensajes de error, supuestamente al reiniciar ( es lo más fácil ) debería funcionar.
Suerte !

---

### Post by konstantin88 on 2007-05-08
Jmorelli
Explicame en criollo, más claro, no manejo bien la terminal todavía...

Gracias

---

### Post by Al_maverick on 2007-05-09
En las instrucciones, tenes que reemplazar spca5xx-20060501.tar.gz por gspcav1-20070426.tar.gz, que es el nombre actualizado del driver, por eso te da error, que no encuentra el archivo

o sea: 
```

tar xvfz gspcav1-20070426.tar.gz
```

y asi en el resto de las instrucciones.

---

### Post by konstantin88 on 2007-05-11
Es una cosa muy básica pero no la sé así que pregunto: cuando pongo
> tar xvfz gspcav1-20070508.tar.gz
dónde lo busca? porque me dice que no existe el fichero y sí existe, entonces probablemente no esté donde debe estar; cuando lo bajé quedó en tmp y no lo encuentra por lo que veo, qué hago?

Gracias

---

### Post by Al_maverick on 2007-05-11
debería estar en la carpeta donde la bajate
pone:
```
ls
```

y verifica el nombre.
una opción siempre útil de bash es poner ```
tar xvfz
```
y las primeras letras del nombre del archivo, despues apreta TAB y debería completar el nombre sólo (si no hay repetidos)

---

### Post by konstantin88 on 2007-05-11
Estando en la carpeta tmp, no lo encuentra, no aparece cuando pongo ls...lo pasé a la carpeta personal mía y ahí si lo encontró. Esto es lo que hice y lo que me pasó:
> konstantin@konstantin-desktop:~$ tar xvfz gspcav1-20070508.tar.gz 
gspcav1-20070508/
gspcav1-20070508/decoder/
gspcav1-20070508/decoder/gspcadecoder.c
gspcav1-20070508/decoder/gspcadecoder.h
gspcav1-20070508/decoder/gspcadecoder-OSX.c
gspcav1-20070508/decoder/gspcadecoder-OSX.h
gspcav1-20070508/Makefile
gspcav1-20070508/Vimicro/
gspcav1-20070508/Vimicro/vc032x_sensor.h
gspcav1-20070508/Vimicro/zc3xx.h
gspcav1-20070508/Vimicro/cs2102.h
gspcav1-20070508/Vimicro/vc032x.h
gspcav1-20070508/Vimicro/pas106b.h
gspcav1-20070508/Vimicro/icm105a.h
gspcav1-20070508/Vimicro/hv7131b.h
gspcav1-20070508/Vimicro/hv7131c.h
gspcav1-20070508/Vimicro/pb0330.h
gspcav1-20070508/Vimicro/ov7630c.h
gspcav1-20070508/Vimicro/tas5130c_vf0250.h
gspcav1-20070508/Vimicro/tas5130c.h
gspcav1-20070508/Vimicro/hdcs2020.h
gspcav1-20070508/Etoms/
gspcav1-20070508/Etoms/et61xx51.h
gspcav1-20070508/Sonix/
gspcav1-20070508/Sonix/sn9cxxx.h
gspcav1-20070508/Sonix/sonix.h
gspcav1-20070508/utils/
gspcav1-20070508/utils/spcagamma.h
gspcav1-20070508/utils/spcausb.h
gspcav1-20070508/utils/spcaCompat.h
gspcav1-20070508/Conexant/
gspcav1-20070508/Conexant/cx11646.h
gspcav1-20070508/Conexant/cxlib.h
gspcav1-20070508/Pixart/
gspcav1-20070508/Pixart/pac207-OSX.h
gspcav1-20070508/Pixart/pac7311.h
gspcav1-20070508/Pixart/pac207.h
gspcav1-20070508/changelog
gspcav1-20070508/gspca_core.c
gspcav1-20070508/Transvision/
gspcav1-20070508/Transvision/tv8532.h
gspcav1-20070508/Makefile.kld
gspcav1-20070508/gspca.h
gspcav1-20070508/Sunplus/
gspcav1-20070508/Sunplus/spca501.dat
gspcav1-20070508/Sunplus/spca505.dat
gspcav1-20070508/Sunplus/spca508.dat
gspcav1-20070508/Sunplus/spca561-OSX.h
gspcav1-20070508/Sunplus/spca506.h
gspcav1-20070508/Sunplus/spca561.h
gspcav1-20070508/Sunplus/spca501_init.h
gspcav1-20070508/Sunplus/spca508_init-OSX.h
gspcav1-20070508/Sunplus/spca508_init.h
gspcav1-20070508/Sunplus/spca501_init-OSX.h
gspcav1-20070508/Sunplus/spca505_init.h
gspcav1-20070508/Sunplus-jpeg/
gspcav1-20070508/Sunplus-jpeg/spca500.dat
gspcav1-20070508/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20070508/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20070508/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20070508/Sunplus-jpeg/spca500_init.h
gspcav1-20070508/gspca_build
gspcav1-20070508/Mars-Semi/
gspcav1-20070508/Mars-Semi/mr97311.h
konstantin@konstantin-desktop:~$ cd gspcav1-20070508
konstantin@konstantin-desktop:~/gspcav1-20070508$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/konstantin/gspcav1-20070508 CC=cc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.17-11-386'
  CC [M]  /home/konstantin/gspcav1-20070508/gspca_core.o
  CC [M]  /home/konstantin/gspcav1-20070508/decoder/gspcadecoder.o
  LD [M]  /home/konstantin/gspcav1-20070508/gspca.o
  Building modules, stage 2.
  MODPOST
  CC      /home/konstantin/gspcav1-20070508/gspca.mod.o
  LD [M]  /home/konstantin/gspcav1-20070508/gspca.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.17-11-386'
konstantin@konstantin-desktop:~/gspcav1-20070508$ sudo modprobe -r gspcav1
Password:
FATAL: Module gspcav1 not found.
Hice algo mal?

Gracias

---

### Post by Al_maverick on 2007-05-11
no, esta bien que te de el error si no lo tenias cargado.

esta ultima instruccion lo unico que hace es asegurarse que no lo tuvieras ya cargado.

```
konstantin@konstantin-desktop:~/gspcav1-20070508$ sudo modprobe -r gspcav1
Password:
FATAL: Module gspcav1 not found.
```

Podes seguir con el instructivo, no hay ningun problema

---

### Post by konstantin88 on 2007-05-11
Ya funcionaaa!
Estuve mirando en man modprobe (gracias a Al_Maverick que me explicó para que servía el command man, jeje), hojeando como usarlo y como lo que me decía que haga el howto iba a eliminar cosas no estaban, dejé esos dos pasos y directamente puse sudo make install y anda joya ahora, se ve re bien!

Graciaaas Al_Maverick, Jmorelli, Tinchio y clasificado
Repito lo que dije en la otra consulta, excelente la onda del foro, felicitaciones!

---

### Post by konstantin88 on 2007-05-11
Me ganaste Al_Maverick, me las arreglé solo, viste?

Gracias

---

### Post by Al_maverick on 2007-05-11
Muy bien! En cualquier momento ya estas del otro lado del mostrador ;)

---

### Post by clasificado on 2007-05-11
¡Buena esa!
Aunque mas no sea mirando, todos aprendemos con tu logro

Clasificado

---

### Post by jpmorelli on 2007-05-12
> **konstantin88 said:**
> Ya funcionaaa!
Estuve mirando en man modprobe (gracias a Al_Maverick que me explicó para que servía el command man, jeje), hojeando como usarlo y como lo que me decía que haga el howto iba a eliminar cosas no estaban, dejé esos dos pasos y directamente puse sudo make install y anda joya ahora, se ve re bien!

Graciaaas Al_Maverick, Jmorelli, Tinchio y clasificado
Repito lo que dije en la otra consulta, excelente la onda del foro, felicitaciones!

Me alegro mucho !! Legué tarde para la aclaración de mi post, veo que no solo te las arreglaste solo sino que ademas te fue muy bien. :lolflag: 
Estos logros son los que hicieron que Linux me guste cada día mas !!!

---

### Post by xarroyo on 2007-09-04
[http://ubuntuforums.org/showthread.php?t=530727](http://ubuntuforums.org/showthread.php?t=530727) aqui tengo mi post!! Resulta que segui las instrucciones de este sitio 

[http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/#comment-314](http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/#comment-314)

la primera vez que lo instale funciono perfectamente pero dias despues dejo de funcionar... no entiendo porq!! pero si van al link que coloque veran todas los mensajes que he capturado del modelo de la camara, informacion.. 

Gracias por su atencion,

Xavier

---

