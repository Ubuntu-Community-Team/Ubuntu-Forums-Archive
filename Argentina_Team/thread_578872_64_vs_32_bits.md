---
title: "64 vs 32 bits"
date: 2007-10-17
forum: Argentina Team
---

### Post by Apipote on 2007-10-17
Tengo una notebook con un turion de 64 bits, y no se que instalarle si ubuntu 64 o 32 bits.

Basicamente me volvia loco no poder ver bien las paginas y videos  por falta de "flash" y gnash no funciona bien en Festy.

Con Gutsy 64 andará bien Flash o Gnash, sin emuladores y cosas raras?

El rendimiento de un hardware de 64 bits con Gutsy de 32 bits, es bueno?

Gracias.

---

### Post by facundocorradini on 2007-10-17
En general, no hay mucha diferencia de rendimiento entre los sistemas de 32 y 64 bits (el potencial está, pero las aplicaciones aún no lo aprovechan),

Con respecto al flash, sé que gutsy viene con un gnash pulenta, pero no sé si se bancará youtube (imho, única razón para querer tener flash...)

---

### Post by Apipote on 2007-10-17
Que sea 32 bits entonces Facundo.
:confused:

---

### Post by tzulberti on 2007-10-17
> **facundocorradini said:**
> En general, no hay mucha diferencia de rendimiento entre los sistemas de 32 y 64 bits (el potencial está, pero las aplicaciones aún no lo aprovechan),
Totalmente de acuerdo en este punto


> **facundocorradini said:**
> Con respecto al flash, sé que gutsy viene con un gnash pulenta, pero no sé si se bancará youtube (imho, única razón para querer tener flash...)

Ahora en 64 podes instalar flash como si estuvieras en 32... apt-get install flashplugin-nonfree, y automaticamente te va a bajar todos los paquetes necesarios.

---

### Post by facundocorradini on 2007-10-17
> Ahora en 64 podes instalar flash como si estuvieras en 32... apt-get install flashplugin-nonfree, y automaticamente te va a bajar todos los paquetes necesarios.

ENSEEEEEERIO???????  ahora me hacés dudar a mí sobre si cancelo el gutsy q YA estoy bajando y pongo a bajar el de 64...

---

### Post by Apipote on 2007-10-17
tzulbert........pero anda bien, no esta emulado ni nada??

---

### Post by sajnox on 2007-10-17
64 vs 32 bits, la pregunta del millon en estos dias.

En mi opinion sirve siempre y cuando este seguro de como se le saca provecho a los 64 bits, si no lo tenes muy claro opta por la de 32.

[Aca]("http://ubuntuforums.org/showthread.php?t=574495&highlight=64+bits") y [Aca]("http://ubuntuforums.org/showthread.php?t=538377&highlight=64+bits") te dejo links con charlas que hubo en el foro. 

Si pones en el buscador de este foro "64bits" tenes muchas respuestas mas que seguro te pueden ayudar

Saludos,

---

### Post by tzulberti on 2007-10-18
> **Apipote said:**
> tzulbert........pero anda bien, no esta emulado ni nada??

Anteriormente para tener flash tenias que vos instalar unas librerias ia32-lib, nspluginwrapper (o algo similar). Ahora te las instala cuando instala flash por apt, asique es mas simple la instalacion.

En verdad si esta emulado porque es el flash de 32 bits (no existe una version para 64 bits). Yo lo vengo usando desde el viernes, y no tengo problemas. Puedo ver los videos que me aparecen en los distintos blogs sin problemas, asique me esta funcionando bien.

Saludos,
TZ

---

### Post by euzkoarima on 2007-10-22
Buenísimo que ahora sea mucho más simple instalar flash en 64 bits. Pregunta: hay una "facilidad de instalación" similar para wine????
Y otra: si instalas wine en 64 bits (del modo que sea, pero supongamos que al final quedo todo bien instalado) lo que podes emular y lo que no, es igual a la versión en 32 bits? o hay cosas que en 32 te van correr y en 64 no.

Saldos,

---

