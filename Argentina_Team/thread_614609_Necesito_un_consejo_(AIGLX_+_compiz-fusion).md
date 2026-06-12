---
title: "Necesito un consejo (AIGLX + compiz-fusion)"
date: 2007-11-16
forum: Argentina Team
---

### Post by faktorqm on 2007-11-16
Hola a todos, quiero básicamente un consejo específico sobre cómo instalar la aceleración 3D de mi escritorio, por que hay 150000 tutoriales, aún en este mismo foro. Tengo una GForce 4 MX-440, 512mb de RAM. 
Lo que necesito es lo siguiente (creo):

- saber si me conviene XGL o AIGLX y por qué.

- saber si me conviene compiz, beryl o compiz-fusion, y por qué.

- un tutorial, (EL tutorial), ese que lo siguieron todos y les anduvo a la perfección y nadie tuvo ningún problema.

Aclaro desde el vamos que tengo el driver de NVIDIA bien instalado, me muestra el logo de nvidia cuando arranca y el ubuntu me dice que el controlador restringido esta activado y en uso. tengo feisty 7.04, por que el 7.10 gutsy la verdad un desastre.... mejor no toquemos el tema.

Desde ya muchas gracias a todos y por favor, hagan un sticky con el tuto ;) salu2!

---

### Post by sajnox on 2007-11-16
Amigo faktor,

> - saber si me conviene XGL o AIGLX y por qué.

Sinceramente aca mucho no te puedo ayudar, soy esclavo de una placa ATI y lo unico que a mi me anda es con AIGLX y anda bien, las veces que intente con XGL lo unico que pude hacer fue desinstarlo


> 
- saber si me conviene compiz, beryl o compiz-fusion, y por qué.

Yo estoy con compiz fusion y lo veo como el mas estable, Beryl es un fork de del compiz original y ahora se volvieron a unir, las novedades y el mayor trabajo hoy se lo lleva compiz fusion. Para mas informacion te aconsejo que leas [ESTO]("http://wiki.compiz-fusion.org/CompizFusionVsCompiz")

> - un tutorial, (EL tutorial), ese que lo siguieron todos y les anduvo a la perfección y nadie tuvo ningún problema.

A mi el que me anduvo es [ESTE]("http://tuxpepino.wordpress.com/2007/06/30/instalar-compiz-fusion-en-ubuntu-feisty/") y todos los tutos que publica el amigo tuxpepino andan bien

Espero que te sirva!!!

---

### Post by vk-cdg on 2007-11-16
Te cuento mi experiencia de novato, como para que tengas un punto de vista mas. Hace solo 3 meses que estoy con Ubuntu y vengo del mundo de las ventanas.
En el trabajo tengo un 7.04 sin beryl ni compiz porque no me da la placa de video (32mb). Contra eso no puedo hacer nada porque es una estación de trabajo corporativa, gracias que pude instalar ubuntu.

En casa decidí esperar hasta que saliera el 7.10, lo instalé y luego de habilitar los controladores restringidos tuve problemas con la detección del monitor, tuve que toquetear a mano el xorg.conf y a partir de ahí todo anda de maravillas. No tuve ni un solo problema.

Decidí instalar quedarme con compiz fusion ya que ahora todo el empeño y novedades lo tendrá el y no tanto (por no decir nada) Beryl.

En fin, es una apuesta, como cuando elegimos una distro de Linux

---

### Post by niko_3100 on 2007-11-17
Te conviene compiz-fusion por beryl ya se abandono y compiz tambien, es decir se fusionaron para dar nombre al proyecto compiz-fusion. Metele eso, Por lo otro creo que te conviene XGL en la wiki tiene una breve explicacion pero no dice bien las diferencias, anda por XGL que es de X.org fijate ahi tambien.

---

### Post by clasificado on 2007-11-17
Trataré de ampliar un poco el comentario del compañero Niko

