---
title: "No puedo conectarme via dial up en Feisty"
date: 2007-04-07
forum: Argentina Team
---

### Post by atari130xe on 2007-04-07
Hola Foro "loco" Argentina :lolflag:  Mi primer post acá pero ya tengo algunos en ubuntuforums en Inglés. Voy al grano, me bajé la ISO de Feisty Fawn Beta, que en mi pc corre bien como Live CD, pero resulta que a diferencia de Edgy (lo tengo instalado), no puedo conectarme por modem dial up (vivo en una montaña y no hay otro medio por ahora), configuro (siempre hablando del modo Live CD, PPPconfig, completo todos los parámetros (Nombre de la conexión, los DNS primario y secundarios (los mismos que uso en Edgy), luego "pon Arnet" (es mi ISP) se conecta y cuando quiero navegar, no pasa one, no se corta ni nada solo que no puedo entrar en ninguna página, alguien tiene alguna idea de como corregir esto? Si necesitan algún listado u otros datos, me avisan y posteo. muchas gracias y saludos desde Bariloche.

---

### Post by guidorossi on 2007-04-07
creo q ese es un error tipico de DNSs. fijate de tener configurados los DNS que te da tu proveedor, y sino recomiendo [OpenDNS]("http://www.opendns.com/")

---

### Post by atari130xe on 2007-04-07
gracias, pero hay algo que no entiendo, si en Edgy funcan esos DNS porque en Feisty no?
*Es posible que Feisty cuando inicia cargue "por defecto" la conexion via ethernet? y que eso "bloquee" de alguna manera mi modem dial up?, podría probar a desabiltar ethernet, funcionará?

---

### Post by atari130xe on 2007-04-09
Nadie usa dial up en Argentina? jajaja che una manito si quiera... :confused:  que podrá ser el problema?

---

### Post by beuno on 2007-04-09
> **atari130xe said:**
> gracias, pero hay algo que no entiendo, si en Edgy funcan esos DNS porque en Feisty no?

Hubo un cambio muy grande entre Edgy y Feisty en cuanto al manejo de todo lo que es redes.
Ahora se usa "network manager" por defecto, haciendo que cambien algunas cosas.
No uso dialup hace un rato ya, asi que no sabria indicarte bien, pero un alternativa es desinstalar network-manager para poder configurar todo igual que con Edgy.

Suerte.

---

### Post by marianom on 2007-04-09
Si tenés la evidencia concreta del problema, deberías levantar un bug en launchpad.

---

### Post by gepatino on 2007-04-09
Yo soy de los uso dial up, pero todavia estoy con edgy. Esta semana me estaré pasando a feisty y espero poder resolver lo de la conexion sino soné (en casa no tengo banda ancha)

Como dijeron más arriba, trata de configurar la conexion con el network-manager, debe haber alguna opción que permita setear los dns desde la conexion dialup, por lo menos en el antiguo administrador de redes se podia.

---

### Post by atari130xe on 2007-04-09
> **marianom said:**
> Si tenés la evidencia concreta del problema, deberías levantar un bug en launchpad.

Evidencia concreta? jeje si en Edgy configurás tu conexion de una manera y funciona perfectamente y estoy acá posteando que hice exactamente lo mismo con Feisty: PPPconfig, etc etc, y NO HAY MANERA de poder usar internet (ESTANDO CONECTADO), que más "evidencia" se necesita? :confused:

---

### Post by atari130xe on 2007-04-09
> **gepatino said:**
> Yo soy de los uso dial up, pero todavia estoy con edgy. Esta semana me estaré pasando a feisty y espero poder resolver lo de la conexion sino soné (en casa no tengo banda ancha)

Como dijeron más arriba, trata de configurar la conexion con el network-manager, debe haber alguna opción que permita setear los dns desde la conexion dialup, por lo menos en el antiguo administrador de redes se podia.

Al menos a mí Feisty me parece más "estable" en MI PC claro, y tiene algo que Edgy no tiene "automounting" por ende no necesito montar las particiones en mi HD, al menos Edgy y mucho menos Dapper lo hacen en mi compu, es más tuve que darle al fstab a lo pavo en esas 2 cosas que en feisty me lo hace al inicio y de manera automática, por esto estoy tan interesado en lograr conectarme a la net, no tengo otra opcón que dial up por el momento, asi que espero solucionar el tema muy pronto. :)

---

### Post by atari130xe on 2007-04-09
> **beuno said:**
> Hubo un cambio muy grande entre Edgy y Feisty en cuanto al manejo de todo lo que es redes.
Ahora se usa "network manager" por defecto, haciendo que cambien algunas cosas.
No uso dialup hace un rato ya, asi que no sabria indicarte bien, pero un alternativa es desinstalar network-manager para poder configurar todo igual que con Edgy.

Suerte.

Trato de hacer funcionar la conexión en el Modo LIve antes de instalarlo definitivamente en mi PC por eso no creo pueda "desinstalarlo" de esa manera pero si no me queda otra tendré que solucionarlo instalandola, cosa que prefiero no hacer hasta que no salga la version final el 19/04

---

### Post by marianom on 2007-04-09
> **atari130xe said:**
> Evidencia concreta? jeje si en Edgy configurás tu conexion de una manera y funciona perfectamente y estoy acá posteando que hice exactamente lo mismo con Feisty: PPPconfig, etc etc, y NO HAY MANERA de poder usar internet (ESTANDO CONECTADO), que más "evidencia" se necesita? :confused:

Si es un problema del distro y se necesita repararlo hay que crear un bug para que la gente que lo tiene que ver, lo pueda verificar y si no le das mensajes de error ni nada con que trabajar, solo van a rechazar el pedido.

Lo de evidencia es "medianamente" fácil: lo mismo que corres por GUI correrlo por terminal para identificar mensajes de error (o la ausencia de), verificar en los logs del directorio /var si tenés un mensaje de error que te permita identificar el problema o correr el bugbuddy con la instrucción para que trackee el proceso.

Yo entiendo el tiempo que consume este tipo de tareas en investigación hasta que des con algo útil pero eventualmente dar información válida va a ayudar a todos: a vos porque te van a arreglar el problema y a otros para que no les pase. Por supuesto, si es que es un bug.

---

### Post by atari130xe on 2007-04-09
> **marianom said:**
> Si es un problema del distro y se necesita repararlo hay que crear un bug para que la gente que lo tiene que ver, lo pueda verificar y si no le das mensajes de error ni nada con que trabajar, solo van a rechazar el pedido.

Lo de evidencia es "medianamente" fácil: lo mismo que corres por GUI correrlo por terminal para identificar mensajes de error (o la ausencia de), verificar en los logs del directorio /var si tenés un mensaje de error que te permita identificar el problema o correr el bugbuddy con la instrucción para que trackee el proceso.

Yo entiendo el tiempo que consume este tipo de tareas en investigación hasta que des con algo útil pero eventualmente dar información válida va a ayudar a todos: a vos porque te van a arreglar el problema y a otros para que no les pase. Por supuesto, si es que es un bug.

Claro, es totalmente comprensible, asi debe funcionar para que todos tengan su SO funcionando a pleno. Estuve probando con Ifconfig y par de cosas más pero nada todavía. De todas maneras si alguien tiene algún procedimiento como para verificar el funcionamiento seria mejor asi lo ejecuto. No soy muy ducho en Linux y mucho menos en redes, asi que todo es bienvenido, sé que al menos en Argentina todavía hay mucha gente que usa dial up y esto ayudaria para los que quieren instalar Ubuntu en sus PC´s.

---

### Post by atari130xe on 2007-04-10
nadie tiene mi problema? que suerte! :confused: , bueno paciencia, cuando aparezca alguien vemos, grax igual

---

