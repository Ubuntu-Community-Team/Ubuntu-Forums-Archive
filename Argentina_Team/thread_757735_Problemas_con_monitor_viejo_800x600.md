---
title: "Problemas con monitor viejo 800x600"
date: 2008-04-17
forum: Argentina Team
---

### Post by ignacioml on 2008-04-17
Hola gente:

No quería empezar un nuevo thread, pero estuve buscando en el foro y leyendo y no pude encontrar alguien con mis problemas.

El tema es que me compré una compu en Jarbarino. La más baratita que había. Ya venía con un Linux instalado. Una distro argentina que se llama RxArt y que también es de la familia Debian. En este momento la máquina está andando con esa distro que tiene KDE.

Por varias razones (la principal, por la comunidad de usuarios que se ayuda mutuamente), decidí pasarme a Ubuntu. Estuve viendo como era el tema. Y empecé instalándomelo en mi casa junto con Vindous XP. Hasta acá todo bien.

El problema es que ahora lo quiero instalar en la máquina esa que tiene la otra distro. La quiero reemplazar por Ubuntu. Como dije, la máquina es nueva y hoy día le anda todo. Pero resulta que no me alcanzó la guita para comprarme un monitor. Así que la estoy usando con un Samsung SyncMaster 3 que tira hasta 800x600.

La cuestión es que pongo el CD, elijo el idioma y me mando a instalar sin tocar nada. La instalación comienza, sale la barrita naranja y cuando termina de llenarse me pone los siguientes mensajes:
```
*Starting deferred execution scheduler atd     [Ok]
*Starting periodic command scheduler crond     [Ok]
*Checking battery state                        [OK]
*Running local boot scripts (/etc/rc.local)    [Ok]
```

esto se queda parpadeando un cacho y sale otra pantalla que dice que no puede arrancar bla bla bla.

Voy de nuevo. Arranca el cd, elijo el idioma y también elijo VGA 800x600 16 es que lo máximo que da este aparato. Arranca la instalación, la barrita naranja, y cuando termina, ahora la pantalla se pone negra. Parece que va a aparecer un cursor en el medio... pero no! Se pone a parpadear un ratito y otra vez la pantalla que dice que no pudo arrancar bla bla bla.

La cuestión es que el problema está en el monitor, porque con este mismo monitor me pasaba lo mismo en la máquina en la que sí lo pude instalar sin problemas. La gran solución fue un monitor también Samsung pero más nuevo de 17". Pero bué, eso era en mi casa. 

Ahora estoy emperrado que quiero que la máquina ande con ese monitor pedorro pero no le encuentro la vuelta. Estuve buscando y no encuentro gran cosa.

Acá no tengo las especificaciones de la máquina pero si mal no me acuerdo tiene un procesador Intel dual y 1 Giga de RAM. Sonido, video y demás on board. Y los CDs con los que estoy probando instalar estan chequeados (tengo 2).

Desde ya, 'chas gracia'

nacho
[SIZE="1"]Otro picapiedra[/SIZE]

---

### Post by faktorqm on 2008-04-17
Hola, existe un instalador que es en modo texto justamente para estos casos. Aparece en el foro pero quiza por otros motivos, ese cd sirve para casos donde simplemente el instalador grafico no anda, y eso puede ser por muuuuuuuchas razones.

El cd se llama "alternate" y lo bajas de ubuntu.com digamos, solo que tenes que decirle que queres este y no el """normal""". No te asustes, el Alternate CD es lo mismo, solo que es mas parecido al instalador de Debian que otra cosa. 

En esta página [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) EXACTAMENTE abajo del boton del dowload, dice "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer." o lo que es lo mismo "Clickee acá si usted necesita el CD alternativo de escritorio. Este CD no incluye el live CD, en su lugar hay un instalador basado en texto".

Espero que te haya servido. Salu2!!

---

### Post by ignacioml on 2008-04-17
Hola pincharrata:

Ya te había visto por acá. Yo también soy platense... aunque no soy pincha, ni del otro tampoco =)

Gracias, che. Ya me pongo a bajar ese CD. La verdad ya había visto que existía, pero con ese nombre se me ocurría que sería algo para espertos :D

Ah, y ya que estamos... alguna sugerencia para pisar el linux preexistente? Uso las particiones que tenga? O particiono todo de nuevo?

nacho

---

### Post by faktorqm on 2008-04-18
Hola, no ninguna, simplemente formatealas y listo. Te recomiendo que leas mi post donde pongo un video y un pdf de instalacion de ubuntu, asi la haces "bien". Acordate de dejar en total para linux 3 particiones, una de sistema (montada como /), otra de datos (montada como /home) y el swap. si tenes dudas pregunta. Salu2!

