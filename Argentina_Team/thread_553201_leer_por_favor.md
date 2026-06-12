---
title: "leer por favor"
date: 2007-09-17
forum: Argentina Team
---

### Post by edd12river on 2007-09-17
primero q todo, agradesco a todos los q me ayudaron hasya ahora, pero todavia no pude solucionar mi problema para conectarme a internet, muchas personas trataron de ayudarme, pero todos contestan lo mismo, q es la solucion del modem de speedy tomson 330 speedtouch pero para ethernet, y yo tengo ese modem para USB...me dieron una guia, pero al tratar de configurar con pppoeconf me dice q no encunetra nada en la placa de red, cosa logica ya q no hay nada conectado ahi...

por favor, nesesito solucionar esto cuanto antes, ya q es la pc q uso para trabajar, y no quiero tener q andar pasando datos se una pc a otra, ademas de q en esta pc tengo xp...


desde ya muchas gracias! :)

---

### Post by FlyerDie on 2007-09-17
Master, entiendo tu necesidad...pero no cumplis para nada con el protocolo de un foro.

*Abris un thread con un titulo sin sentido y para nada orientativo.
*Ya estabas haciendo la consulta en otro thread ( [http://ubuntuforums.org/showthread.php?t=547669&highlight=330+speedtouch](http://ubuntuforums.org/showthread.php?t=547669&highlight=330+speedtouch) )
*En ese mismo thread no haces las cosas como te comentan...seguir PASO a PASO..entonces como pretendes que te funcionen las cosas??

1/2 pila :-({|=

---

### Post by por100pre1 on 2007-09-17
Saludos. ¿Has leído [esta]("https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo") guía? [Aquí]("http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=en_es&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FUKSpeedtouchDSLHowTo") hay una traducción automatizada. Espero que te sea útil.

---

### Post by edd12river on 2007-09-17
> **FlyerDie said:**
> *Abris un thread con un titulo sin sentido y para nada orientativo.
ya se q el titulo no tiene sentido, pero entende mi desesperacion y q la poca gente q quiso ayudarme al tiempo desaparecio y me quede sin ayuda..

---

### Post by clasificado on 2007-09-17
> ya se q el titulo no tiene sentido, pero entende mi desesperacion y q la poca gente q quiso ayudarme al tiempo desaparecio y me quede sin ayuda..

No te preocupes, a nosotros también nos habla gente que sin quererlo nos falta el respeto.

Sobre tu modem, fijate las guias que el amigo por100pre1 acercó que son buenas

Clasificado

---

### Post by por100pre1 on 2007-09-17
Dame unos minutos y te doy una traducción decente de esa guía y la posteo...

---

### Post by por100pre1 on 2007-09-17
**Guía para el módem DSL Speedtouch de Reino Unído**

Introducción:

Este documento explica cómo configurar una conección de bánda ancha DSL para personas viviendo en el Reino Unído usando un módem USB u otros módems soportados por el controlador speedtch. 

Instrucciones:

Con kernels modernos (>= 2.6.10) tan solo necesita los paquetes ppp y libatm1. El paquete speedtouch no es necesario. 

Descargue el firmware para módem de [la página de Alcatel]("http://www.speedtouchdsl.com/driver_upgrade_lx_3.0.1.2.htm") y extráigalo con [el extractor de firmware]("http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor"). Si esto le parece complejo, puede descargar e instalar un [paquete de firmware no oficial]("http://people.debian.org/%7Emd/") (por ejemplo: dpkg -i speedtouch-firmware_0.3012k.deb). 

Despues de instalar el firmware puede desconectar y reconectar el modem para cargarlo. 

Copie el archivo /usr/share/doc/ppp/examples/peers-pppoa a, por ejemplo, /etc/ppp/peers/adsl. El siguiente comando realiza esta acción: 

```
sudo cp /usr/share/doc/ppp/examples/peers-pppoa /etc/ppp/peers/adsl
```

Edite con gksudo gedit /etc/ppp/peers/adsl para incluir el nombre de usuario provisto por su proveedor de servicios de internet y los identificadores de VP y VC 0.38 (estos varian de acuerdo con su proveedor de servicios de internet). 

Edite los archivos pap-secrets y/o chap-secrets en la carpeta /etc/ppp/ y actualízelos con el nombre de usuario y contraseña provistos por su proveedor de servicios de internet añadiendolos a cada linea en el formato "NOMBRE-DE-USUARIO" "*" "CONTRASEÑA". 

Después de iniciar, será capaz de comenzar la conneción con los comandos usuales (por ejemplo pon adsl).
[B]
Espero que puedas resolver tu problema.[/B] :)

---

### Post by edd12river on 2007-09-17
una cosa, si el modem arranca, osea prenden las luces y esta para conectar, hay q hacer todo eso?

gracias! desde ya

---

### Post by sajnox on 2007-09-17
POR100PRE1,

Solo mostrarte mi admiracion por tu animo de colaborar en todo y con todos.

Saludos,

---

### Post by por100pre1 on 2007-09-17
> **sajnox said:**
> POR100PRE1,

Solo mostrarte mi admiracion por tu animo de colaborar en todo y con todos.

Saludos,

¡Muchas gracias! Estoy a las ordenes siempre. ¡Disfrutemos todos juntos de la libertad!

---

### Post by por100pre1 on 2007-09-17
> **edd12river said:**
> una cosa, si el modem arranca, osea prenden las luces y esta para conectar, hay q hacer todo eso?

gracias! desde ya

No es justo ni razonable que tengas que hacer todo eso. Mi consejo mas practico sería que simplemente desecharas ese módem. [Aquí]("http://ubuntuforums.org/showpost.php?p=3382159&postcount=12") posteé un rato atrás un comentario al respecto. No solo los usuarios de Ubuntu han tenido dificultades con ese módem, incluso usuarios de Windows Vista están teniendo dificultades con ese módem. Si tu ordenador tiene una tarjeta de Ethernet, puedes adquirir un buen router. Puedes preguntar a tu proveedor de internet que opciones tienen en cuanto a routers se refiere.

---

### Post by marianom on 2007-09-17
Coincido plenamente, vos le estás pagando el servicio, lo justo es que te trataran mejor. Así que a levantar el telefono, recordando lo que dice el tango: "El que no llora, no mama".

---

### Post by edd12river on 2007-09-17
sisi eso hice, pero saban q me dijeron en speedy, q ellos no brindan servicio tecnico de linux, y q no me pueden hacer cambio de  modem porque no tienen stock...¬¬ cosa q seguro es mentira, pero igual voy a hacer la queja en atencion al consumidor...no puede ser que te cobren una fortuna yno te brinden servicio...

gracias, y voy a ver q hago con el modem... :)

---

### Post by leo_rockway on 2007-09-17
No menciones Linux, para la gente del pseudo servicio tecnico de las isp es como si les hablaras en chino. de ultima deciles que tenes vista o algo asi, por100pre1 ya dijo que en vista tambien tiene problemas.

---

### Post by sajnox on 2007-09-17
edd,

1) No menciones que usas Linux, siempre te lo van a usar de excusa...aunque ni sepan de que se trata

2) Deciles que se te rompio el USB que tenias libre y que si no te dan el modem que queres te cambias de compañia, pero hacelo en serio, ya que si no te dan el modem que queres se merecen que te vayas.

