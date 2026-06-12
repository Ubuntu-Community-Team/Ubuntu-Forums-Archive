---
title: "Bug Bios"
date: 2007-10-26
forum: Argentina Team
---

### Post by Apipote on 2007-10-26
Es espantoso.
Trato de bootear, para instalar, en mi compaq presario f566 y tanto en ubuntu como en xubuntu 7.10 x32 me sale BUG BIOS y se cuelga y no progresa la instalación.
Si uso las versiones x64 ( es un turion x64), no sale el "bug bios", pero luego de cargar el kernel con muchos errores, se cuelga y se pone gris brillante la pantalla.
No puedo irme de Vista parece........
Ayuda por favor !
Gracias.

---

### Post by sajnox on 2007-10-26
Epa apipote,

No habias podido con esa maquina con Feisty??

Probaste arrancar con la modificacion en el inicio de vga=0

WanderingKnight estoy seguro que nos puede dar una mano (WK es la misma maquina que Nati llevo a la cafeconf para que le hagan la instalcacion)

Saludos

---

### Post by Apipote on 2007-10-26
Si probe esa opcion en "other options" y nada.......

---

### Post by niko_3100 on 2007-10-26
instala el partition magic y edita la particion y deja espacio libre y intenta asi. Te cuento yo tngo una compaq v3415 pero el vista me duro dos horas, primero con el cd de xp formatie todo y instale xp y despues ubuntu feisty. Ahora estoy con feisty escribiendo sin vista y con el bios bien jejej!!! Cualquier cosa agregame al msn no creo que el bios sea distinto el hard de tu notebook y la mia es muuuuuuy parecido.

---

### Post by Apipote on 2007-10-27
Partition magic? no entiendo.
Ahora formatee todo, y le puse un vista x32 oem que yo tenía. Pero antes, hice el backup de toda la porqueria pesada que trae de fábrica.

La version x32 de gusty , me da "bug bios" y no vale la pena romperse la cabeza si la x64 no da "bug bios"
Solo que se clava en medio de la carga del live cd.
Voy a probar con el alternate.
Otras ideas?
Alguien probó wifi con los drivers de ubuntu "propietarios" broadcom?

---

### Post by WanderingKnight on 2007-10-27
> 
Si uso las versiones x64 ( es un turion x64), no sale el "bug bios", pero luego de cargar el kernel con muchos errores, se cuelga y se pone gris brillante la pantalla.

Eso se solucionaba haciendo lo siguiente:

En el GRUB, apretas "e" sobre el kernel que queres bootear, y le agregas:

```
noapic vga=791
```

...le das enter y apretas b para bootear.

Igual me llama much la atencion lo de la version 32 bits.

> 

WanderingKnight estoy seguro que nos puede dar una mano (WK es la misma maquina que Nati llevo a la cafeconf para que le hagan la instalcacion)

La de Natalia era una f500, no se si habra alguna diferencia. Igual yo no pude configurar el wireless, tuvieron que updatear el firmware desde otra laptop igual.

---

### Post by sajnox on 2007-10-27
[quote]a de Natalia era una f500, no se si habra alguna diferencia. Igual yo no pude configurar el wireless, tuvieron que updatear el firmware desde otra laptop igual.[/code]

El tema del wireless es por o ultimo que me preocuparia, ademas creo que gutsy venia con mejor soporte para las placas wifi

Saludos

---

### Post by Apipote on 2007-10-28
Wandering, 
Por favor, hace de  cuenta que tengo 5 años y guiame.
Yo pongo el livecd y booteo, en que momento y a donde agrego ese parámentro?
Con el livecd f6 "other options" ese parametro no funciona

Sajnox.
He leido que si bien gutsy trae drivers, para las placas bradcom wifi, estos "no funcionan"como deberian.

Lamentablemente, no hay mucha experiencia en internet, sobre mi compaq f566.
Ojala algun forero que me lea, y tenga una, exponga su historia.
Slds.

---

