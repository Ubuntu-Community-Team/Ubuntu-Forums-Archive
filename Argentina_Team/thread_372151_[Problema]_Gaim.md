---
title: "[Problema] Gaim"
date: 2007-02-27
forum: Argentina Team
---

### Post by dj termitu on 2007-02-27
Hola, me llamo Andrés. Hace no mucho que me pasé a ubuntu. Hoy estaba haciendo una instalación nueva desde 0 de ubuntu. Lo que hice fue instalar ubuntu, luego descargar las actualizaciones, luego hice algunos de los pasos que se encuentran en esta página:
[http://www.ubuntu-es.org/node/4440](http://www.ubuntu-es.org/node/4440)
Y otros de los que se encuentran en esta:
[http://www.bootlog.cl/blog/tips/guia-post-instalacion-ubuntu-edgy-i/](http://www.bootlog.cl/blog/tips/guia-post-instalacion-ubuntu-edgy-i/)
Y también instalé el programa "envy" que lo que hace es configurarte la placa de video. (


Bueno, ahora paso a comentar el problema. En el gaim cuando recibo emoticons, no se de que tipo, se me cierra de la nada.

También tengo otro problema. El tema es que las mayusculas no cambian rapidamente en ubuntu, entonces casi siempre al comenzar a escribir me salen 2 mayusculas juntas, por ejemplo si yo quiero decir "No" escribo "NO", o con la palabra "También" escribo "TAmbién".

Esos son los unicos 2 problemas que me surgieron hasta el momento
Espero sus respuestas y desde ya muchas gracias por la ayuda que me puedan brindar

Andrés

EDIT: también estuve buscando en google y no encontré a nadie con un problema parecido al mio, quizás por que habré buscado mal.

---

### Post by clasificado on 2007-02-28
¡Que loco!

Te recomiendo **encontrar los logs del gaim**. Despues postealo y vemos por acá que se puede hacer.

Segun su sitio web, estan por acá:
```

Where does gaim store its logs?
    **On unix, they are in ~/.gaim/logs**, on win32 they are in the C:\Documents and Settings\user\Application Data\.gaim\logs directory. (NOTE: Application Data is a hidden directory.) In either case, new logs (new as of 0.73) are in subdirectories that correspond to protocol/yourscreenname/theirscreenname.

```

Si nó, hay una forma mas complicada que es **abrir una consola, y ejecutar el gaim desde ahi** (escribite **gaim** sin mas vueltas y arranca). La diferencia es que va escribiendo en la consola todo lo que se le ocurre que viene al caso, inclusive los errores. Cuando se cuelge, **copialo y traelo a nosotros** que tambien puede ser util :D. Conste que son dos cosas distintas

Tirando al boleo, se me ocurre que puede ser que se te haya roto algun dibujador gráfico (siendo bruto). Reinstalandolo alcanzaría, pero hay que ver _cual_ es

Ahora, lo de las mayusculas, *me superó.*

Clasificado.

---

### Post by beuno on 2007-02-28
> **dj termitu said:**
> Bueno, ahora paso a comentar el problema. En el gaim cuando recibo emoticons, no se de que tipo, se me cierra de la nada.

A mi me pasaba eso con alguna version del Gaim (con algun emoticon custom especifico), lo solucione instalando el ultimo Gaim 2 beta6 (o beta5)

---

### Post by BlackHero on 2007-02-28
ami tambien me pasaba esactamente lo mismo hasta que lo actualize al beta 5 y despues al 6 nunca mas ese problema es muy tedioso y encima tenia una bronca por que de la nada pasaba instala el gaim desde su ultima actualizacion de aca [http://www.debuntu.org/gaim-2.0.0beta6-edgy-networkmanager-support](http://www.debuntu.org/gaim-2.0.0beta6-edgy-networkmanager-support)  ahi te va a decir que agregues unas lineas a tu repositirio despues de hacer eso abri consola y tipea sudo aptitude update luego que actualize sudo aptitude install gaim y listo ya vas a tener gaim nuevo y vas a poder poner imagenes tambien lo que antes no se podia hacer =)

---

### Post by lavaramano on 2007-02-28
yo estoy teniendo un quilombo con el beta5 que me rompe mucho las bolas.
cuando me pasan un archivo via msn/icq/loquesea, el campo del nombre del archivo en la ventanita donde elegis donde lo vas a guardar, me aparece vacio. entonces tengo que completarlo yo.

alguna idea? (uso dapper y no pienso actualizar :mrgreen: )

creo que voy a tyerminar bajando al source y compilarme al beta 6..

---

### Post by beuno on 2007-02-28
> **lavaramano said:**
> yo estoy teniendo un quilombo con el beta5 que me rompe mucho las bolas.
cuando me pasan un archivo via msn/icq/loquesea, el campo del nombre del archivo en la ventanita donde elegis donde lo vas a guardar, me aparece vacio. entonces tengo que completarlo yo.

alguna idea? (uso dapper y no pienso actualizar :mrgreen: )

creo que voy a tyerminar bajando al source y compilarme al beta 6..

A mi me pasaba con varias apps en Edgy, por ahora no me paso en Feisty.
Creo que no es un tema del gaim, sino algo del gtk+, pero no quiero mentir.

---

### Post by zspikes on 2007-02-28
yo tenia el mismo problema con el gaim, y me habia resignado ya y estaba usando el meebo (www4.meebo.com). La cosa es q cuando actualice a edgy, se actualizo el gaim tb y el problema termino. Quiza tengas q actualizar el gaim.

---

### Post by dj termitu on 2007-02-28
Bueno, el tema del gaim está solucionado. Ahora pasemos al tema de las 2 mayusculas que se me hacen en vez de una. Vuelvo a explicar mi problema. Ahora estoy escribiendo bien pero vean atentamente si escribo rapido.

BUeno el problema es que me aparecen 2 mayusculas al comienzo y en windows no era asi. YA probe cambiandole la velocidad del teclado. NO funcionó eso.

AHora entienden cual es mi problema?

Mi teclado es Microsoft wireless multimedia keyboard pero también enchufe uno con cable y es lo mismo.

Hay alguna solución para esto?

---

### Post by spg76 on 2007-02-28
Te fijaste en "Preferencias de Teclado", en donde dice "Opciones de Distribución", hay un grupo llamado "Comportamiento de BloqMayus" y otro "Comportamiento de Mayus/Bloq".
Quizas probando alguna de las opciones te solucione el problema.

---

### Post by dj termitu on 2007-02-28
> **spg76 said:**
> Te fijaste en "Preferencias de Teclado", en donde dice "Opciones de Distribución", hay un grupo llamado "Comportamiento de BloqMayus" y otro "Comportamiento de Mayus/Bloq".
Quizas probando alguna de las opciones te solucione el problema.
No, no es ninguno de esos :S

Ahora otra pregunta, hay alguna forma de correr el warcraft iii con el wine? por que por lo que entendi el winex es pago.

---

### Post by clasificado on 2007-02-28
> **dj termitu said:**
> Ahora otra pregunta, hay alguna forma de correr el warcraft iii con el wine? por que por lo que entendi el winex es pago.

Segun [el appdb de wine](http://appdb.winehq.org/appview.php?iVersionId=1177), el Warcraft 3 anda bastante bien si se usa opengl, aceptando algunos problemas graficos en los botones.

Es un How-to, por ahi no sea a prueba de bobos pero te lo deja andando.

Clasificado.

PD: Soy medio enfermito con el orden, porque me da comodidad: Si tenés algo mas que decir sobre el Warcraft 3, te recomiendo que **abras un nuevo thread** asi hablamos libremente sobre el Warcraft 3 y no mezclamos el asunto con el Gaim que era donde habiamos empezado :P

---

### Post by dj termitu on 2007-03-01
Muchas gracias, ya probe un how to pero no me deja abrir el warcraft :P
espero que este si, después lo voy a probar por que ahora me tengo que ir a estudiar

---