Recorda que vos pagar por internet y son ellos los que se tienen que adaptar a tus necesidades no vos a las de ellos

Saludos

---

### Post by LaHire on 2007-09-18
> **sajnox said:**
> edd,

1) No menciones que usas Linux, siempre te lo van a usar de excusa...aunque ni sepan de que se trata

2) Deciles que se te rompio el USB que tenias libre y que si no te dan el modem que queres te cambias de compañia, pero hacelo en serio, ya que si no te dan el modem que queres se merecen que te vayas.

Recorda que vos pagar por internet y son ellos los que se tienen que adaptar a tus necesidades no vos a las de ellos

Saludos

el punto dos es EL punto.-

tampoco pidas un cisco de 40 bocas, claro :P

Como experiencia personal, a mi también me pasó eso...pero como soy muy tonto para seguir tutoriales, pegué el tubazo y dije "tengo un solo puerto usb, quiero un modem ethernet" y a la semana me lo dieron :/

Yo cometí el error de decir "Si, uso Ubuntu 6.10 con Kernell 2.6.x, en dual boot con Debian Sarge, y quiero saber si me dan un modem nuevo porq este no anda" :P

Y mirá que mis tiradas de carisma no son para nada buenas :)

Espero q lo logres solucionar! :)

---

### Post by leo_rockway on 2007-09-18
> **LaHire said:**
> Si, uso Ubuntu 6.10 con Kernell 2.6.x, en dual boot con Debian Sarge

y no te preguntaron con que se come? :lolflag:
me hace acordar al capitulo de los simpsons en que homero se pone compumundohipermegared y el tipo de los comics le pide una conexion, jaja.