### Post by tzulberti on 2007-10-22
Creo que se puede instalar el wine con el apt-get (no estoy seguro de esto).
Sin embargo, si estoy seguro que el wine que te instalas es uno de 32... Es decir, no existe un Wine que simule un Windows de 64 bits, todos simulan ser uno de 32 bits.

---

### Post by Apipote on 2007-10-22
Pero si el ubuntu x32 tiene el mismo rendimiento que el x64, creo que no tiene sentido renegar, por más que tengas hardware de 64 bits.
No?
:confused:

---

### Post by facundocorradini on 2007-10-22
La conclusión de todas estas charlas, es que de momento no todos los paquetes están disponibles para 64 bits, y los que sí (en su mayoría) no cambia el rendimiento.


Si quieres evitar complicaciones, lo mejor sigue siendo instalar el sistema de 32 bits.

---

### Post by Apipote on 2007-10-22
Facu
Mi laptop tiene 1gb de ram y un Turion de 64.
Se banca bien el Ubuntu o mejor Xubuntu?
Hasta ahora en mi pc, el xubuntu 7.04 me anduvo brutal.

---

### Post by facundocorradini on 2007-10-22
> Facu
Mi laptop tiene 1gb de ram y un Turion de 64.
Se banca bien el Ubuntu o mejor Xubuntu?
Hasta ahora en mi pc, el xubuntu 7.04 me anduvo brutal.

????!!!!!!!!!!!!!!!!! 


tu máquina supera cuatro veces los requerimientos para ubuntu.  Ponle el de 32 bits que te va a andar espectacular! 

:D


(mi laptop es apenas un celeron D de 1.3ghz, 512 RAM y video intel 915, y corre ubuntu con los efectos al máximo sin ningún problema :D)

---

### Post by sebadigri on 2007-10-22
Pero se puede instalar Aplicaciones 32 bit en la 64 bit? a mi me paso la semana pasada en la 7.04 que me bajaba todos packetes .deb i386 y no me funcaba ninguno por q era 64 bit y dije fue meto 32 bit..y ahora la gutsy la meti 32 bit tmb jaja diganme total ya instale 5 veces ubuntu desde q lo empece hace la semana pasada jaj

Sea por estas cosas o por que con el vmware player de alguna forma genere errores en la particion y termine de romper intentando repararla..Ahora uso virtualbox

---

### Post by MeduZa on 2007-10-23
solo deberias instalar 64bits si tenes mas de 4gb de ram, usas aplicaciones que usen  coma flotante mucho, o sos queres ayudar en el desarrollo de aplicaciones en 64btis, sino quedaten en 32bits, de por si el de 64 deberia comer mas memoria que el de 32bits (por logica)
asi que por ahora no le veo el sentido.

---

### Post by faktorqm on 2007-10-23
> **MeduZa said:**
> solo deberias instalar 64bits si tenes mas de 4gb de ram, usas aplicaciones que usen  coma flotante mucho, o sos queres ayudar en el desarrollo de aplicaciones en 64btis, sino quedaten en 32bits, de por si el de 64 deberia comer mas memoria que el de 32bits (por logica)
asi que por ahora no le veo el sentido.

No entendi. como que en 64 come mas memoria que en 32??!?!?! no es asi me parece, pero por las dudas contame si es asi a ver si el que esta equivocado soy yo. salu2!!

---

### Post by facundocorradini on 2007-10-23
Estoy de acuerdo con  faktorqm.  No veo razón por la que 64 debiera consumir más que 32...

---

### Post by MeduZa on 2007-10-23
> **faktorqm said:**
> No entendi. como que en 64 come mas memoria que en 32??!?!?! no es asi me parece, pero por las dudas contame si es asi a ver si el que esta equivocado soy yo. salu2!!

el registro de memoria es del doble de tamaño, lo que antes usaba 32bits ahora necesita 64bits, no significa que vaya a ser el doble de memoria usada, pero algo aumenta, es normal que un sistema operativo que maneja registros mas grandes use mas memoria, capas recuerdan el paso de 16bits a 32 bits que todo necesitaba mas memoria, yo ya lo habia vivido mucho antes cuando pase de 8 bits a 16 bits ^_^



Saludos

---