### Post by daz! on 2007-10-28
Quise instalar Gibbon en una compaq presario v3415la y me tiró un bug 80 - 81- 82 (no recuerdo bien) .

Intenté con Fedora 7 y lo mismo. 

Revisando vi que varios tenían el mismo problema. No puede resolverlo y quedé con Feisty. 

Parece que Broadcom anda con Gibbon ... pero... encontré los [siguientes post]("http://ubuntuforums.org/showthread.php?t=528618") no muy alentadores con esta actualización. 

Por ahora me quedo con Feisty intentando hacer andar el wireless. 
Voy a probar con este [post]("http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom"). 

Salu´

---

### Post by Apipote on 2007-10-28
Bueno, no hay caso.

Al menos en mi Compaq presario f566la, no pasa el live cd ubuntu 32 bits.

Con los datos de Wandering, pude instalar ubunty y xubunutu de 64 bits.

De terror, los drivers de la broadcom no funcionan y enlentecen la maquina alevosamente, y los drivers de nvidia no funcan bien tampoco.

Seguiré con vista ( que anda bien en esta laptop ) por ahora.
Slds y espero que sirva.

---

### Post by faktorqm on 2007-10-29
aca te da un par de consejos que podes hacer:
++: segun tengo entendido por lo que lei el problema es mas conocido como "bios bug 81" y aparece en todas las distribuciones de gnu/linux. asi que todo mal :++

