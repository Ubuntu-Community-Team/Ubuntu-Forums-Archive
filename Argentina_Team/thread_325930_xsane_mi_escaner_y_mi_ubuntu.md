---
title: "xsane mi escaner y mi ubuntu"
date: 2006-12-26
forum: Argentina Team
---

### Post by MeduZa on 2006-12-26
Hola a todos los hermanos ubuntiales argentinos ;) , papa noel (si el mismo viejo gordo y barbudo ^_^ ) me trajo un scanner de regalo :D , y hasta hoy todo lo que e enchufado a la pc con ubuntu es magicamente detectado y usado :) venia bien hasta q enchufe el scanner. y el xsane no me lo detecta :(

Entonces como hago con todo lo que no me anda o necesito saber como hacerlo andar, empece a buscar por TODA la web una solucion.
Primero q nada mi escaner es un Canon Pixma MP530 (si es una impresora all in one, la printer anda perfecto pero el scaner mmm)
En la pagina de sane dice q mi modelo anda perfecto con la ultima version.
[http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=pixma+mp530&bus=usb&v=04a9&p=1712]("http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=pixma+mp530&bus=usb&v=04a9&p=1712")
hasta ahi la peor parte esta pasada, ahora siguiendo algunas guias encontre q mi ubuntu lo detecta:

> sane-find-scanner -q
found USB scanner (vendor=0x04a9 [Canon], product=0x1712 [MP530]) at libusb:002:007


despues de ahi para adelante no entiendo q hacer, supuestamente tengo todo instalado no se q es lo que tengo q editar para agregarlo, segun entendi el modelo que tengo q usar es el MP150 pero ni idea. el xsame me sigue diciendo q no ahi una scanner detectado (ni tratando en admin)
Despues de editar un archivo del sane, el sane ahora SABE q es un canon MP530 antes solo detectaba vendor=0x04a9 , product=0x1712 ) at libusb:002:007
Alguna idea?

[URL="http://ubuntuforums.org/showthread.php?t=325930&page=2"]EDIT: PROBLEMA SOLUCIONADO IR AL FINAL DEL TEMA =D> 
EDIT: PROBLEM FIXED GO TO THE END OF THE THREAD =D> [/URL]

MeduZa

---

### Post by elgatogordo on 2006-12-26
te da un mensaje de error?

---

### Post by beuno on 2006-12-26
Aca se rompieron la cabeza un rato:

[http://ubuntuforums.org/showthread.php?t=143504](http://ubuntuforums.org/showthread.php?t=143504)

(se que no es tu modelo, pero quizas te sirva alguno de los pasos)

---

### Post by MeduZa on 2006-12-26
> **elgatogordo said:**
> te da un mensaje de error?

ningun error, lo que me llama la atencion es que el comando sane-find-scanner detecta el scaner perfecto pero el comando scanimage -L no ve nada es como q en el medio falta algo, como decirle al sane q el scanner esta ahi pero no se donde :(

Todos los demas que encuentro por ahi el problema q tienen es que sane-find-scanner no les detecta nada pero a mi si

---

### Post by spg76 on 2006-12-26
Perdón, te conteste lo que ya habías hecho.

---

### Post by MeduZa on 2006-12-26
ok voy descartando posibilidades a ver si esto ayuda a q me ayuden :)

en el screen se ve lo que me sale
ok 

1) eso no es :rolleyes: 
2) tampoco es porque el scanner esta mas al pedo q yo
3) ya probe y tampoco es
4) seguro es esta :confused: pero como hago eso ya lei el man ese y no entiendo lo que tengo q hacer
5) lo mismo q arriba no entiendo como se hace eso ](*,)  mi backend se llama sane-pixma
6) eso no es 

alguno sabe como hacer la 4 o la 5 ? :confused:

---