---

### Post by ignacioml on 2008-05-05
Acá estoy de nuevo.

Bueno, le hice caso al picharrata y me bajé el alternate CD. Estuve chusmeando por ahi cómo se hacía y me mandé. Reparticioné el disco porque las particiones anteriores tenían unos tamaños extraños. Y en principio tuve dos problemas y después un tercero y un cuarto.

1. Durante la instalación, a diferencia de lo que me pasó durante la instalación gráfica, nunca se me pidió un nombre de usuario y contraseña. Ergo, cuando arrancó el sistema se me llenó el tugen de preguntas cuando para entrar tenía que contar con usuario y contraseña. A grandes problemas, grandes soluciones... durante el arranque apreté Esc y entré en modo texto siendo root sin poner ningún password! y bué, no me quedó otra que apelar a mis pobres nociones unixescas/linuxescas y por medio del comando adduser me creé un usuario y una contraseña. Listo el pollo!

2. Durante la instalación, llegué a una instancia en la que me preguntaban si no quería evitar que el sistema funcione con ciertas resoluciones de pantalla. Sí, justo lo que yo quería! Las taché todas excepto las 640x480 y 800x600. Genial! Pero resulta que cuando el sistema arrancó y me pedía un usuario, lo hizo en 1280xandá a saber cuánto y a qué tasa de refresco. Decí que por más que veía doble alcanzaba a distinguir algo. Entonces cuando entré con mi usuario me metí en el menú fuí a resolución de pantalla y la puse a 800x600. Ah, qué alivio! Incluso, después probé con una más alta y anduvo. Bárbaro! Ahora, digo yo, para qué cuernos me preguntó el tema de las resuluciónes que quería evitar? Okey, dejémoslo ahí, que después de todo se resolvió.

3. Durante la instalación, y como había puesto que quería todo en español, me ofrecieron como ubicación y sistema horario península, baleares o canarias. Yo me dije, después lo cambio y elejí uno al azar. Ahora resulta que el reloj está mal puesto y quiero corregirlo, y ya que estamos cambiemos la zona horaria... pero no, para hacer este cambio el sistema me pide un password, pero qué password? porque yo pongo el de mi usuario y me saca a patadas, lo dejo en blanco y no me da ni cinco de corte... querrá el password de root? Y hasta acá llegó mi alma :help: Pero por lo que ví después este problema también lo tengo cuando quiero instalar el plug-in de flash payer para firefox y cualquier otro plug-in.

4. Y esta es la peorcita por ahora. Resulta que en la barra superior me encuentro con el simbolito de un parlante tachado. Ah, tenés razón, que ahora que pienso no escuché la musiquita de Ubuntu cada vez que arranca. Me pongo con el cursor arriba del icono en cuestión y me sale un cartelito que me dice que el control de volumen no encontró ningún dispositivo al que controlarle el volumen... en pocas palabras quiere decir que en la instalación no me reconoció el sonido? si es eso, cómo lo arreglo? desde ya que se trata de una placa onboard...

Bueno, por ahora no hay más informaciones para este boletín. Si alguno tiene un hueso para tirar, lo espero con los brazos abiertos.

'chas gracia'

---

### Post by clasificado on 2008-05-06
> **ignacioml said:**
> nunca se me pidió un nombre de usuario y contraseña

yo te diria que te lo tomes con limonada.

empezá de vuelta y con paciencia porque hay algo que no me cuadra:
Por uno u otro motivo yo he usado siempre el alternate, y siempre me pidió el usuario y la contraseña.

Si te falta la contraseña del usuario puede que se haya mezclado entre los carteles de la instalación y ahora sea cualquier cosa :lolflag:

clasificado

---

### Post by faktorqm on 2008-05-07
> **ignacioml said:**
> Acá estoy de nuevo.

Bueno, le hice caso al picharrata y me bajé el alternate CD. Estuve chusmeando por ahi cómo se hacía y me mandé. Reparticioné el disco porque las particiones anteriores tenían unos tamaños extraños. Y en principio tuve dos problemas y después un tercero y un cuarto.

1. Durante la instalación, a diferencia de lo que me pasó durante la instalación gráfica, nunca se me pidió un nombre de usuario y contraseña. Ergo, cuando arrancó el sistema se me llenó el tugen de preguntas cuando para entrar tenía que contar con usuario y contraseña. A grandes problemas, grandes soluciones... durante el arranque apreté Esc y entré en modo texto siendo root sin poner ningún password! y bué, no me quedó otra que apelar a mis pobres nociones unixescas/linuxescas y por medio del comando adduser me creé un usuario y una contraseña. Listo el pollo!