[http://www.youtube.com/watch?v=OeXzrav2R7w](http://www.youtube.com/watch?v=OeXzrav2R7w)

---

### Post by edd12river on 2007-09-18
adivinen q me dijeron los lindos operadores de speedy, cuando le me ti el chamullo de los puertos usb, les dije q mi maquina tiene 2 puertos, uno de la impresora y otro para el "modem" (pongo entre comillas xq estoq tengo n oes un modem, es una m*****), bueno saben q me respondieron...q me compre una placa pci con puertos usb, ahi le meto el chamullo de q la tengo usada, de q tengo dos puertos solos pci uno con la placa de video y otro con la de sonido, y el tipo me dice q no es problema suyo, y yo le digo q si, xq ellos tienen q proporcionarme servicio xq yo les estoy pagando, y ellos me dicen q el problema es ajeno a ellos xq lo q se rompio fue algo de mi pc...osea q ellos se desligan del problema, ahi les digo q bueno esta bien, q no se preocupen q en arnet (para los q no saben arnet=linux, speedy=mircrosofth), el chabo me dice q ellos tmp me hivan a proporcionar un modem de esas caracteristicas, y le digo q es mentira xq ya llame y averigue (ademas sabiebiendo q los d eun call center no pueden colgar xq un amigo labura en uno) ahi le meti una serie de ******** a el a su familia a speedy y a todo lo q se liga a ellos...el chabon no sabia q hacer, me saque mal xq me trato de mentiroso, le dije q hiva a hacer una denuncia en atencion al consumidor y el flaco me corto :s ...xq sera? jaa...bue en un rato llamo de nuevo a ver q onda...no me pienso cambia de empresa, voy a peliar por el modem hasta la murte, y cuando le dije q tenia vista me dieron una pagina para bajarme los drivers..


se q es largo pero vale la pena leerlo! jeje



gracias! y los mantendre al tanto

---

### Post by undiaperfecto on 2007-09-18
bien capo, seguisela a muerte.
yo cuando tenia speedy tampoco tenia compatibilidad y tuve que eliminar mi linux rxart que vino de garbarino, para poner un xp trucho.
ahora tengo fibertel y uso ubuntu, y encima duplicaron las velocidades :)

---

### Post by FlyerDie on 2007-09-18
> **undiaperfecto said:**
> 
ahora tengo fibertel y uso ubuntu, y encima duplicaron las velocidades :)
Es mentira lo de la duplicacion...si lees el mail que te enviaron o la publicidad (letras pequeñas) dice bien clarito que si tenes 2.5mbps te lo pasan a 3mbps...osea, donde esta la duplicacion de bandwidth?? en los pobres enlaces de 640kbps y de 1mbps?? es una estafa...como todo lo de fibertel.

---

### Post by marianom on 2007-09-18
¿En serio? ¡Ufa! Yo había entrado como por un tubo en el verso.

---

### Post by leo_rockway on 2007-09-18
> **edd12river said:**
> ahi le meti una serie de ******** a el a su familia a speedy y a todo lo q se liga a ellos...

yo entiendo que estes enojado, pero el pobre chabon no tiene la culpa de que speedy sea un desastre.
a mi me paso que me queria poner speedy y mi linea telefonica no estaba digitalizada; la mina del call center de telecom me queria convencer de que no era problema de ellos. pense en hacer lo mismo que hiciste vos con este chabon y mandarle un rosario dedicado a su madre, pero seguro la mina gana 600 pesos y encima se tiene q aguantar a todos los payasos que llaman diciendo "se me rompio el internet explorer". asi q me contuve, corte y llame a atencion al consumidor. los de atencion al consumidor me dijeron que tenia que llamar a la reguladora de telecomunicaciones, que ellos no se hacian cargo de ese problema. llame a la reguladora de telecomunicaciones y me dijeron que internet no esta regulado, asi que ellos tp se hacian cargo del problema.
ergo... me puse telecentro. encima los de telecentro me dieron un modem motorola (me sorprendio mucho) con salida ethernet y usb.

---

### Post by Gideon26 on 2007-09-18
Hola bueno coincido con la mayoria de todos el isp en realidad debe ajustarse a tus necesidades aca en neuquen, funciono esto llamar al isp diciendo que queres dar la baja del isp ya que no te dieron el soporte indicado (que es el del modem por lan) y que por tal motivo queres darle la baja y queres pasarte no se que habra por donde estas ( aca hay jetband tambien) y ellos practicamente se bajan los calzones ajaj diciendote que ya mañana o pasado mañana te envian un tecnico para instalarte el otro modem y que como a modo de  disculpa por 3 meses te dan la conexion bificado dejandote a 49 por mes ajja, buenoi aca varios del lug lo hicieron y funciono. no se de ultima proba eso en cuanto  tu consulta en el how to ya respondi a tus dudas.  saludos!

---

### Post by LaHire on 2007-09-19
> **FlyerDie said:**
> Es mentira lo de la duplicacion...si lees el mail que te enviaron o la publicidad (letras pequeñas) dice bien clarito que si tenes 2.5mbps te lo pasan a 3mbps...osea, donde esta la duplicacion de bandwidth?? en los pobres enlaces de 640kbps y de 1mbps?? es una estafa...como todo lo de fibertel.