### Post by juanman on 2007-10-23
> **MeduZa said:**
> el registro de memoria es del doble de tamaño, lo que antes usaba 32bits ahora necesita 64bits, no significa que vaya a ser el doble de memoria usada, pero algo aumenta, es normal que un sistema operativo que maneja registros mas grandes use mas memoria, capas recuerdan el paso de 16bits a 32 bits que todo necesitaba mas memoria, yo ya lo habia vivido mucho antes cuando pase de 8 bits a 16 bits ^_^


La verdad q se siente el mayor consumo de memoria. Además del registro de memoria más grande (q no debe ser muy grande, me parece) está el hecho de q si usás programas de 32b en un sistema de 64b, también tendrás q cargar en memoria las mismas librerías de 32b aparte de las de 64.
En mi caso, me funciona más rápido un sistema de 32b q uno de 64b, ya q con éste último, al consumir más memoria, mis 512mb de ram no aguantaban y pasaba mucho tiempo "swapeando" y "deswapeando", lo q enlentece mucho más q el aumento de velocidad q pueda tener el procesador...

Saludos

---

### Post by facundocorradini on 2007-10-23
Pues yo tengo la versión de 64 bits en mi desktop, y el rendimiento está a favor de esta (hay muy poca diferencia, pero para fanáticos es genial). 

Pero de hard no entiendo tanto y no estoy capacitado para discutir los porqués.

Sin embargo el consejo sigue siendo el mismo: al usuario comun, que recién empieza, le conviene usar el sistema de 32 bits.

---

### Post by tzulberti on 2007-10-23
Yo tengo 2gb de memoria ram,y apenas ciento la diferencia entre un 64 y uno de 32 bits.

---

### Post by faktorqm on 2007-10-24
Hola, tiene razón meduza. Yo la limé.

Para que entiendan un poco, es más o menos asi: en 32 bits, por ejemplo, para representar el número "1" se representa como "00000000000000000000000000000001", el "2" se representa como "00000000000000000000000000000010", el tres como "00000000000000000000000000000011" y asi sucesivamente hasta ""11111111111111111111111111111111" que vendria a ser 2 elevado a la 32 MAS 2 elevado a la 31 MAS 2 elevado a la 30 y asi sucesivamente...........

ahora bien, cuando estamos en 64 bits, la representacion de un "1" por ejemplo deberia ser "0000000000000000000000000000000000000000000000000000000000000001", la del "2" seria "0000000000000000000000000000000000000000000000000000000000000010", la de "3" seria "0000000000000000000000000000000000000000000000000000000000000011", y asi........

por lo tanto, cada tamaño se va al doble, o sea, lo que antes fisicamente ocuapaba 32, ahora ocupa 64. entonces claro, si antes tenias 512mb de ram, para guardar una entero, (en C por ejemplo) necesitas 4 bytes, en 32 bits, pero en 64, son 8. esto en C se soluciona poniendo sizeof (variable), en otros lenguajes no se. Entonces en una memoria de 512 mb, donde con 32 bits guardaba supongamos, 128mb, con 64 bits de la misma memoria estas ocupando 256mb.

Bueno, pequeño repaso de teoría. Lo que no estoy tan tan seguro es si el manejo interno de la memoria se hace por bytes o por bits. En teoría, el sistema operativo maneja bytes, el hardware bits, por que sino los desarrolladores nos volveriamos locos!!. pero bueno, basta por hoy. salu2!

---

### Post by Mataca on 2007-10-24
En resumen te consume mas memoria :P

En mi casa tengo 2 pc, ambas con athon 64, una con 2gb y otra con 1gb de RAM y la verdad que probe en ambas la versión de 64 pero no note diferencia alguna.

Me quedo con la de 32 hasta q empiecen a desarrollar mas la arquitectura, quiza es muy pronto todavía.

---

### Post by Apipote on 2007-10-24
Acuerdo con mataca

---

### Post by WanderingKnight on 2007-10-24
El dia que quiera mas de 4 GB de RAM (8 veces lo que tengo ahora!) me paso a 64 bits... por ahora estoy contento en esta arquitectura.

32 bits should be enough to everyone... (?)

---

