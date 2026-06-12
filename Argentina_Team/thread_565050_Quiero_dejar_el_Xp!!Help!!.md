---
title: "Quiero dejar el Xp!!Help!!"
date: 2007-10-01
forum: Argentina Team
---

### Post by Never Here on 2007-10-01
Hola, quiero dejar de usar el Xp y bueno..tengo un par de problemas..

Baje el Ubuntu 7.04 (desktop edition) la version de 64bit AMD y no puedo ejecutarlo en una computadora..o sea..booteo desde el cd y me dice k consiga una distribucion de 32 bits

la computadora en cuestion es una AMD sempron 2600+ , 1,83Ghz, 256 ram, disco de 80 , Placa de video Geforce FX 5200de 32 bit con windows xp service pack 2..se me ocurre k no ande pork la placa es de 32 bits?

en fin..quisiera saber si me pueden ayudar..y si es por la placa k me digan cual me tengo k bajar...en esa makina no tengo internet..

por otro lado tengo una makina con xp service pack 2, AMD Sempron 2800+ , 1.61 Ghz. 448 de ram y un disco de 80 y una placa de video Nvidia GeForce 6100 nForce 405 y kreo k es de 256..
bueno, en esta makina si me corre el ubuntu en live..pero cuando quiero ver si puedo hacer lo del cubo me pide k instale los unos drivers de la placa y cuando le mando k si es obvio k no los puede bajar pork no se conecta a internet...

alguien me puede ayudar? 

desde ya muchas..gracias

PD: soy muuy basico con esto de linux..si todo sale bien lo pondria en la makina k tiene inet..pero eso le dejamos para otro dia..

---

### Post by Hei Ku on 2007-10-01
mi recomendacion sería que lo pruebes en la maquina que tiene internet, con un liveCD de la version de 32bits. El tema es que los drivers de la placa de video los tiene que bajar de internet, y va a ser mas facil para que lo pruebes.

Ahora, si solo lo queres instalar por el cubo, te diria que lo pienses dos veces, y lo evalues desde el LiveCD. La parte importante de usar una PC es para que la vas a usar, y de eso depende que el cambio a Linux sea mas o menos facil. El cubo, y otros efectos graficos dejan de tener importancia cuando no podes hacer las cosas realmente importantes.

---

### Post by Never Here on 2007-10-01
Hola, gracias por responder tan rapido..el tema va asi..en este momento se esta bajando el otro ubuntu..el i386..ese es el de 32 bits?
y si, aparte de lo del cubo me interesa todas las demas fucionalidades..el tema es k lamentablemente mi hermanastro vio un video del linux con el beryl y bueno..me esta hinchando las bolas desde ese dia...o sea..el viernes..bueno..la de el seria la makina sin inet..
ahora la mia..la k tiene inet no puedo ver lo del cubo desde el live pork me pide los drivers pero no se puede conectar..alguna sugerencia??

desde ya muchas gracias:)

---

### Post by msangil on 2007-10-01
Fijate en ***Sistema / Administrador / Gestor de controladores restringidos*** si no tenés ahí un driver esperando a que lo tildes como OK para usar.

Normalmente esto te lo avisa cuando inicia después de que instalaste en la barra de tareas (arriba derecha, al lado del día y la hora). El iconito es como si fuera el dibujo de una placa en color verde. Por alguna razón capaz no lo mostró o no lo viste.

Si, el que dice x86 es el de 32 bits. Usá ese que es el que corresponde con tu micro.

Cuando instales la versión 32 bits contanos a ver si te apareció esto que te decía.

No te olvides después de leer cómo [habilitar multimedia]("http://ubuntuforums.org/showthread.php?t=413624") en Ubuntu porque si no la mitad de los archivos no los vas a poder ver (está en inglés - acá en el foro de Argentina tiene que haber seguro uno en castellano).

Éxitos con eso.

---

### Post by User21 on 2007-10-01
**[www.guia-ubuntu.org](www.guia-ubuntu.org) y pegate una mirada por el foro. Googleá y lee y recontra lee. Lamentablemente XP nos hizo tontos, y ahora nos cuesta APRENDER! **

---

### Post by Chilongola on 2007-10-02


yo no lo pude decir mejor!!!!!

Te va a gustar todo esto de Linux (Ubuntu).  Sigue contandonos como te va.

---

### Post by Never Here on 2007-10-02
hola..gracias por responder y por la guia..estoy leyendo..pero antes de seguir tengo una duda "existencial"..
es necesario que tenga conexion a internet para poder instalar correctamente el ubuntu y los paquetes con los codecs?

o sea..en una maquina que no tiene internet..puedo hacer todo eso?
y sino..como hago(si es que hay alguna forma) de bajarlo a la makina que si tiene internet y pasarlo a la otra(que no tiene)

desde ya ,muchas gracias

---