### Post by elgatogordo on 2006-12-27
fijate por acá
[http://www.ubuntu-es.org/index.php?q=node/26739](http://www.ubuntu-es.org/index.php?q=node/26739)

---

### Post by jpmorelli on 2006-12-27
A mi me paso con un HP Photosmart 3180 ( las del ultimo plan canje de HP ) que cuando configure la impresora, todo bien (USB) imprimia, etc, pero no escaneaba.
Un día la veo a mi mujer escaneando unas cosas y miro la pantalla y que veo ???? UBUNTU !!!! no estaba en WIndor !!!!! COMO HICISTE ?, como hice que ?, HACERLO ANDAR ???, No hice nada, estaba en Ubuntu y me dio fiaca cambiar y busque la utilidad y vi esta ( xsane ) que decía que era para escanear, abrí y escaneé...
:o 
Conclusión: Dásela a alguien que no sepa y te lo arregla, jaja

---

### Post by elgatogordo on 2006-12-27
instalate desde el synaptic el quiteinsane
lo abris con la  terminal escribiendo quiteinsane
te va a aparecer la lista de escaneres
haces doble click en el tuyo
se te abre una ventana con opciones
trata de escanear a ver que pasa
una cosa que me pasaba a mi con la impresora y que a lo mejor te sirve para el multifunción. tenia que enchufar primero la impresora y tenerla prendida y despues enchufar y prender la computadora para que me imprimiera

---

### Post by MeduZa on 2006-12-27
creo que tengo q compilar los mp150-0.12.2 -.- lo peor es q no entiendo q son si el same es vercion 1.0.18 (backend) y 1.0.14 el sane
segun esta guia: [http://home.arcor.de/wittawat/pixma/ubuntu-howto.html](http://home.arcor.de/wittawat/pixma/ubuntu-howto.html)
y este es el resultado T_T:

sudo make (o sin sudo)
cc  -Wall -W -DWITHOUT_SANEI -DHAVE_FCNTL_H -DHAVE_STDINT_H -g -O -DWITH_RESMGR -fPIC -pedantic   -c -o usb.o usb.c
usb.c:31:28: error: linux/compiler.h: No such file or directory
usb.c: In function &#8216;usbSendControlMsg&#8217;:
usb.c:707: warning: unused parameter &#8216;ep&#8217;
make: *** [usb.o] Error 1

que puede ser?

---

### Post by MeduZa on 2006-12-28
Bueno lo logre, ya me anda el scanner :) gracias a todos por las ideas orientativas, dejo esto a modo de how-to:
Para mi scaner Canon Pixma MP530 (y todos los PIXMA) segui esta guia:
[http://home.arcor.de/wittawat/pixma/ubuntu-howto.html]("http://home.arcor.de/wittawat/pixma/ubuntu-howto.html")
El primer problema que tuve es que no lo podia compilar, me puse en contacto con el/la que escribio eso (no se que es) y muy amablemente me dio un par de ideas de donde podia estar el problema. (me dijo que eso lo hizo y probo en dapper y no en edgy por eso el error) al final logre compilar los nuevos backend (llamemoslos drivers), luego de eso, continue los pasos de la guia y listo ya andaba el sane (modo linea de commando)
PEEEEROOOOOOOOOO el xsane (sane para X) no andaba, me seguia diciendo que no veia un scanner, entonces me di cuenta que el xsane guarda la info del backend en otro lado (me di cuenta recien) y listo cree otro link de /usr/lib/sane/tu_backend a /usr/local/lib/sane/tu_backend.so y cree una copia .so.1 (reemplace los 2 q habia) el xsane a mi entender pone las cosas en local y el sane en lib.
y listo con eso andubo el xsane y anda como patada ninja del ninja negro de titanes en el ring (me re bole :mrgreen: )

If some body is looking for information about how-to make the Canon Pixma MP530 works (or similar model), please contact me, I can translate this text to english.

Saludos y espero le sirva a otro perejil tan perdido como yo :mrgreen:

---

### Post by elgatogordo on 2006-12-28
no dejes de probar el quiteinsane, como software para escaneo es mucho mejor

---

### Post by MeduZa on 2006-12-29
> **elgatogordo said:**
> no dejes de probar el quiteinsane, como software para escaneo es mucho mejor

encima q me llevo un scanner andando me regalan alto dato XD 
ahora lo pruevo
aunque mas completo q este ? tiene todo :???:

---

### Post by elgatogordo on 2006-12-29
fijate si tenes instalados el gocr y el ocrad, son para reconocimiento óptico de caracteres. lo instalas desde el synaptic y se uxan con todos los programas de escaneo

---

### Post by Niccpaganini on 2007-01-26
Hola MeduZa, como hiciste para lograr instalar instalar el driver en edgy? Obtengo el mismo error que posteaste anteriormente.

---

### Post by MeduZa on 2007-09-06
viene instalado de fabrica pero tiene un error en un link por eso no anda, basicamente lo que sucede es que, el driver se llama mp 150 y funciona para todas las mp pero se olvidaron, o aun no existia, la mp530 entonces no lo pusieron link, pero es el mismo archivo para la mp150, segui la guia en el link que puse mas arriba, yo compile los drivers pero no era necesario ya estaban en el sistema!

---

### Post by rojojuan on 2007-09-06
> **MeduZa said:**
> Bueno lo logre, ya me anda el scanner :) gracias a todos por las ideas orientativas, dejo esto a modo de how-to:
Para mi scaner Canon Pixma MP530 (y todos los PIXMA) segui esta guia:
[http://home.arcor.de/wittawat/pixma/ubuntu-howto.html]("http://home.arcor.de/wittawat/pixma/ubuntu-howto.html")
El primer problema que tuve es que no lo podia compilar, me puse en contacto con el/la que escribio eso (no se que es) y muy amablemente me dio un par de ideas de donde podia estar el problema. (me dijo que eso lo hizo y probo en dapper y no en edgy por eso el error) al final logre compilar los nuevos backend (llamemoslos drivers), luego de eso, continue los pasos de la guia y listo ya andaba el sane (modo linea de commando)
PEEEEROOOOOOOOOO el xsane (sane para X) no andaba, me seguia diciendo que no veia un scanner, entonces me di cuenta que el xsane guarda la info del backend en otro lado (me di cuenta recien) y listo cree otro link de /usr/lib/sane/tu_backend a /usr/local/lib/sane/tu_backend.so y cree una copia .so.1 (reemplace los 2 q habia) el xsane a mi entender pone las cosas en local y el sane en lib.
y listo con eso andubo el xsane y anda como patada ninja del ninja negro de titanes en el ring (me re bole :mrgreen: )

If some body is looking for information about how-to make the Canon Pixma MP530 works (or similar model), please contact me, I can translate this text to english.

Saludos y espero le sirva a otro perejil tan perdido como yo :mrgreen:

Hola Meduza:
Tengo el mismo problema tuyo con un scanner canon. Por favor, podés describir más detalladamente qué tengo que hacer para que me funcione el scanner en el entorno gráfico? (me anda fenómeno con sane pero no con Xsane). Te aclaro que me inicié poco tiempo con Ubuntu. Lo que puedas aportar será bienvenido

Gracias

---

