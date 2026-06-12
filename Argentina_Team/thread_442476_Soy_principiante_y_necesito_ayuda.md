---
title: "Soy principiante y necesito ayuda"
date: 2007-05-13
forum: Argentina Team
---

### Post by albertof67 on 2007-05-13
Hola Gente,... soy Alberto me gustaria poder disfrutar de Ubunto pero tengo un inconveniente.. tengo una pIII 750 mhz con 128 mb ram  2 discos (1 de 5 Gb y otro de 30 Gb) baje el iso de ubunto de la web. lo copie al cd  y cuando arranco mi pc.. apararece tpdo un cheque que dice ok en cada uno luego me aparece la pantalla de instalacion , cambio el idioma a Español y cuando le doy el ok para instalar aparece luego una pantalla marron con el puntero del mouse y ahi se queda.. por tiempo indeterminado.. ( ya es la 2da ves que intento instalarlo la 1ra ves con la version 6.10 y me hacia lo mismo .)

Anteriormente intente intalar otras distros.. pero me fueron muy dificiles ya que me preguntaban muchas cosas , lei en la web que Ubunto era especial para principiantes..espero poder recibir respuesta a mis consultas desde ya muchas gracias..


Alberto (Lanus, Bs As, Argentina)

---

### Post by lugonesjoaquin on 2007-05-13
Hola:

La cosa es que Ubuntu necesita como minimo para andar el Live-cd 256 MB de ram, tene en cuenta de que tiene que cargar todo ahi. Creo que es por eso, ya que en velocidad del procesador yo lo instale en procesadores de menos incluso.

Lo que podes hacer es conseguirte el cd de Xubuntu, un derivado de Ubuntu pero que utiliza otro entono grafico (XFCE) más rapido, o, conseguirte el alternate cd de Ubuntu que no instala a modo Live sino que arranca la instalacion a modo texto.

**ubuntu Alternate:**
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)

Otra cosa que puedes tratar que no se si andará es con el partition magic desde Windows (O algun otro particionador) creas una particion de 512 MB o màs con el formato Linux Swap y volve a probar de poner el cd y arrancarlo.

---

### Post by lavaramano on 2007-05-13
ultimamente, entre gnome y xfce hay tan poca diferencia que no la recomendaria como un DE mas liviano..

pero si, la "solucion" al problema es algun cd instaldor "alternate", el cual tambien te va a hacer preguntas, pero no son tan complicadas..
de ultima, anda ejecutando el instalador de a poco y te anotas las dudas que tengas, despues volves y preguntas :mrgreen:

si, es toda un trabajo hacer eso, pero una vez que sepas a que se refiere cada pregunta, vas a darte cuenta que no era tan dificil 

saludous

---

### Post by albertof67 on 2007-05-13
Muchas gracias por sus prontas respuestas.. estoy bajando el ultimate.. a ver que pasa.. despues les cuento.. 

un abrazo

---

### Post by kno712 on 2007-05-13
> **lugonesjoaquin said:**
> 
Otra cosa que puedes tratar que no se si andará es con el partition magic desde Windows (O algun otro particionador) creas una particion de 512 MB o màs con el formato Linux Swap y volve a probar de poner el cd y arrancarlo.

Ya que estamos en linux, digo yo que mejor utilizar una herramienta GNU, como por ejemplo GParted. Muy facil de utilizar y nada que envidar a Partition Magic.

---

### Post by lugonesjoaquin on 2007-05-13
> **kno712 said:**
> Ya que estamos en linux, digo yo que mejor utilizar una herramienta GNU, como por ejemplo GParted. Muy facil de utilizar y nada que envidar a Partition Magic.
Si pero esta no tiene version para Windows.

Si bien tiene un LIve CD es un desperdicio de CD, bue, aunque no sé, queda a eleccion del usuario, por ahi ya tiene el Partition Magic instalado, no sé.

[**Descargar CD Live cd Partition Magic**]("http://ufpr.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-6.iso")

---

### Post by Al_maverick on 2007-05-13
Yo tuve una situacion similar con una PII de 740MHz y 128MB de RAM.
El Live CD de Xubuntu andaba, pero no funciona para instalar con menos de 256MB. Para instalarlo me tuve que bajar el alternate CD.
Anda bastante bien, ahora estoy usandolo y no es una luz, pero se maneja. Y me permitio sacarle el Win98 a la PC que me ponia loco cada vez q lo usaba :D