### Post by JoACoV on 2007-10-02
> **Never Here said:**
> hola..gracias por responder y por la guia..estoy leyendo..pero antes de seguir tengo una duda "existencial"..
es necesario que tenga conexion a internet para poder instalar correctamente el ubuntu y los paquetes con los codecs?

o sea..en una maquina que no tiene internet..puedo hacer todo eso?
y sino..como hago(si es que hay alguna forma) de bajarlo a la makina que si tiene internet y pasarlo a la otra(que no tiene)

desde ya ,muchas gracias
si se puede, lo que tenés que hacer es bajarte los paquetes que correspondan y grabarlo en un cd o algo asi y copiarlos en la otra maquina para instalarlos. Otro user cn mas experiencia capaz que te pueda dar mas detalles, yo soy muy novato (Instale Ubuntu hace 2 días)

---

### Post by marianom on 2007-10-02
Never Here, busca en este mismo foro argentino por el tema de "paquetes", "sin internet" (y algunas otras palabras alusivas): hay algunos posts muy buenos y muy completos sobre como instalar paquetes sin net.

---

### Post by Chilongola on 2007-10-03
La primer vez que instale Ubuntu lo hice sin internet.  Probe varios programas por casi dos semanas antes de conectarlo al internet.  Programas basicos, desde luego...

---

### Post by Never Here on 2007-10-10
Hola
bueno, despues de una semana de idas y vueltas termine instalando el ubuntu en la makina sin internet..y conserve el xp!!:)

baje un par codecs para poder escuchar mp3 y ver algunos videos..podriamos decir k fue una instalacion "exitosa"..podriamos, pero todavia tengo un par de "problemas" para k kede completamente funcional..

1. de un thread de este mismo foro sake los paquetes de los codecs..bueno, el tema es k algunos de los paquetes me dice k no estan o cuando los bajo y los kiero instalar el SO no me deja pork no se k problema con la dependencia...
2. no baje ningun driver para la placa de video..pero baje unos paquetes k habia en otro thread de aka k decia(o por lo menos eso entendi) k kon eso le andaba bien, pero a mi unos paquetes me decian lo mismo de la dependencia y no los pude instalar..ah, tengo una nvidia Geforce fx5200..
3. cuando baje esos paquetes hubo 2 k me andaban, me decia k ya estaban instalados y los reinstale igual..y ahi fui a controladores restringidos para habilitar la placa y me decia k no hacia falta, como k ya estaba todo bien..asi k me voy a efectos de escritorio y aka viene el problema..se me keda la pantalla en blanco..o sea, toda la pantalla en blanco pero con el cursor..ahora quisiera saber si es pork me faltan los drivers o pork la placa no se banca los efectos de escritorio..si asi fuera seria una desilusion para mi hermanastro..mi placa es un pokito mejor:)

bueno, si alguien me puede decir donde bajar algunas de estas cosas estare muy feliz..y tmb donde bajar el beryl para poder instalarlo en la otra makina asi mi hermanastro o se pone feliz o se termina de frustar :P

bueno, sin mas, muchas gracias ;)

---

### Post by hernyman on 2007-10-11
> **Never Here said:**
> la computadora en cuestion es una AMD sempron 2600+ 

Debe ser un Sempron de los de socket 754, de esos creo que la mayoría (o todos, no me acuerdo ahora) son de 32 bit nada más.

---

### Post by Hernán-Amaya on 2007-10-11
Por el tema de las dependencias suelen traer algunos dolores de cabeza! fijate que paquetes te pide para instalar y bajalos. cualquier cosa pregunta

---

### Post by WanderingKnight on 2007-10-11
> 
3. cuando baje esos paquetes hubo 2 k me andaban, me decia k ya estaban instalados y los reinstale igual..y ahi fui a controladores restringidos para habilitar la placa y me decia k no hacia falta, como k ya estaba todo bien..asi k me voy a efectos de escritorio y aka viene el problema..se me keda la pantalla en blanco..o sea, toda la pantalla en blanco pero con el cursor..ahora quisiera saber si es pork me faltan los drivers o pork la placa no se banca los efectos de escritorio..si asi fuera seria una desilusion para mi hermanastro..mi placa es un pokito mejor

Mira, yo tengo exactamente la misma placa que vos (FX 5200), y Beryl anda sin problemas. Los paquetes que tenes que instalar para que ande correctamente son:

```
beryl
emerald-themes
beryl-manager
```

Despues haces en la consola:

```
sudo gedit /etc/X11/xorg.conf
```

Vas a donde dice:

```
Section "Device"
```

...y agregas:

```
Option          "AddARGBVisuals"        "True"
Option          "AddARGBGLXVisuals"     "True"
```

Despues haces reboot y listo.

El problema es que yo no se exactamente como haces para instalar los paquetes sin conexion a internet... asi que en eso no te puedo ayudar.

---

