---
title: "¡Se me cuelga el xorg y vengo con cara de perro apaleado!"
date: 2007-01-04
forum: Argentina Team
---

### Post by clasificado on 2007-01-04
**Buenas a todos, me les presento: clasificado. Es un gusto verlos a todos aqui presente.** Terminado el protocolo, ahora los dos temas que quiero tratar.

**El primero: Vengo a pedir ayuda**, Perdonen el pecado de comenzar así, pero vieron como dice el dicho - Hoy por mi, mañana por ti.  Siempre lo dije yo y nunca me permití escuchar a nadie más decir este refrán (me tapo los oidos con las manos, y canto fuerte "¡lalalalalala!")

**Ahora si, con su permiso, Segundo:**

¡Se me cuelga el Xorg sin ninguna razon aparente! 

¿Pero para que vengo acá? ...Sabiduria, hermano...

*Osea, no quiero reinstalar. me gustaria entender porqué se rompió. Aunque eso me lleve a estudiar fisica nuclear, entender que nada tiene sentido y llegar a la conclusion dos años despues de que hay que reinstalar (aunque mas no sea el Xorg)*

Las cosas se pueden arreglar de muchas formas, y siempre estan las basicas y mas obvias, y le siguen algunas que tambien son básicas, pero solamente una mano experimentada te las puede advertir. **Quisiera que me compartan sus puntos de vista.** Al fin y al cabo lo voy a terminar arreglando yo y no ustedes porque es mi computadora y no la de ustedes

Soy nuevo en Linux, y es el primer problema crítico con Kubuntu que tengo, y es la primera vez que tengo la ESPERANZA de que algo se puede arreglar METIENDO MANO COMO CIRUJANO, y no dandole con el desfibrilador cual doctorucho con miedito de tocar al paciente.

**Empecemos - Que tenemos.**

Procesador: Pentium 3 933mhz
Ram: 384mb
Mother: Nomeacuerdoymedafiacafijarmeenlaplaca
Video: [Geforce 2 gts pro] con driver propietario [nvidia nosecual]

**Sigamos - Que es lo que pasa.**

"Era un dia soleado y el enfermito estaba encerrado en su Kubuntu navegando con el Firefox (o viendo un disco de computadora ajena con el Konqueror a través de Samba, o el ultimo fue eligiendo avatar con el Kopete), y derrepete el mundo se detiene,  como si viniera la Muerte misma y tocara con su dedo maldito la PC."

La impresion de "el mundo se detiene" se enumeraria así:
1) La pantalla se Congela (por ej: si el firefox está mostrando un gif animado, éste se detiene)
2) El teclado deja de responder (el capslock no responde, el numpad si, ctrl+alt+backspace no hace nada, ctrl+alt+Floquesea tampoco me cambia de consola)
3) Me quiero matar

**Veamos la luz al final del tunel - ¿Que se quiere?**

Éste es mas simple decir que hacer: Quiero Mirar el Bug. no verlo, MIRARLO. Quiero ver cada una de sus patitas peludas, quisiera ver ese cuerpo regordete pero reventado entre dos engranajes  de mi Xorg, clavando todo el sistema. Lo tomo con una pinza ("Acá estás, infeliz") y lo saco para siempre.

*Osea, no quiero reinstalar. me gustaria entender porqué se rompió. Aunque eso me lleve a estudiar fisica nuclear, entender que nada tiene sentido y llegar a la conclusion dos años despues de que hay que reinstalar (aunque mas no sea el Xorg)*

**Saliendo del tunel hacia lo desconocido - ¿Que hago para arreglarlo?**

1) Lo primero que hice fue resetear. Cuando me cansé de que se cuelgue y de andar reseteando empezé a buscar alternativas.

2) El numlock y un ping me dieron a entender que el sistema ESTABA VIVO, EMIPLÉGICO PERO VIVO