2. Durante la instalación, llegué a una instancia en la que me preguntaban si no quería evitar que el sistema funcione con ciertas resoluciones de pantalla. Sí, justo lo que yo quería! Las taché todas excepto las 640x480 y 800x600. Genial! Pero resulta que cuando el sistema arrancó y me pedía un usuario, lo hizo en 1280xandá a saber cuánto y a qué tasa de refresco. Decí que por más que veía doble alcanzaba a distinguir algo. Entonces cuando entré con mi usuario me metí en el menú fuí a resolución de pantalla y la puse a 800x600. Ah, qué alivio! Incluso, después probé con una más alta y anduvo. Bárbaro! Ahora, digo yo, para qué cuernos me preguntó el tema de las resuluciónes que quería evitar? Okey, dejémoslo ahí, que después de todo se resolvió.

3. Durante la instalación, y como había puesto que quería todo en español, me ofrecieron como ubicación y sistema horario península, baleares o canarias. Yo me dije, después lo cambio y elejí uno al azar. Ahora resulta que el reloj está mal puesto y quiero corregirlo, y ya que estamos cambiemos la zona horaria... pero no, para hacer este cambio el sistema me pide un password, pero qué password? porque yo pongo el de mi usuario y me saca a patadas, lo dejo en blanco y no me da ni cinco de corte... querrá el password de root? Y hasta acá llegó mi alma :help: Pero por lo que ví después este problema también lo tengo cuando quiero instalar el plug-in de flash payer para firefox y cualquier otro plug-in.

4. Y esta es la peorcita por ahora. Resulta que en la barra superior me encuentro con el simbolito de un parlante tachado. Ah, tenés razón, que ahora que pienso no escuché la musiquita de Ubuntu cada vez que arranca. Me pongo con el cursor arriba del icono en cuestión y me sale un cartelito que me dice que el control de volumen no encontró ningún dispositivo al que controlarle el volumen... en pocas palabras quiere decir que en la instalación no me reconoció el sonido? si es eso, cómo lo arreglo? desde ya que se trata de una placa onboard...

Bueno, por ahora no hay más informaciones para este boletín. Si alguno tiene un hueso para tirar, lo espero con los brazos abiertos.

'chas gracia'

perdon por tardar, estoy con parciales :s

3) normal. a mi tambien me paso. Ir a sistema -> administracion -> fecha y hora.
Apretar desbloquear, poner la contraseña, y en el primer cuadrito que te aparece dice "zona horaria", y lo cambias de ahi.

4) ir a sistema -> preferencias -> sonido y en el cartel que te aparece, apreta probar, si no te anda, pone alsa, si no te anda, oss, si no te anda, pulseaudio, si no te anda, screenshot y postealo :)

Salu2!!

---

### Post by ignacioml on 2008-05-10
Bueno, acá estoy de vuelta.

Tardé porque estuve probando como solución darle permisos a mi usuario, ponerlo en todos los grupos en los que cae el usuario que crea ubuntu. No funcionó nada.

Al final le hice caso a clasificado y reinstalé todo. Y creo saber dónde empezó todo el problema. Cuando instalé la primera vez, una de las primeras cosas que hace la instalación es preguntarte tu nombre y te dice que una buena idea es poner tu nombre completo. Yo que soy un paranoico que no pone en ningún lado nombre y apellido juntos (a menos que se trate de algo muy necesario) cuando me preguntó el nombre yo lo dejé en blanco; y después nunca me pidió nombre de usuario ni contraseña.

Ahora, cuando reinstalé, le puse un nombre cualquiera y después sí me pidió usuario y contraseña y anduvo todo bien.

pincha : te agradezco por las soluciones propuestas. La de la zona horaria tenía idea de que era así pero como tenía problemas con el usuario con el que entraba al sistema nunca llegaba a la instancia en la que había que hacer los cambios. Ahora que anda todo bien con el usuario, ya cambié todo.
Y por el tema del audio, no me hizo falta, porque ahora anda. No me preguntes cómo ni por qué, pero desde la primera vez que entré al sitema escuché los tambores. :)

Gracias

Ah, ¿y cómo hago para cambiarle el título al post y agregar [Solucionado]?

nacho

---

### Post by faktorqm on 2008-05-11
Creo que no se puede. Lo sacaron con la nueva version del foro. no se como de manejan los admins al respecto. Me alegro mucho de que te haya servido. Salu2!

---

