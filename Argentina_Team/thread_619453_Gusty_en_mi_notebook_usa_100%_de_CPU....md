---
title: "Gusty en mi notebook usa 100% de CPU..."
date: 2007-11-21
forum: Argentina Team
---

### Post by JorgeGhersa on 2007-11-21
Hola ubunteros, paso por aquí para que me ayuden con mi problemilla:

Tenía Feisty puesto en una notebook y andaba caaaaasi perfecto, pero como tenía también la partición del Win y qué sé yo; para pasar a Gutsy directamente hice un fresh install ( en el interín la evangelicé a mi madre, mostrandole todo el Compiz en su notebook grosa ).

El problema que tengo es que ahora anda lentísimo, y se ve que tiene que ver con cómo usa el procesador: cualquier cosa que le pido, así sea abrir la consola y tirar top, le consume una catralada de cpu; no es que haya algun otro proceso chupando procesador ( salvo xorg, pero no más del 20% ) sino que cuando le pido lo que sea, ese proceso se morfa todo.

Esto ya había empezado durante la instalación, pero asumí que era por correr desde la memoria. Me da la impresión, y lo digo por algún mensaje de error que pispeo cuando arranca, que esto tiene que ver con el escalado de frecuencias que no anda o anda mal; otra opción es relativa al gnome porque al arrancar no tenía gnome-panel, y cada tanto algún errorcito me tira ( por ejemplo, ahora se colgó el intercambiador de usuarios ); otra es con el X, porque al arrancar la pantalla de progreso con el logo de ubuntu está enorme y descentrada...

Mensajes de error durante el cargado:
En "loading hardware drivers" se queda un rato y después sale con "error inserting iwl_wifi_rc80211_simple..."
otro: "cannot create /sys/devices/.../cpufreq/scaling_governor" o algo así ( estoy leyendolo cuando pasa, lo copio de memoria )


Como ven, sé lo suficiente como para pensar posibilidades, pero no tanto como para encontrar soluciones. ¿Funcionaría volver a instalar Feisty de cero y hacer un upgrade desde ahí?