3) Un server de SSH en el kubuntu y un cliente (putty) en otra pc (mientras está colgado) corriendo un top me mostraron la realidad: el proceso del Xorg se fue al 100. ¡Solo el Xorg, y no todo el sistema! ¡¡¡SOLO EL XORG!!!!. y que se le va a hacer, no solo al explorer.exe le pasa, parece.

No pude darle un killall, pero un [sudo reboot] desde ahi me pareció mejor que andar dandole al reset.

4) Empiezé a revisar el /var/log/Xorg.0.log, aunque todavia no encontré nada que me sirva

**Y ya.** ¿Que más podrían aportar para ayudarme a continuar con este calvario?

[SIZE="4"][COLOR="Blue"]Y desde ya: ¡Muchas Gracias![/COLOR][/SIZE]

Clasificado.

---

### Post by Nemesis Teufel on 2007-01-04
JAJA, terrible lírica tenes para describir tus problemas..
Hay que ser un libro de poesía de ubuntu (?)


Yo soy mas bruto que vos, aclaro pero quizá sea lo mas obvio.. (que es lo mas inesperado)
Te pasa solo con ubuntu que se te cuelga? quizá sea un problema de hard que no ventila, ademas coincide con el día de calor.. 

Podrías darte cuenta de esta forma si no:
Se te cuelga siempre al mismo tiempo? tarda menos cuando hace calor?
Cuando reinicias lo hace mas pronto esto de colgarse?

---

### Post by felipelerena on 2007-01-05
cosas que haria yo:
1) mirar la temperatura del micro
2) cambiar la placa de video y probar.
3) probar la misma instalacion de ubuntu en otra maquina

---

### Post by beuno on 2007-01-05
Busca en:

/var/log/dmesg
/var/log/kern.log
/var/log/syslog

---

### Post by kowal on 2007-01-05
El driver nvidia es beta? Cómo lo instalaste? Tenés Beryl, XGL o algo así instalado?

---

### Post by clasificado on 2007-01-05
¡Gracias a todos por las respuestas!

**problemas de temperatura**
Ksensors fue el elegido, y dio un 40 para el cpu, 49 para el mother y 40 para el hdd. Creo que está dentro de los limites.

Aun así, hasta donde tengo vivido yo (Windows), cuando se cuelga por temperatura, se cuelga TODA LA MACHINE, y no solo el xorg como en mi caso.

**Cuestiones con la placa de video**
El driver resultó ser un nvidia 1.0-7184, instalado através de un automatix
Cambiar la placa de video no podrá ser (no tengo otra)
Ni bien se instaló este kubuntu edgy, tuve la idea de instalar un xgl, pero al fallar toda la cosa, lo desinstalé y quedó ahi.

**Cuestiones de Logs**
¡¡¡Que demonios!!! Apenas si estoy entendiendo de que corno guarda cada uno.
De cualquier manera, en el siguiente cuelgue. ¡los copio! y despues veo que me dicen.

**@felipelerena**: "probar la misma instalacion de ubuntu en otra maquina"
¿Y como haria eso?, digo. ¿Copio y pego todo el rigido? Este es un kubuntu en muy malas manos. No hay dos segundos iguales para esta PC. aún si me consiguiera otra pc, dudo que tenga el mismo hardware como para aguantar meterle el rigido, nosé. no entendí

[COLOR="Blue"][SIZE="3"]¡Es un paso grande para el hombre! ¡Gracias a todos![/SIZE][/COLOR]

Clasificado.

---

### Post by jpmorelli on 2007-01-06
Buenas clasificado ! Te comento que yo tuve un problema similar al tuyo y pensaba como puede ser que Linux con lo estable que es se quede congelado ??? 
Grata y no tanto fue mi sorpresa cuando me di cuenta que no era el sistema el congelado... lo que dejaba de responder era mi teclado y mi mouse, ambos inalambricos y de Microsol
La base se conecta via USB al CPU, mas específico, es el modelo Wireless Multimedia 1.1 ( teclado y Mouse ), entonces desconectaba y conectaba el USB y seguía usando mi querido Ubuntu.
Aclaro que esto me pasaba en Dapper y luego de alguna actualizacion automatica dejo de pasar ( no se cual porque a veces no pasaba ), con Edgy nunca mas, gracias al cielo.
Bueno fijate porque tal vez sea eso :)
Suerte.