Seeee, el otro día un tipo vino y me ofreció una tecnología nueva, era algo así como una red de computadoras muy muy grande, la llamó "internet". no le hicimos caso y lo quemamos por hereje...

Es como el otro tipo q vino y dijo que no somos el centro del universo...pfffffffffffffffffffffffffffff hay gente loca, eh

---

### Post by FlyerDie on 2007-09-19
> **LaHire said:**
> Seeee, el otro día un tipo vino y me ofreció una tecnología nueva, era algo así como una red de computadoras muy muy grande, la llamó "internet". no le hicimos caso y lo quemamos por hereje...

Es como el otro tipo q vino y dijo que no somos el centro del universo...pfffffffffffffffffffffffffffff hay gente loca, eh

Te comento que yo tengo ADSL, y en su momento cuando a los clientes que teniamos 2.5mbps nos lo DUPLICARON, tenia velocidades cercanas a los 5mbps de download...es obvio que solo lo tuve durante el tiempo que duro la promocion ya que no pensaba pagar lo que salen los 5mbps de ADSL.
La **** de Fibertel es el netcache que utilizan entonces nunca tenes la velocidad real de salida de la que te venden ya que esa velocidad la tenes realmente y silo contra sus equipos y no contra la nube.

---

### Post by faktorqm on 2007-09-19
estas sugiriendo, que la gente de fibertel aparte de hacer packet dropping askerosamente, encima tiene en los backbones velocidades inferiores al ancho de banda total que necesitan para darle el servicio que prometen a sus clientes??!? era lo unico que faltaba! pero para, hablas con conocimiento de causa? salu2!

---

### Post by Mataca on 2007-09-19
Yo tengo fibertel, llamé por la duplicación de ancho de banda y me dijeron que de 2.5 me lo duplican a 3 o sea.... 2.5 + 2.5 = 5 
Así me eseñaron a sumar, quizá me equivoque. Igualmente por mi experiencia puedo decir que Fibertel anda muy bien, trabajo en un ISP hace 6 años ya (telecentro) y la verdad que al ver las demas empresas Fiber anda mejor q muchas.
Abolutamente todos tienen el ancho de banda restringido. De una manera u otra lo restringen. Imaginense todos los usuarios conectados a servidores p2p a la velocidad real, bueno.. como que congestionarian todo..

edd12river Tenes que reclamar, ponete firme, habla en serio y te van a dar bola. Pero no insultes a los que te atienden por que esa gente que está del otro lado que verdaderamente labura, mientras que las cabezas de las empresas les "ordenan" que se manejen así. Ellos no tienen la culpa, al menos no directamente...

Pd. por100pre1 sos un groso, sabelo

---

### Post by FlyerDie on 2007-09-19
> **Mataca said:**
> Yo tengo fibertel, llamé por la duplicación de ancho de banda y me dijeron que de 2.5 me lo duplican a 3 o sea.... 2.5 + 2.5 = 5 
Así me eseñaron a sumar, quizá me equivoque. 

jaja y que explicacion te dieron a que te lo "duplican" a 3mbps?

---

### Post by leo_rockway on 2007-09-19
> **FlyerDie said:**
> jaja y que explicacion te dieron a que te lo "duplican" a 3mbps?

Yo ayer vi el afiche de fibertel con la propaganda de esta promocion y dice "multiplicamos la velocidad". 

a los q tienen 2.5 se lo multiplican por 1.2... son reeeeeeeeebuenos xq si querian te lo multiplicaban por 0.33  o algo asi... :lolflag:

en mi isp cada vez q se cae la conexion es imposible comunicarse con ellos, aca todas las isp son una porqueria!

---

### Post by LaHire on 2007-09-19
> **FlyerDie said:**
> jaja y que explicacion te dieron a que te lo "duplican" a 3mbps?

2+2 =  5 
para valores infinitamente grandes de 2
o porq el Gran Hermano lo dice.-


:guitar:

---

### Post by martincho90 on 2007-09-21
> **edd12river said:**
> una cosa, si el modem arranca, osea prenden las luces y esta para conectar, hay q hacer todo eso?

gracias! desde yaSi hacelo igual.
Aqui tenes otro tutorial: [http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html")
No aflojes, segui intentando hacerlo andar, tiene que andar, eso te va a enseñar mucho de tu equipo.

---

### Post by matogrosso on 2007-09-25
Quiza te ayude:

[http://ubuntuforums.org/showthread.php?t=559395](http://ubuntuforums.org/showthread.php?t=559395)

---