**Sobre Compiz-Fusion**
[quote=http://es.wikipedia.org/wiki/Compiz_Fusion]Compiz Fusion es el resultado de la unión entre el paquete "Compiz Extras" de Compiz y las partes del proyecto Beryl [...] (Por lo que es) más estable al contar con Compiz como núcleo. [/quote]

Compiz es el nucleo funcional y sobre el, compiz fusion un paquete de plugins que lo hacen espectacular (lo que todos queremos).

**Sobre Xgl y Aiglx**l
[quote=http://es.wikipedia.org/wiki/XGL](Xgl es) una capa que se encuentra sobre OpenGL vía glitz. Aprovecha las ventajas de las modernas tarjetas gráficas mediante sus controladores OpenGL, que soportan aceleración por hardware de todas las aplicaciones X[/quote]

[quote=http://es.wikipedia.org/wiki/AIGLX] (AIGLX es un proyecto libre) para permitir aceleración indirecta GLX, capacidad de render en X.Org y drivers DRI. Les brinda un renderizado hecho completamente por hardware a los clientes remotos de X[/quote]

Por cuestiones de complejidad, la comunidad está mas de acuerdo en que utilizar AIGLX tiene mas beneficios, ya que simplifica el asunto careciendo de la capa adicional que necesita XGL.

Aunque por otro lado, la pobreza de [los drivers privativos de ATI hacen que no puedan utilizar AIGLX]("http://customisinglife.wordpress.com/2006/11/06/no-3d-acceleration-for-aiglx-with-ati/") ya que no lo soporta (paradójico: [el driver open source para ATI si funciona]("https://help.ubuntu.com/community/RadeonDriver#head-a0611c41ff1ce7fa4e0245e29ce6e33c7ed30209")),[ por lo que es comun que se les recomiende usar XGL]("https://help.ubuntu.com/community/CompositeManager/AIGLX")

***Paren las rotativas!!*** [El nuevo driver ATI ya soporta AIGLX]("http://barrapunto.com/articles/07/10/24/0852227.shtml"). Sin embargo, a un esceptico como yo, incuso dentro de este bunker antiatómico del cual estoy tecleando, le queda claro que si bien es un gran avance el aiglx es una sola de las muchas tareas de las que se encarga la placa de video, y otra que suele andar bastante mal es el renderizado directo que se usa para reproducir videos, que en por promedio de todo driver hecho desde una empresa privada para linux, siempre puede ser que ande lo suficientemente mal como para que sea inusable.

por lo que habrá que probar

Clasificado

---

### Post by faktorqm on 2007-11-20
Hola muchachos, active compiz fusion y anda re bien. tengo algunas dudas de cosas pero la verdad no tuve tiempo ni de mirar el compizconfig asi que primero lo testeo un poki yo luego pregunto si no encuentro solucion. GRACIAS POR EL TUTO!!!!!!!!!!!!!!!

la pregunta que me cabe si o si es: ¿como hago para saber si tengo la aceleracion AIGLX activada? por que si tengo xgl, no lo estoy usando, lo tendria que activar. aparte compiz sobre xgl me abduce la pc. recien acabo de ver en la guia ubuntu un tip que parece que soluciona el problema del rendimiento ¬¬

esos repositorios de treviño son confiables no? quien es treviño? por que tiene repositorios y yo no? aparte cada vez que quiero hacer algo que tenga que ver con eyecandy aparece treviño en el medio...........

che otra cosa: ¿como instalo Avant windows navigator? recuerden que estoy en 7.04 todavia. busque en los foros pero aparecen primero los de 7.10 y no iba a andar filtrando medio foro ;)

"dejame llevarte hacia donde voy, strawberry fields forever"

---

### Post by niko_3100 on 2007-11-20
Treviño son repositorios no oficiales de canonical, de la comunidad que se mantiene actualizado por los usuarios de ubuntu. Son confiables yo me baje el amsn 0.97 y el wine ultimo y nada andubo todo bien. Mira yo para nvidia tengo xgl y la verdad que compiz me anda de 10.

---

### Post by vk-cdg on 2007-11-20
Ya tiene repositorios para Gusty?
La última vez que gogleé no había pero fue hace un tiempito ya.

---

### Post by faktorqm on 2007-11-20
si si estan a full con gutsy los tipos. me parece que la limaste un pokito por que sino mira la fecha de este blog!

[http://tuxpepino.wordpress.com/2007/08/01/instalar-avant-window-navigator/](http://tuxpepino.wordpress.com/2007/08/01/instalar-avant-window-navigator/)

ojo! capaz el chabon lo actualizo, no se fijate que ahi dice. ahora bien, alguien para 7.04?

vos decis ke pruebe XGL que va andar rapido? va, rapido no, acelerado? que placa tenes? lei por ahi que AIGLX ya viene por defecto en el driver de nvidia, sera cierto? gracias a todos loco!!!!

---

### Post by vk-cdg on 2007-11-20
Evidentemente lo actualizó, porque ese tuto no estaba. 

Gracias mil

---

