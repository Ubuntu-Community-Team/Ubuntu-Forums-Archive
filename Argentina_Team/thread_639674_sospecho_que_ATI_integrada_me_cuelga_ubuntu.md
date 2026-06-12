---
title: "sospecho que ATI integrada me cuelga ubuntu"
date: 2007-12-13
forum: Argentina Team
---

### Post by melvinlopez06 on 2007-12-13
Eso, sospecho que la ATI integrada de mi pc esta jodiendole la vida a ubuntu y este se cuelga cada dos por tres, ni siquiera me ha dejado mandar este post al foro, lo he tenido que hacer desde win2.

**Que tengo:**
Motherboad pcchips
ATI Radeon Xpress 200 series integrada
Intel P4 3.2 Ghz HT
1 Gb Ram DDR
Disco seagate 250Gb modelo ST3250824AS
cdrom benq

**Este es el escenario:**
La pc es de mi trabajo, es una computadora armada, aqui en el work le pusieron windows xp prof y todo anda de lujo, juegos y todo (los ratos de oscio del medio dia jeje).
El win se jodio como al año de uso (raro) y se reinstalo todo y aproveche a dejar una particion de 40 Gb para linux ya que tenian un proyecto por aqui y pues se iba a usar una maquina como server de apache, php y mysql en un linux.

Un buen dia me decidi a instalar ubuntu 7.04 para hacer pruebas sobre unos programas en php, y probe el live cd como una hora y luego instale, todo perfecto, se tardo a lo sumo 15 minutos. Reinicio y cargo ubuntu (literalmente volo, tardo 28 segundos en mostrar el escritorio) la sorpresa fue que comence a ocuparlo, instalar php, paquetes de lenguaje, etc etc y zaz el primer golpe, colgada por completo, nada pero nada funcionaba, ni reiniciar las X, ni mover el mouse, ni pasar a la consola ni siquiera el numlock funciona pues, si escucho musica hasta esa se queda trabada.

Bueno eso paso como a los 20 minutos de uso, reinicie y vuelve a pasar, hoy trabajando con openoffice como a los 15 minutos, y asi se ha colgado infinidad de veces, todas haciendo algo distinto, usando firefox, escuchando musica, navegando, incluso solo usando solo el editor de textos.

No es hardware, todo esta bien puesto y funcionando porque despues de los cuelgues de ubuntu (y cuando me canso de eso) reinicio y trabajo en win y cero problemas.

Pense en que talvez los drivers de video fallaban, e instale los propietarios y se volvio a colgar. Salio el ubuntu 7.10, y actualice con el alternate disk y se colgo en plena instalacion.
Reinstale ubuntu con el 7.04 nuevamente, actualice con el alternate y todo bien, instale los drivers propietarios de ATI y todo bien, use la maquina mas de una hora, abri firefox y murio, colgada otra vez.

Salieron los nuevos drivers de ati y los instale siguiendo una guia en adslworld (o algo asi), estos funcionaron correctamente (pese a que la pc se colgo como 8 veces durante todo el proceso) pero al final quedaron instalados, con rendering 3D y toda la pelota, hasta instale compiz y todo perfecto, el cubo gira suave, muy suave y rapido, el 3D funciona mas que bien, probe penguin racer y bien bello.
Desactive compiz y lo mismo, se colgada al rato de uso. La pc se sigue colgando cada cierto tiempo, es invariable, veces trabajo 15 minutos y se cuelga, otras veces 1 hora, 2 horas y se cuelga, haga lo que haga, no creo que sea hardware porque no encuentro logico que despues de trabarse 4 veces, reinicie a windows y trabaje todo el dia tranquilamente ahi.

No puedo ver si el sistema sigue vido despues de colgado porque solo yo uso linux. He visto los log del xorg y no encuentro nada significativo ya que se borran al reiniciar la pc, pero les dejo el xorg.conf.