[http://ubuntuforums.org/showthread.php?p=3596393](http://ubuntuforums.org/showthread.php?p=3596393)

PARTE DE UN POST:

"EDIT/: tratando de instalar el ubuntu me tope con un problema que tuvo otra persona con la misma laptop serie f5000 y vi que la forma de arreglarlo era apretar f6 cuando estaba cargando, y ahi habia que poner un comando corto que era: noapic y arrancaba perfectamente pero con el tuquito todabia nose como hacer, alguna sugerencia?"

lo saque de aca: 

[http://www.tuquito.org.ar/foros/viewtopic.php?p=10284&sid=985e68f2ab9f73893b5bfc290c8d9586](http://www.tuquito.org.ar/foros/viewtopic.php?p=10284&sid=985e68f2ab9f73893b5bfc290c8d9586)

ESTE ES DE DAPPER, pero el problema aparentemente era el mismo y dice mas o menos algo parecido al de arriba:

[http://ubuntuforums.org/showthread.php?t=257912](http://ubuntuforums.org/showthread.php?t=257912)

aca habia que leer mucho, asi que te lo dejo a vos de tarea para el hogar XDxD

[http://ubuntuforums.org/archive/index.php/t-332829.html](http://ubuntuforums.org/archive/index.php/t-332829.html)

sino busca "bios bug 81" en google y ahi te va a saltar, todo lo que puse ahi mas mil cosas que no me fije. espero ke te haya servido. salu2!


OFF TOPIC: FTP DE LA PONTIFICIA UNIVERSIDAD CATOLICA DEL PERU

[http://linux.pucp.edu.pe/downloads/](http://linux.pucp.edu.pe/downloads/)

tiene un par de cosas copadas, manuales y demas.

---

### Post by Apipote on 2007-10-29
Gracias hermano.
Pero linux aún, se tiene que poner las pilas. Falta mucho para ser amigable como win. Es una lástima, pero entiendo porque mucha gente no se quiere pasar a linux aún.

---

### Post by niko_3100 on 2007-11-09
YO tengo una compaq v3415 y me tira ese bug pero me levanta normalmente, quise instalar gutsy y cuadno intenta cargar el live cd me tira un error de microcode con el bcm43xx que es algo del wifi broadcom y muere ahi no levanta el live cd. Tengo feisty que me va de diez y le isntale el wifi con el wine y el driver de xp de la tarjeta wifi broadcom, va de diez. Pero gutsy no me levanta voy a probar con xubuntu 7.10 a ver si por lo menos me levanta el live cd.

---

### Post by clasificado on 2007-11-10
> **Apipote said:**
> Gracias hermano.
Pero linux aún, se tiene que poner las pilas. Falta mucho para ser amigable como win. Es una lástima, pero entiendo porque mucha gente no se quiere pasar a linux aún.

Si te cansaste de intentar, proba esperando 6 meses a que salga la proxima version de ubuntu con mas soporte de hardware, ya que las notebooks tienen un hardware ESPANTOSO y por costumbre absolutamente incompatibles para lo que no fueron preparados. (Hay que agradecerles a los muchachos del kernel, que hacen un laburo increible con esto)

Puede que linux no sea amigo de todos asi como windows no le cae bien a todo el mundo. En mi caso, empeze con linux porque el vista no me quiere (p3 933mhz, una pc de hace 5 años). Ahora cuando uso windows me siento incomodo :)

Clasificado

pd: no todos son como uno; hay mucha gente que no se pasa, cada uno por sus propios motivos.

---

### Post by niko_3100 on 2007-11-10
Nah ahi estoy en desacuerdo con vos, el hardware de la notebook por lo menos a mi en 3 notebooks que hice intalacion de ubuntu me tomo todo de 10, creo que al contrario como es hardware mas standar es mas seguro que te tome todo de una.

Igual sigo insistiendo feisty funciona mejor que gutsy.... por lo menos es mi conclusion que saque.

---

### Post by Apipote on 2007-11-11
Que se yo, mira tengo ahora a esta laptop f566 con xp pro y vuela, el vista con aero también anda bien aca, pero es medio lenteja.
En la de los chicos, un athlon con 2 gb de ram y una video de 256 vista vuela con aero activado.
Voy a seguir esperando a que cuando instale ubuntu me levante todo de una sin mezclar drives de win como he leido por acá.
Slds

---

### Post by niko_3100 on 2007-11-11
Que tiene de malo instalar mezclar drives? que son drivers? son secuencias de 1 y 0 que la computadora interpreta. En teoria para la computdaroa deberia ser lo mismo un .exe o un .inf o un .bin

---

### Post by Apipote on 2007-11-12
Quizas tengas razon Niko.
Es un mambo mío, no me gusta nada de win en linux.
Slds

---

### Post by faktorqm on 2007-11-15
che apipote, y con la 7.04 te tira lo mismo? 

en la page de compaq hay un upgrade de bios, que dice que soluciona un problema (para windows, pero lo hace) de la bateria.

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-54827-1&lc=en&cc=us&dlc=en&product=3446257&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-54827-1&lc=en&cc=us&dlc=en&product=3446257&os=228&lang=en)

ahi te deje el link, te aviso por las dudas que flashear el bios no es una pavada, no te quiero asustar, pero me parece que lo tenes que saber, por ejemplo, si se te apaga en el medio de la "flasheada" si no tiene crashfree o 2 bios, la compu no te prende nunca mas y la tenes que llevar a soporte tecnico de ellos. pensa que estas poniendo el software base de la compu para que el resto de los sistemas operativos trabajen sobre ella. tene cuidado y la bateria bien cargada cuando lo hagas, si lo haces.

esto de todas maneras capaz no te soluciona el problema, pero siempre es mejor tener el bios actualizado. salu2! y si tenes dudas pregunta.

---

### Post by Apipote on 2007-11-20
Gracias por el dato Faktorqm, lo hice, y ya puedo instalarlo, incluso a pclinux, pero no andan los drivers nativos linux para la broadcom wifi de porqueria.
habra que esperar.
Slds

---

### Post by faktorqm on 2007-11-21
bueno, bien ahi entonces!! ya tenerlo isntalado es un paso. que placa wifi tenes? marca y modelo y cosas que ya viste por favor. salu2!

---

### Post by Apipote on 2007-11-21
No es mucho.
Sigo con xp, pero ya he leido en todo lo que se encuentra google y concluyo:

Pclinux es mas amigable que Ubuntu para estas laptop ( Compaq presario serie f500 ) que se llevan muy mal con las distros derivadas de Debian.

La placa wifi es la peor para linux.........la broadcom, no entiendo  porque, pero no le encuentran la vuelta a los drivers nativos de linux...........aún.

Usan esta porqueria de placa wifi con una emulación ( ndiswrapper) de los drivers de xp, que me parece horrible. Pero no queda otra si queres usar wifi.

Estoy convencido que con el tiempo esta serie de laptops estará integramente soportada por linux, y sugiero esperar.

Mientras, anda muy bien con xp, y muy lenta con el vista preinstalado.

Slds a todos y espero les sirva.

---

### Post by _X_ on 2007-12-30
buenas.. primer post x aqui :P
tmb tgo un F566 y si bien logre instalar ambas versiones a pesar del bug bios, la version d 32bit era inutilizable (lo hice, entre tantos cmd con un noirqdebug y no recuerdo si tmb con un acpi=off o force)
siguiendo cn el tema del bug bios y el updete al bios... si le pasa algo a la notebook.. no me lo puedo permitir... mi duda es cuanto dura el proceso? (me da cierto miedito actualizarle el bios)

Saludos!

---

### Post by faktorqm on 2007-12-30
hola, dura dependiendo de cada computadora, 2 o 3 minutos, no le tengas miedo, si tenes una notebook, asegurate de que no se te acabe la bateria y de no perder la conexion a la red electrica por las dudas, nada mas. es un proceso lo mas normal del mundo. salu2!

---

### Post by _X_ on 2007-12-30
el miedo q tgo es el mismo q tube antes d flashear alguno d mis celulares, un moto v191, muerto x flash ¬¬ y un rokr E2 q no solo NO muere x mal flasheo sino q tmb tiene linux! :D (con todo lo q implica) es cosa d juntar coraje... gracias x la respuesta!

---

### Post by Apipote on 2008-02-27
Nada muchachos.
Todo lo que sea laptop HP ( Compaq ), es NADA amigable con linux. 

He comprobado lo que se dice en la red: no hay distros que funcionen adecuadamente con esta laptop ( la mia f566 ). 

He probado todas las buntu, pclinuxos y mepis, pues algunos las han podido instalar.
El proceso es penoso, los drivers nativos de linux, para la wifi broadcom, están rotos, usan ese ndswrapper horrible que mete drivers de xp ( si, así como lees ), la pantalla se cuelga, y mucho más. Probá.

Lamentablemente, está programada para la porquería de VISTA, e incluso meterle xp es un parto ( pero lo hice ).

Las alfas de Hardy, parece que siguen con los drivers nativos para la bradcom rotos. No se el resto de los bugs, si están reparados.

Sorry por las malas noticias.

---

### Post by niko_3100 on 2008-02-27
Yo teng una compaq v3415 con feisty, es verdad no pude instalar gutsy pero tngo feisty isntalado con wifi y todo con ndispwrapper. Tengo un hp compaq nx9030 media viejita pero levanto gutsy de 10, intentaron instalar feisty??

---

### Post by Apipote on 2008-02-27
La verdad..........Festy no intenté. Pruebo y te cuento.

---

### Post by faktorqm on 2008-02-27
Probaste con FreeBSD? no te quiero meter en un entuerto, no se que tipo de usuario sos, si un gnu/linux lo manejas de taco, te va a resultar apenas dificil, si no vas a tener que leer leer y leer. Probalo aunque sea para sacarte la duda, a ver si el nucleo *BSD se la banca contra tu notebook. Salu2!

p.d.: podes probar OliveBSD, que creo que es un freeBSD o un openBSD version live...

---

### Post by Apipote on 2008-02-27
> Probaste con FreeBSD?

No, pero me supera sin duda alguna.
Gracias igualmente, supongo es cuestión de tiempo.

---

### Post by niko_3100 on 2008-02-27
Primero proba con feisty a ver que si levanta todo bien.

---