La notebook es una portege 7200Cte con el Docking Station puesto y una placa de red pcmcia MSI ( comprada a propósito porque trae el chipset Realtek que marcha lindo en ubuntu ). 
Acá hay un pdf con toda la data de la máquina, aunque no figura el docking station ( que trae el floppy, la lectora de dvd, puertos usb, y unas cuantas cosas ); en resumen es un p3 con 320 de Ram.
 [http://www.eserviceinfo.com/download.php?fileid=23732](http://www.eserviceinfo.com/download.php?fileid=23732)

No sé qué salidas de qué comandos postear, ni cómo buscarlas, pero uds. digan y yo mando.

La verdad, un bajón: yo quería ver de qué se trataban las mejoras de consumo de batería en 7.10, y otros chichecitos nuevos, y me comí este yunque en la cabeza...

---

### Post by Hei Ku on 2007-11-21
Como dijiste lo del escalado de frecuencias, te fijaste a que frecuencia funciona el CPU?
Yo lo veo con un applet de karamba, pero supongo que conky tambien lo debe tener.

Fijate en el bios que dice sobre ese tema, y fijate en los foros que hay bastante sobre frequency scaling.

---

### Post by JorgeGhersa on 2007-11-21
El Bios tiene un setting cuyas opciones son "Always low", "always high" y "dynamically switchable" que es la seleccionada.

Cuando pongo el monitor de frecuencia de la cpu del panel de gnome ( era más rápido que bajarme el conky, con esta máquina super lentificada ) sale un aviso que dice "No podrá modificar la frecuencia de su máquina. Su máquina puede estar mal configurada o no tener soporte hardware para el escalado de frecuencia de la CPU.", y el applet dice "Sin soporte para el escalado de frecuencia - 336mhz (100%)".

Ahora, seguí tu ( no por repetido menos sabio ) consejo y googleé: [este muchacho]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/") me da la pista de buscar en el contenido de /sys/devices/system/cpu/cpu0/, donde debiera haber una carpeta cpufreq y un contenido de ella, y no lo hay ( esto debe querer decir que no se pudo instalar el escalado y por eso no se crearon, ¿no?)

( También había algo que sonaba como lo mío en launchpad, pero "Launchpad is offline for scheduled maintenance." Buu... ).

( Mientras tanto, el panel de gnome siguió haciendo cosas locas: se clavó el iconito de la red en el dibujito ese que da vueltas, congelado, a pesar de que ya estaba conectado a la red de casa ).

(...)

Después para comprobar que se trata de esto y no de cualquier otra cosa, cambié el setting del bios a "always low" para ver qué onda. Tardó milenios en cargar todo, volvió a aparecer el cartel de "no podrá", se volvió a colgar el cambiador de usuarios, y el monitor de frecuencia ahora dice "497mhz (100%)" ( ??? ). Y haciendo lo mismo con Always High, sigue tardando eones, pasó por una forma vieja de Gnome ( el ícono de la ayuda era el salvavidas ) y después mutó en el común, me volvió a rebotar el cambiador de usuarios, y ahora la frecuencia es 501mhz.

(...)

De todos modos, cambié de hipótesis predilecta: eso de que salga el logo de ubuntu y la barra naranja descentrados, y que al principio no me anduviera el gnome-panel, me hace olisquear una mala configuración del X - porque me acuerdo que en este foro, no sé en qué thread, a alguien le pasó lo mismo con los paneles y le dijeron que era un tema de cómo estaba configurado el Xorg... Igual, con mi ignorancia, es como ir al médico y decirle "creo que tengo una infección de tal cosa"; mejor que lo determine el que conoce más los síntomas...

En fin, GRACIAS Hei Ku y los que se vengan de acá en más para ayudarme con esto...

---

### Post by margori on 2007-11-21
Estimado Jorge:

Busque tu notebook por la red y encontre estas especificaciones, entre otras: Intel P3 600MHz RAm 64MB max 128MB.

Los requerimientos minimos de hard estan en [ubuntu features]("http://www.ubuntu.com/products/whatisubuntu/desktop/features") y dice que necesitas como minimo 256MB.

No es por ser mala persona, pero no creo que le puedas sacar mucho a tu notebook con Ubuntu. Quizas tengas que optar por algo mas liviano, como Xubuntu.

---

### Post by JorgeGhersa on 2007-11-21
Gracias por la intención, margori, pero debés haber encontrado mal las specs porque es expandible hasta 320, que es lo que tiene puesto; si te fijás en el pdf que dejé linkeado ( en realidad es un link a un sitio donde lo bajás, porque no encontré una url directa ) dice bien. Capaz te saltó la 7020, que es el modelo casi casi igual pero es un toque más modesto...

( Si fuera así, tampoco hubiera podido tener Feisty, que aparte andaba lindo y hasta me dejaba jugar con el Blender y el Inkscape, aunque sea un poco )


Agrego un dato: comparo mi máquina fija ( desde la que escribo ) que tiene Feisty y cuando no está haciendo nada dice que el cpu está usando 0 mientras que la notebook sin nada andando más que el gnome pelado me dice que está usando 27%.

Los escucho, oh oráculos... ;)

---

### Post by Hei Ku on 2007-11-22
Saquemonos la duda. La probaste en "Always high"? Si asi te anda, seguimos buscando por el lado de la frecuencia, si no, encaramos por otra cosa.

---

### Post by JorgeGhersa on 2007-11-22
Sí, ahí arriba lo puse, capaz se pasó porque lo agregué en una edición .

> 
Y haciendo lo mismo con Always High, sigue tardando eones, pasó por una forma vieja de Gnome ( el ícono de la ayuda era el salvavidas ) y después mutó en el común, me volvió a rebotar el cambiador de usuarios, y ahora la frecuencia es 501mhz.