---

### Post by MeduZa on 2007-01-06
> **clasificado said:**
> me tapo los oidos con las manos, y canto fuerte "¡lalalalalala!")


todos los dias se aprende algo nuevo y muy util :p 

no creo q sea el Xorg lo que se te quede colgado pero puede ser algo que este mal configurado, pega el /ect/X11/xorg.conf aca asi lo revisamos un poco

suerte, excelente manera de pedir ayuda :)

---

### Post by clasificado on 2007-01-07
¡Buenas de nuevo!

**@jmorelli, por su teoría sobre periféricos:** Yo soy un pibe que se considera optimista pero prudente. no creo que la novedad, el progreso y la evolución sean la misma cosa. Eso me lleva a resistir en la trinchera de los dispositivos ps2.

Pero me siento obligado a decir que tu teoría tiene un punto flojo. Me pongo a mi mismo como testigo, y estando yo como narrador para confirmar lo que el testigo dice, se convierte ésta en una prueba irrefutable:

[QUOTE=clasificado]1) La pantalla se Congela (por ej: si el firefox está mostrando un gif animado, éste se detiene)[/QUOTE]

Si el problema fuera solo de dispositivos de interfaz humana (como le llamaban en Windows), ni el Firefox con su gif animado ni los sensores de medición de memoria y cpu que llevo en la barra de tareas debería detenerse. Y lo hacen. se congelan.

Pero como decia [El Principito]("http://www.franciscorobles.com.ar/libros/principito/"): "Nunca se sabe". Asi que la proxima vez voy a probar desenchufando y volviendo a enchufar. Con probar no pierdo nada. [COLOR="Blue"]Gracias![/COLOR]

**@MeduZa, por su problemita de excepticismo: ** Todo bien con vos MeduZa, pero lo que vos creas o dejes de creer a mi Xorg parece no importarle (aunque tengo que admitir que las 10 horas que hay entre lo que respondiste y lo que estoy escribiendo, vienen sin cuelgue de Xorg - ¡Segui creyendo por favor!). ¿Que te hace pensar que mi Xorg no se cuelga?

Me gustaría remarcar un concepto particular. Colgarse, ¿que significa?:
"Dicese del programa o seccion del programa que no muestra señales de estar haciendo algo útil por el sistema que lo acompaña, y no escucha debidamente (o en absoluto) a las instrucciones que un usuario pueda querer asignarle a través de cualquier método que disponga" (según yo).

Siempre dentro de la subjetividad que cada usuario le transmite al asunto de "no muestra señales", "no escucha debidamente", y "algo útil", ya que el ser humano tiene la naturaleza de no ver, no decir, ni saber que es lo que debe hacerse, cuando más le conviene por supuesto.

Amparandome en estos conceptos teóricos claramente explicados y cientificamente comprobados, puedo declarar "con carpa" que mi Xorg se cuelga, 

ya que: no actualiza video; no quiere cerrarse ni reiniciarse (ni morirse: un [sudo killall xorg] fue completamente ineficiente - esto disparó en mi mente una escena de los caballeros del zodiaco); y cuando accedo por otra computadora por ssh y le pido a [top que me muestre que está pasando]("http://www.die.net/doc/linux/man/man1/top.1.html"), ¡el Xorg tiene la CARADUREZ de mostrar un uso del procesador de 100%! como diciendo "¡Estoy haciendo algo re importante! Es tan importante que no vale la pena hacer caso a nada mas en el universo conocido, ¡ni siquiera hacer eso para lo cual fui diseñado!"

