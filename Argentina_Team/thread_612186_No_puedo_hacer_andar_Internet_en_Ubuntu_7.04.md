---
title: "No puedo hacer andar Internet en Ubuntu 7.04"
date: 2007-11-13
forum: Argentina Team
---

### Post by angelnochero on 2007-11-13
Hola nuevos amigos de linux, soy un novato en el tema y se me presento un problema, eh instalado Ubuntu 7.04, hace mas o menos 2 o 3 semanas mediante el programa Wubi, que simplemente instala Ubuntu desde linux ocupandose de las particiones y haciendo el "trabajo sucio" ya que yo manualmente no pude encontrar solucion para usar los dos sistemas, tuve que utilizar este programita.Esto es simplemente como dato pero no creo que tenga que ver con mi problema. 
El resultado fue optimo, Ubuntu anda a la perfeccion, pero el problema llego cuando quise instalar mi Modem Huawei MT810 de arnet, si el alfajor del diablo, como lei por ahi que le dicen, busque por toda la red algun tutorial que expliquen a un usuario principiante como hacer la instalacion y efectivamente lo encontre, era complicado, ya que en el uso de la terminal soy un queso, pero pude salir aireoso, y medianamente me di vuelta.
Ahora el problema, en uno de los pasos del tutorial, me pide que instale el build-essential, un paquete esencial, al menos al parecer, cuando hago esto me salen un monton de palabritas en ingles q no entiendo y al final me aparece E:/ no fue encontrado, error en la instalacion. No son palabras textuales, es mas o menos lo que recuerdo.
Como no tuve otra saltie el paso y segui con lo demas, hasta llegue a que me reconozca el Modem, o sea la lucecita verde de Link esta prendida, solo me falta que salga el gestor para que configure mi cuenta Arnet. Que segun el tutorial no sale o no se activa, por que falle en uno de los pasos, mas precisamente, el de Build-Essential.
Como soy inquieto, busque en internet el paquete(obviamente desde Wxp), lo encontre y cuando quise instalarlo, ya en ubuntu, me sale un error de dependencia, diciendo que falta un paquete llamado lib6 o algo haci, les recuerdo que esto lo hago solo de memoria, puede que me equivoque.
Si alguno fuera tan amable de decirme como solucionar el problema se lo agradecere, me muero por utilizar mi linux al maximo, y dejar de depender de windows, q ya hace rato que quiero cambiarme definitivamente.

Muchas gracias
AngelNochero
Si quieren pueden agregarme al correo:
[email]angeljmena@hotmail.com[/email]

---

### Post by sajnox on 2007-11-13
Bienvenido!!!

A ver, vamos por partes. Por suerte tenes el XP con el que podes navegar por internet. entonces, en esta direccion tenes el paquete que necesitas con las dependencias

[ACA]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbuild-essential%2Fbuild-essential_11.3_i386.deb&md5sum=9555bbff826c8f059d00a824d6285275&arch=i386&type=main") esta el build essential 

Y [ACA]("http://packages.ubuntu.com/feisty/libdevel/libc6-dev") el libc6

Y [ACA]("http://ubuntuforums.org/showthread.php?t=497135&highlight=instalar+sin+internet") te dejo un post de como instalar paquetes sin internet

Bueno, probalo y contanos como fue

Suerte!!

---

### Post by rretamar on 2007-11-13
Primera (y seguramente infructuosa) opción: llamar a los Arnet Boys y plantearles tu problema: de esa forma quizás quede asentado que hay gente que usa eso llamado LINUX y que no todo es Windows en la vida. Hablemos, contemos que SO estamos usando, y sobre todo, reclamemos. 

Otra alternativa (con mayores posibilidades de un desenlace feliz) es reclamar a Arnet que el MT810 no funciona bien (que es cierto...los problemas son varios y ampliamente conocidos) y exigir que te lo cambien por uno del tipo "dual" (o sea con port USB y Ethernet). Si con la primera llamada no da resultados, volvé a interntarlo, porque no hay un criterio "inamovible" al respecto y depende quien te toque del otro lado de la línea (y la forma en que te sepas "imponer").

Reemplazar ese infame soft-modem por un router ethernet es lo mejor que se puede hacer. 

Saludos !

---

### Post by Illuminator on 2007-11-14
El build-essential está en el CD de instalación, si podes conseguir uno entonces copia y pega lo siguiente en la consola:

```
sudo apt-cdrom add
```

```
sudo aptitude install build-essential
```

---

### Post by angelnochero on 2007-11-14
Miren probe de todas las formas antes mencionadas....

con el apt-cdrom

no me lee la lectora (tengo el ubuntu alternate quemado en un disco)

el caso es que llegue al punto que al instalar todos los paquetes necesarios para build-essential, me falta uno, el g++...para instalar ese  paquete tengo que tener el lib6++ o algo haci...pero que pasa cuando voy a instalar el lib6++, me dice que me falta el g++...y haci sigue el circulo.

Haci que no se realmente lo como solucionar el tema.

por otro lado....les digo que el cd me lo reconoce en modo virtual o sea puedo acceder a el tranquilamente mediante el explorador, pero no haci desde la terminal. me aparece "E:/ no esta" o algo haci con mas palabras. Ya me estoy desanimando.

---

### Post by sajnox on 2007-11-15
> **angelnochero said:**
> 
por otro lado....les digo que el cd me lo reconoce en modo virtual o sea puedo acceder a el tranquilamente mediante el explorador, pero no haci desde la terminal. me aparece "E:/ no esta" o algo haci con mas palabras. Ya me estoy desanimando.

Es raro eso, en que carpeta se monto el cd?

---

### Post by User21 on 2007-11-15
Este es el "ULTIMATE ALFAJOR DEL DIABLO COMO" , traido a vosotros gracias a DrJuano... Con el, ya he evangelizado MUUUCHOS alfajores del diablo, y ahora son solo simples "tapitas de exquisita masa con dulce de leche" del Señor!!! Amén! 

No dejes de visitarlo! [http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810](http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810) 

Gracias, Dr Juano.. :)

Con eso, deberias salir como cachetazo!

---