¿O sea que es otra cosa?

---

### Post by Hei Ku on 2007-11-22
Te fijaste en los logs de kernel /var/logs/kernel.log para ver si hay dice algo mas?

Tambien fijate esta thread sobre frequency scaling, no creo que sea eso, pero estaria bueno sacar del medio los errores que te aparecen en el boot.

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

Una pregunta, que pasa si usas el LiveCD de Gutsy? Lo mismo?

---

### Post by JorgeGhersa on 2007-11-23
Voy respondiendo por partes:

Tema Log: muy hardcore para mí, no entiendo casi nada y no sé bien qué buscar... Ni siquiera sé qué sección podría postear ( porque no da poner tooooodo ) para que otro la entienda... Lo que sí, noté un par de cosas, uds. dirán si son relevantes:
1- Si busco ( ctrl-F ) palabras como scaling, cpufreq, o frequency y no sale nada.
2- Encontré sí que lo primero que me registra en cada booteo es:
> Nov 21 03:00:05 ElMorralDeHermes kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov 21 03:00:08 ElMorralDeHermes kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov 21 03:00:08 ElMorralDeHermes kernel: Symbols match kernel version 2.6.22.
Nov 21 03:00:08 ElMorralDeHermes kernel: No module symbols loaded - kernel modules not enabled. 
¿Algo que ver ahí?


Tema HowTo:
En el paso de "sudo modprobe acpi-cpufreq" me sale "Error inserting acpi-cpufreq (/.../.../acpi-cpufreq.ko ): No such device." Pero parece que les pasa a varios, según el resto del tema del how to... ( De nuevo: mucho no termino de entender lo que se hace en ese howto ).

Tema Gutsy Live:
Cosas superficiales que quizás importen: el logo al cargar está centrado ( en la versión del disco duro, repito, aparece grandote y más a la derecha-abajo ), lo del wifi vuelve a pasar ( ver primer post ), y vuelve a no tener las barras del gnome ( aunque esta vez amenazó en un flashazo de tenerlas; "solución" mía, leída por ahí, hacer un lanzador con xterm, luego reiniciar el gnome-panel; ahí se cierra al cerrar la consola pero después vuelve ). 
En cuanto a la frecuencia, vuelve a saltar ese error durante el booteo ("cannot create..." ), pero esta vez le añade un "frequency scaling not supported" abajo, como para que quede clarito; y ya con el gnome andando el monitor de frecuencias tira "freq. s. unsuported - 500mhz", el monitor del sistema muestra también bastante uso... si bien no puedo saber si esto no es por correr desde el live, sí, pareciera estar igualmente lerda.
...

Acabo de reencontrarme con mi CD de Feisty. Yo sigo con la hipótesis de que más allá del escalado, el tema puede pasar por el X y cómo en Gutsy no termina de cerrarle el tipo de pantalla que tengo; así que lo que voy a hacer, basado en puras suposiciones, es hacer un instalado a cero de Feisty, actualizar, y upgradear a Gutsy desde ahí. Sea por eso o no, con suerte, la "buena" configuración que me daba F se puede trasladar a través del upgrade, y me quedo con lo mejor de ambos mundos... ( aunque sin nunca saber a ciencia cierta qué pasaba... )

Hago eso y les cuento. De nuevo, gracias...

---

### Post by JorgeGhersa on 2007-11-23
Y no, no funcionó.

Los errores durante el booteo son los mismos, el gnome vuelve a pasar por iconitos viejos y tarda en cargar, y en el reinicio después de la actualización tiró un 300 y algo, y en la segunda vez 646mhz; y en general sigue inmanejable...

¿Sugerencias?

---

### Post by Hei Ku on 2007-11-23
Revisar los errores en los logs de kernel y messages, para ver si encontras algo que parezca significativo.

Por otro lado, tenes que usar la maquina. Yo te recomendaria quedarte por el momento en 7.04 y postear un bug en launchpad, a ver si te pueden ayudar.

---