Ah, el Xubuntu que instale es el Edgy, 6.10. Por los comentarios que lei no valía la pena usar la versión 7.4

---

### Post by kalel on 2007-05-14
yo usaria el alternate install pero instalaria un manejador de ventanas, [fluxbox]("http://fluxbox.sourceforge.net/") o [e17]("http://www.enlightenment.org/")

pk la verdade tenes muy poca ram como para correr siquiera un xfce dignamente.

[acá]("http://xwinman.org/") te dejo un site con info de manejadores de ventanas

---

### Post by albertof67 on 2007-05-14
Hola Gente!!! me alegro mucho por tantas respuestas.. les cuento cn generar un swap con el partition magic ( ya que lo tenia en windows) funciono la instalacion del 7.04 Maravilloso.. 
Ahora estoy investigandolo.. por lo pronto estoy buscando el driver del modem ADSL Zyxel que me instalo telefonica.. para poder tener internet desde Ubuntu..

Muchas Gracias a TODOS!!!!!!!


Alberto (posible futuro nuevo usuario de UBUNTO.....

---

### Post by jayflower on 2007-05-14
El modem Zyxel 630C ? USB? O con posibilidad de conectarlo al Ethernet?

---

### Post by Gideon26 on 2007-05-14
> **albertof67 said:**
> Hola Gente!!! me alegro mucho por tantas respuestas.. les cuento cn generar un swap con el partition magic ( ya que lo tenia en windows) funciono la instalacion del 7.04 Maravilloso.. 
Ahora estoy investigandolo.. por lo pronto estoy buscando el driver del modem ADSL Zyxel que me instalo telefonica.. para poder tener internet desde Ubuntu..

Muchas Gracias a TODOS!!!!!!!


Alberto (posible futuro nuevo usuario de UBUNTO.....
Hola alberto para poder configurar el zyxel P630 C-1 que es el que te da telefonica de argentina (speedy) en la pagina de ULUGA tenes un How To (como hacer) anda y segui ese instructivo que te va a andar es el mismo que use yo. 

[http://ubuntu-ar.com.ar/node/38](http://ubuntu-ar.com.ar/node/38)

saludos.

---

### Post by albertof67 on 2007-05-15
Gracias por el dato del modem lo habia encontrado en lugem.. tengo el modem USB (preguntaban por ahi) el instructivo esta fantastico el tema es que cuando quiero instalarel paquete
sudo dpkg -i br2684ctl_20040226_1_i386.deb 

me da un error.. como que no encuentra la libatm1 ... que necesita estar instalada previamente.. hasta ahi llegue estoy investigando...


un Abrazo..

Sigo Aprendiendo... Alberto

---

### Post by marianom on 2007-05-15
Hace 

```
sudo apt-get install libatm1
```

en una terminal para que te la instale así podes seguir con el proceso.

---

### Post by lavaramano on 2007-05-16
o "sudo aptitude install -f"

---

### Post by albertof67 on 2007-05-17
Hola Gente nuevamente .. haciendo consultas... gracias por el dato de como instalar el libatm1 pero mi problema es de donde lo saco?? lo busque por todo el ubuntu y no lo encuentro ..alguien sabe???

Muchas Gracias

---

### Post by jayflower on 2007-05-17
Si tenés internet ese comando baja el paquete de unos servidores donde están los repositorios y lo instala, pero por lo que comentas no tenés porque estás sin modem en Ubuntu, lo podés bajar de [aca]("http://packages.ubuntu.com/feisty/libs/libatm1"). Si no estás en Feisty en esta pagina de [Ubuntu]("http://packages.ubuntu.com/") podés buscar paquetes. Supongo que te conectas desde otro Sistema Operativo, los pones en Ubuntu y asi... No sé la dependencia de paquetes, si te pide otros hacés los mismo, los bajas de ahí y seguis compilando el driver del modem zyxel de porquería.
saludos

---

### Post by albertof67 on 2007-05-17
Hola Gente.. encontre lo que buscaba lo instale y tambien el driver del modem pero no puedo conectarme .. tengo que revisar a ver si algo hice mal.. pero esta todo instalado supongo que me falta alguna pavada..

Muchas Gracias por la ayuda..!!!!

Alberto

---

### Post by albertof67 on 2007-05-18
Bueno Gente solo queria comentarles que estoy navegando.. con el Firefox de Ubunto atraves de sppedy...!!!!!


Gracias a TODOS!!!

Alberto

---