Ni con drivers libres ni propietarios para el video deja de colgarse, hice testeo de memoria con la opcion que da ubuntu en el grub y todo tranquilo.

Pueden ayudarme !! alguna sugerencia, me arta que pase eso de que se cuelgue.

PD. ni siquiera me ha dejado enviar el post desde ubuntu, se trabo a los 10 minutos, intente 3 veces y la ultima vez ni siquiera me funciono Alt + PrintScreen + REISUB, ya que se queda en las nubes y no quiere bajar de ahi. :(

---

### Post by faktorqm on 2007-12-14
Hola, la verdad, es un problema bastante particular el tuyo. Lo que a mi me parece, aunque no estoy muy seguro, pueden 3 cosas claves (en orden de importancia):

1- la configuracion del bios, revisala de pe a pa, los modos de suspendido, las configuraciones del irq, y de acpi/apic, y etc.

2- Se me ocurre que tambien puede ser algun error en el sistema de archivos de la particion de swap que te cuelga la compu, aunke es menos improbable, es logica o primaria? si podes trata de tener 3 primarias, una con win (no la toques) y la otra ext3 y al final swap. con algun testeador de superficie de disco podes darle a todo el disco a ver si esta por ese lado el problema.

3- Especifica el modelo de tu mother, a ver si se encuentra en google algun bug de ubuntu y que capaz hay algun parche (estilo 915-resolution), o algun manejador de chipset mantenido por la comunidad o algun modulo de algo que capaz te esta colgando la compu.
Creo que lo mejor seria entrar en modo recuperacion (o memtest 86 podes hacer tb) para ver bien lo que esta pasando y activar todos los logs posibles, del kernel, del xorg, y demas variete para ver lo que esta pasando. si no podes ver los logs, [http://www.fs-driver.org](http://www.fs-driver.org) creo que era podes ver particiones ext, ext2 y ext3 bajo windows.

Salu2!!

---

### Post by Moonlit Knight on 2007-12-14
Tengo la misma PC que vos y me pasaba lo mismo, probó desinstalando el paquete powernowd y fijate que pasa, a mi me solucionó el problema.
Buscalo en synaptic

o en consoloa

sudo apt-get remove powernowd

---

### Post by melvinlopez06 on 2007-12-14
faktorqm ya revise la bios asi exaustivamente y todo parece andar bien, instale los drivers para ver ext2 en windows y vi los logs del xorg, los del xgl y no vi nada sobre errores, solo unas advertecia de AIGLX de ahi todo normal.

Los discos duros (gracias al instalador de win) tienen particiones logicas, excepto la de win que es primaria.

Moonlit Knight te cuento que ya removi el paquete que me dijiste, posteriormente reinicie (por sis las diules) y ahorita estoy en ubuntu.

Ya llevo 20 minutos y no hay señales de colgarse, estoy escuchando musica, escribiendo esto, y ya instale uno que otro programa y al parecer todo tranquikis.

Probaré toda la mañana la pc con ubuntu, a ver que pasa, tengo tanto que hacer aqui, a ver como va y posteo resultados al rato.

Siento no poder dar el modelo de mi motherboard puesto que no puedo destaparla para ver, aunque ya que estoy en ubuntu si hay algun comando para saberlo y mostrar el modelo de la madre haganmelo saber.

Buscare al respecto, a ver si encuentro algo.

---

### Post by faktorqm on 2007-12-14
Hola, buenisimo que desinstalando eso te anda. Asi también, me siento en la obligación de comentarte algo, originalmente el powernowd es una tecnologia que te permite regular la frecuencia del microprocesador segun la carga que se le pida, ejemplo: si estas usando el gedit no necesita la misma frecuencia que si estas trabajando con OO, con el amarok, mientras warcraft 3. no se si me expliko bien.
Ahora bien, para que hacen esto es la pregunta, tiene una simple respuesta, y es la duracion del microprocesador. Se calcula que se alarga la vida útil entre un 800% y un 1200% dependiendo del uso.
Si te preguntas que tiene que ver, es por el tema de la temperatura que levanta cuando anda a la maxima frecuencia, si anda al taco y no hace nada, no tiene sentido.

Moonlit Knight: vos podes abrir la compu para ver el modelo? en el bios no dice? tiene ke decir cuando arranca o en la parte de informacion del bios.

Ahora bien, aprovecho el tema para desvirtuarte un poco: en mi compu no anda el powernowd. el error es el siguiente:

```
* Starting powernowd...
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent.
* CPU frequency scaling not supported
[OK]
```

Ahora bien, es verdad que mi micro no soporta frecuency scaling? tengo un AMD Athlon XP 2600+ Barton. o es que la ruta esa con la doble // es un bug y por eso no lo carga? yo mire el archivo S20powernowd pero no encontre ningun error. Si me dicen que no lo tengo en mi micro, josha asi lo saco del inicio, por que como total no se me activa... es lo mismo!!

Gracias y salu2!!

---

### Post by melvinlopez06 on 2007-12-14
hey faktorqm fijate que ya llevo toda la mañana en el ubuntu y ningun problema, todo trankikis y funcionando como se debe, ni señas de cuelgues, todo va de lujo.

Esa tecnologia del powernow ya la habia leido en algun lado, y si es una gran idea para optimizar el rendimiento de los procesadores, y es mas utilizada en las laptops y ayuda un vergo para el ahorro de energia y dura mucho mas la bateria del portatil.

El modelo de mi mother se los debo (hasta que reinicie el ubuntu porque ya no se me trabo jeje) y sino pues le preguntare al de soporte.

Yo veo raras esas dos // en la ruta, al rato y es ese el problema.
Vere como consulto lo de la mother, para tener mas datos y que la mara sepa que hacer cuando se topen con esas motherboards, recuerdo que hay un programa en win que se  llama everest y hace reportes de hardware, en la tarde me zampo a win y veo que ondas.

Posteo al rato, el ubuntu va de lujo

---

### Post by kowal on 2007-12-14
> **faktorqm said:**
> Hola, buenisimo que desinstalando eso te anda. Asi también, me siento en la obligación de comentarte algo, originalmente el powernowd es una tecnologia que te permite regular la frecuencia del microprocesador segun la carga que se le pida, ejemplo: si estas usando el gedit no necesita la misma frecuencia que si estas trabajando con OO, con el amarok, mientras warcraft 3. no se si me expliko bien.
Ahora bien, para que hacen esto es la pregunta, tiene una simple respuesta, y es la duracion del microprocesador. Se calcula que se alarga la vida útil entre un 800% y un 1200% dependiendo del uso.
Si te preguntas que tiene que ver, es por el tema de la temperatura que levanta cuando anda a la maxima frecuencia, si anda al taco y no hace nada, no tiene sentido.

Moonlit Knight: vos podes abrir la compu para ver el modelo? en el bios no dice? tiene ke decir cuando arranca o en la parte de informacion del bios.

Ahora bien, aprovecho el tema para desvirtuarte un poco: en mi compu no anda el powernowd. el error es el siguiente:

```
* Starting powernowd...
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent.
* CPU frequency scaling not supported
[OK]
```

Ahora bien, es verdad que mi micro no soporta frecuency scaling? tengo un AMD Athlon XP 2600+ Barton. o es que la ruta esa con la doble // es un bug y por eso no lo carga? yo mire el archivo S20powernowd pero no encontre ningun error. Si me dicen que no lo tengo en mi micro, josha asi lo saco del inicio, por que como total no se me activa... es lo mismo!!

Gracias y salu2!!

Según tengo entendido se puede si el micro soporta la tecnología PowerNow! o Cool n' Quiet. En mi caso tengo el problema de que el Cool n' Quiet lo tengo habilitado en el BIOS pero el powernowd no me lo toma (curioseando en launchpad parece ser que no soy el único).

Más info sobre powernowd:
[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/44699](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/44699)
[http://gentoo-wiki.com/HOWTO_PowerNow](http://gentoo-wiki.com/HOWTO_PowerNow)

Saludos!

---

### Post by Moonlit Knight on 2007-12-14
Hola otra vez. Te paso al data de mi pc, Tengo un mother Intel D101GGC y el micro es Pentium IV 3.0 Ghz HT.

La PC antes se me colgaba todo el tiempo también, hasta que saqué el powernowd.

Tenía entendido, por la descripción, que el powernowd sirve más que nada para Pentium M, mobile, para las laptops, ahí es dónde se requiere más la regulación de la frecuencia, para un menor consumo de la batería, 

En una Desktop me parece inutil, a menos que se agrave la crisis energética, o para evitar que te cobren la multa los del gobierno por gastar de más. :confused:

---

### Post by rojojuan on 2007-12-16
> **Moonlit Knight said:**
> Hola otra vez. Te paso al data de mi pc, Tengo un mother Intel D101GGC y el micro es Pentium IV 3.0 Ghz HT.

La PC antes se me colgaba todo el tiempo también, hasta que saqué el powernowd.

Tenía entendido, por la descripción, que el powernowd sirve más que nada para Pentium M, mobile, para las laptops, ahí es dónde se requiere más la regulación de la frecuencia, para un menor consumo de la batería, 

En una Desktop me parece inutil, a menos que se agrave la crisis energética, o para evitar que te cobren la multa los del gobierno por gastar de más. :confused:

Este es un tema importantísimo. Gracias desde ya a todos los que aportaron sus experiencias. Soy otro de los que en Gusty sufren continuos cuelgues. Borré ahora powernowd y la máquina parece andar más suave y no tengo ningún problema. 
Será algo que AMD tiene que mejorar?
Voy a seguir averiguando en Internet.
Si alguien puede agregar algo más sobre este tema  para compus de escritorio, agradecido.

---

### Post by faktorqm on 2007-12-17
me parece que no anda en varias distros.

[http://www.usenetlinux.com/archive/topic.php/t-615294.html](http://www.usenetlinux.com/archive/topic.php/t-615294.html)

es un tema con el acpi. parece que va a haber que esperar por un nuevo kernel :S

---

### Post by rojojuan on 2007-12-17
> **faktorqm said:**
> me parece que no anda en varias distros.

[http://www.usenetlinux.com/archive/topic.php/t-615294.html](http://www.usenetlinux.com/archive/topic.php/t-615294.html)

es un tema con el acpi. parece que va a haber que esperar por un nuevo kernel :S

Lástima que al desactivar powernowd la temperatura sube varios grados. Antes andaba alrededor de 38-39 y ahora 43-44.

---

### Post by faktorqm on 2007-12-17
si yo tenia activado el corte de temperatura por bios y lo tuve que sacar desde que uso ubuntu por que calienta re mal :S:S ahora le tuve que poner un cooler duro para mantener el sistema vivo :D y anda josha. salu2!

---

### Post by Mister X on 2007-12-17
> **rojojuan said:**
> Lástima que al desactivar powernowd la temperatura sube varios grados. Antes andaba alrededor de 38-39 y ahora 43-44.

No creo que sea un gran problema esa temperatura, averiguá que rango de trabajo tiene tu CPU.
Como dato, el micro mío aguanta hasta 92º C y la temperatura que tengo normalmente es de entre 40 y 50

---

### Post by rojojuan on 2007-12-17
Problema ninguno, todo bien.
Con estos días de calor anda en los grados que dije; efectivamente el procesador que tengo (AMD X2 3800+) soporta alrededor de 80 y pico, según ví en la página de AMD.
De todas formas, a lo mejor el nuevo kernel soluciona el problema; ví que ya salió, espero hasta que esté disponible en Sinaptic.

---