Definitivamente creo que se le zafó un tornillo. no se cual, pero creo firmemente que hay uno ahí flojo (en el Xorg).

Peeeeeeero nada de eso quiere decir que compartir mi xorg.conf no me pueda ayudar a resolver este misterio aunque sea en parte, ¡asique ahi está a disposicion de todos ustedes! [COLOR="Blue"]Gracias![/COLOR]

Y así. [COLOR="Blue"][SIZE="3"]¡Gracias de nuevo por la buena onda (al menos)![/SIZE][/COLOR]

---

### Post by kowal on 2007-01-07
Bueno, voy a intentar dar algunas opciones como para ir descartando que puede ser.. (aclaro que es Domingo.. 7:59 y recién vengo de un boliche.. asi que no me pidan mucha coherencia.. :KS)

1) Yo te diría que primero vayas probando cambiar algunas opciones en el xorg.conf.. por ejemplo poner una almohadilla o numeral (este simbolito #) al principio de la línea que dice  ```
option "AllowGLXWithComposite" "true"
``` o donde dice ```
option "RenderAccel" "true"
``` que se pudieron haber agregado cuando quedó instalado XGL a medias.

2) La versión del driver de nvidia de los repos (restricted) va por 1.0.8774. 
No me fio mucho de Automatix ni EasyUbuntu (en mi experiencia son un poco "sucios" para instalar las cosas.. prefiero usar los repositorios).
Podrías probar desinstalar los drivers (sudo aptitude purge nvidia-glx) y volverlos a instalar.. tal como dice en [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

3) Otra opción puede ser reconfigurar xorg.conf con el comando "sudo dpkg-reconfigure xserver-xorg" (esto te crea automáticamente un backup del viejo xorg.conf por las dudas)

Saludos y espero sirva (al menos para descartar posibilidades).

---

### Post by tseliot on 2007-01-07
Sigue usando el driver 71xx que es lo que tu tarjeta necesita.

Puedes intentar cambiando tu /etc/X11/xorg.conf como aconsejo en el punto 4 de la Problems Section de mi guía:
[http://albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION](http://albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION)

es en inglés pero creo que se entiende.

---

### Post by MeduZa on 2007-01-07
no entendi un sorete lo que dijiste pero sono lindo jajajjajajja
Dije que no creo que sea el XORG por la simple razon que a mi no me pasa eso, por eso digo q puede ser configuracion ya que segun decis hardware no parece ser, la idea de q postearas el conf funciono asi que me diste bola y eso es lo que importa, 

1) borra o comenta (#)  esto:

> 

  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"

Section "InputDevice"
  
  # /dev/input/event
  # for USB
  Identifier "stylus"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  
  # /dev/input/event
  # for USB
  Identifier "eraser"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  
  # /dev/input/event
  # for USB
  Identifier "cursor"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

De paso si haces eso te va a empezar a andar cualquier vercion de adobe photoshop que uses en wine (si no lo haces no te anda)

2) kowal se me adelanto, proba eso q dice el (eso que remarco el desactiva cosas que pueden tener problemas en el driver que estas usando).

3) esto no se que es:
>   load "v4l"
pero en el mio no esta

4) esto menos:

>   option "XkbOptions" "lv3:ralt_switch"

el 3 y 4 ni idea pero en el mio no estan, asi que se lo dejo a otro que sepa q es eso.

proba eso y nos decis

saludos

---

### Post by jpmorelli on 2007-01-07
> **clasificado said:**
> ¡Buenas de nuevo!

**@jmorelli, por su teoría sobre periféricos:** Yo soy un pibe que se considera optimista pero prudente. no creo que la novedad, el progreso y la evolución sean la misma cosa. Eso me lleva a resistir en la trinchera de los dispositivos ps2.

Pero me siento obligado a decir que tu teoría tiene un punto flojo. Me pongo a mi mismo como testigo, y estando yo como narrador para confirmar lo que el testigo dice, se convierte ésta en una prueba irrefutable:



Si el problema fuera solo de dispositivos de interfaz humana (como le llamaban en Windows), ni el Firefox con su gif animado ni los sensores de medición de memoria y cpu que llevo en la barra de tareas debería detenerse. Y lo hacen. se congelan.



Caramba ! Por esta aclaración y aunque el post sea tuyo veo que podrías ser un muy buen detective ! A mi se me pasó por leer sin prestar atención. Mi teoría queda descartada entonces. :-k

---

### Post by clasificado on 2007-01-09
¡Saludos a Todos!

El sol ha vuelto a dar luz por mi ventana, y con ella: Se colgó mi Xorg.

Son casi las siete de la matina, El cuelgue se produjo rondando las 6 al configurar el [cliente NX]("http://www.nomachine.com/download-package.php?Prod_Id=27") para probarlo sobre mi misma pc.

Ahora solo pienso en ir a dormir. Así que me limito a subir los logs y una que otra pavada para tenerlo apilado en algún lugar. 

Empecé una investigación sobre el tema, pero que el sueño venció:

1) [Esta persona]("http://llistes.bulma.net/pipermail/bulmailing/Week-of-Mon-20061030/079062.html") tuvo un problema similar, y lo resolvió. 

Segun dice 
[QUOTE=Manuel Martínez]Era problema del kernel - o eso creo yo -. Habia conflicto 
entre los modulos rivafb y nvidia. El caso es que no se porque empezo 
ahora a dar el error, ya que llevaba con ese kernel un año casi.[/QUOTE]

¿Y no tendré yo el mismo problema? Revisando los módulos del kernel, creo que PUEDE SER
```
teclado@negra:~$ modprobe --list | grep -i nvidia
/lib/modules/2.6.17-10-386/volatile/nvidia.ko
/lib/modules/2.6.17-10-386/volatile/nvidia_legacy.ko
/lib/modules/2.6.17-10-386/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.17-10-386/kernel/drivers/char/agp/nvidia-agp.ko

teclado@negra:~$ modprobe --list | grep -i rivafb
/lib/modules/2.6.17-10-386/kernel/drivers/video/riva/rivafb.ko

```

2) [Esta otra persona]("http://ubuntuforums.org/archive/index.php/t-77277.html") Habla de conflictos de los kernels de dos versiones distintas del driver nvidia.

Puede afectarme si se hubieran actualizado los drivers por apt-update y yo no me di cuenta.

Pero ya a esta altura, no me da la cabeza. Será para dentro de unos cuantos pares de horas.

Sobre sus opiniones, señores kowal, tseliot y MeduZa, Me van a servir para desentrañar el asunto ya que **cada vez que abro el cliente nx, se va el Xorg a ver las nubes. Y eso es un buen lugar para comenzar las pruebas.** Aunque me quedo sin cliente nx hasta que termine el asunto

---

### Post by BlackHero on 2007-01-11
hola clasificado un gusto conocerte anduve desaparecido un tiempo del foro pero bue paso a comentarte tenes muy buena lirica escucha para mi pero solo para mi primero que nada mencionaste ya haber vivido o experimentado problemas de cuelgues con windows que quiere decir eso que estabas hasta las manos de virus o adas o mala configuracion del sistema o problemas de crasheo con algunas aplicaciones del sistema base bue pero tambien el 50  porciento de eso es hard la cosa viene asi si vos tuviste esos problemas lo mas factible es que sea el hard el problema colgarse para la pc no necesariamente obliga que sea problemas de temperatura los cuelgues por lo general suelen ser por cortos en la memoria ram y cortos en la memoria video siii crasheaaan como las mejores bue suponiendo que sea un corto ya sabes que podes hacer, por otro lado vos meniconaste tener una placa de video gforce 2 y con las caracteristicas del micro que no quiere decir pero si para los que saben en que epoca se vendia tal micro y tal mother podria ser una placa onboard una gforce 2 onboard que te consume memoria ram verdad hasta ahi vamos bien, calculo por otro lado que el problema podria llegar a ser no la placa de video sino un problema de instalacion no por que instalaste mal sabemos que esto es automatico pero podria ser que que como mencionaste automatix seguramente dio un error al instalar lo que instalaste bueno mencionando algo mas si estoy en lo correcto tu placa de video no tiene menos de 32 mb ram ni mas de 64 mb ram que quiere decir que mas alla de los mb ram es un sistema dentro de todo pesado para tu pc tenes una pc estandar sin quitarle merito para nada pero es pesado volviendo al punto creo que si tu placa de video es onboard "memoria compartida con el sistema" tendrias problemas con los drivers creo que los drivers para placa de video linux no se llevan bien con las placas onboard por ser las mas baratas me pasa eso. 

POSIBLE SOLUCION:

                           1)   reconfigura los drivers "sudo dpkg-reconfigure xserver-xorg" como dijo kowal.

                           2)   bajate los drivers privativos de la pagina oficial e instalalos fijate lee si andan bien para el sistema que tenes si se te complica usa los del synaptic o add/remove ya que mencionaste ser nuevo en esto de GNU/linux.

                           3)   si despues de hacer todo eso la maquina sigue andando mal desarmala deja que se descargue la estatica, limpiala y chekea la bios si podes bajarle los recursos a alguna cosas mejor para obtener un mejor rendimiento.

                           4)  si el problema perciste empiesa a provar piesas nuevas saber (detectar el problema no quiere decir que lo puedas arreglar)

        Saludos 

P/D: no estoy acostumbrado a escrivir tanto :P

---

### Post by sympozium on 2007-06-07
Tengo tu mismo problema pero con un video geforce 6150 (integrado), avanzaste en algo??

---

### Post by clasificado on 2007-06-09
@sympozium: Lamentablemente no :P

Probé todo lo que me recomendó el team de uluga a traves de este thread, sin resultado.

En algún momento de edgy, una actualización terminó de reventar los drivers nvidia, y dejó de encender el Xorg con las versiones privativas.

Desde ese momento, estoy con la version Open Source "nv", que como la uso para laburar y no uso el 3D, resigné Beryl y me quedó una PC funcionando joya.

Ya mi kubuntu se me está llendo de las manos, asi que es probable que vuelva a empezar, y ahi voy a retomar este tema

Clasificado.

---

### Post by undiaperfecto on 2007-06-09
con el nuevo kernel no molesta mas, al menos llevo 1 dia trabajando a mas no poder, y nada, dejo de colgarse el xorg.

---

### Post by clasificado on 2007-06-27
¡Y me acordé que alguna vez habia abierto esto che!

¿Sabian que lo arreglé? Para los que no se acuerdan (todos :P), a mi se me colgaba el Xorg y me dejaba de responder todo menos el mouse (que se movía, pero no hacia nada mas). Yo tuve la suerte de encontrar como repetirlo, entonces me fue "facil" arreglarlo: Encendia el calc, y se colgaba. Para apagarla o resetearla, me conectaba por ssh desde otra (y responde, lo que se cuelga es el xorg), le doy sudo reboot y a otra cosa.

Puse esto en el xorg.conf
```

    DefaultDepth    24
    Option         "RenderAccel" "false"
    Option         "AllowGLXWithComposite" "false"
    Option         "NvAgp" "0"

```

Ahora, yo no entiendo como es que beryl funciona despues de haberle deshabilitado todo eso :D. Tengo Direct Rendering y toda la pelota.

Es que leyendo y leyendo, encontré que el driver nvidia-glx-legacy esta hecho pelota, y anda la mitad de las veces (yo estoy en la mitad que no funciona). Asi que le fui poniendo NO a todo, hasta que anduvo!

En cuanto llegue a alguna configuracion que funcione (y tenga habilitado ALGO), la posteo asi cierro con broche este tema

Clasificado

---

