---
title: "Instalación programas de windows en Ubuntu"
date: 2008-03-13
forum: Argentina Team
---

### Post by malbecar on 2008-03-13
Buenas, perdon si ya se hablo en otro post, pero la verdad que no pude encontrar nada.
Estoy necesitando correr el office 2003 en ubuntu y quizas algunos otros programas de windows, queria saber cual es la mejor forma de hacerlo.

De lo que estuve leyendo en los foros de ingles wine es la alternativa.
Cual recomiendan.
Muchas gracias.

Mariano

---

### Post by sajnox on 2008-03-13
Para correr office la opcion mas simple es usar crossover applications (es pago), si mal no recuerdo podes bajar una version de prueba para ver como anda.

[http://www.codeweavers.com/products/cxoffice/truth_in_advertising/the_real_dirt/](http://www.codeweavers.com/products/cxoffice/truth_in_advertising/the_real_dirt/)

Ahi te deje el link para que puedas ver la pagina del fabricante (Codeweavers)

---

### Post by Apokalyptica79 on 2008-03-13
Hola malbecar el officc tiene algo en particular que no lo puedas hacer usando el openoffice? 
Hasta donde se con el open podés hacer lo que necesites.
Saludos.

---

### Post by pol666 on 2008-03-13
wine no es una alternativa es un camino ....


la alternativa es Open Oficce y eso es lo que recomiendo.

---

### Post by niko_3100 on 2008-03-13
Obvio chabon que es lo que no te gusta de open Oficce no solo es igual hasta lo encuentro mas facil de usar, sino proba Abiword que es re basico pero bue..

---

### Post by guisheca on 2008-03-13
Mirá, si REALMENTE NO TENES ALTERNATIVA y no te queda otra que usar el office de m$, yo te recomiendo el programa "[playonlinux]("http://www.playonlinux.com/es/download.html")" que en un comienzo servía para jugar a juegos de windows en linux, pero ahora ya se pueden instalar varios otros programas como el office 2003, 2000, safari, etc.
En el enlace que te dejo se pueden descargar los paquetes .deb para ubuntu, o bien, se pueden agregar los repositorios a nuestro sources.list.
Después se [descargan los scripts]("http://www.playonlinux.com/es/scripts.html") del programa que quieran instalar (ya sean juegos o utilitarios) y ejecutamos el script mediante playonlinux. Y eso es todo.
Espero haberte ayudado.

---

### Post by malbecar on 2008-03-13
Muchas gracias a todo por contestar. Muy buena velocidad.
Lamentablemente no me queda otra que usar el excel, tengo grandes archivos del trabajo hechos con m excel. Es verdad q podes hacer un monton de cosas con el open office pero el excel a cierto nivel no son iguales, ya me paso con mac.
Y ponerme a reformular formulas y macros es pesado.
En un blog lei justamente el programa que comentas, cuando entre para saber mas del programa ahi vi que estaba basado en wine y de ahi la pregunta.
Este es link:
[http://www.techtear.com/2008/03/13/playonlinux-una-ayuda-para-jugar-juegos-de-windows-en-linux/]("http://www.techtear.com/2008/03/13/playonlinux-una-ayuda-para-jugar-juegos-de-windows-en-linux/")

---

### Post by leo_rockway on 2008-03-13
Q: que vas a hacer si M$ Office 2007 (y ooxml) adquieren popularidad (St. IGNUcius no lo permita!)? Vas a seguir usando una aplicación ofimática de la dácada pasada?

Yo que vos aprovecharía esta oportunidad para actualizar tus archivos y pasarlos a un formato libre que te garantiza que SIEMPRE vas a poder abrirlos.

---

### Post by malbecar on 2008-03-13
Es un buen punto el q mencionas leo_rockway, pero lamentablemente no depende de mi, sino de mi trabajo.

Sin embargo voy a tratar de pasar todo mis archivos que tenga y voy posteando que problemas me saltan.

Mientras playonlinux es la mejor opcion entonces?

---

### Post by leo_rockway on 2008-03-13
La opción que mejor funciona para M$ Office 2003 es, como bien dijo sajnox, Crossover Office.

---

### Post by malbecar on 2008-03-13
Ok, pero en este mundo libre no voy a usar un soft que haya q pagar. Muchas gracias.

---

### Post by niko_3100 on 2008-03-13
Noooooo con playonlinux se puede jugar al Sonic Adventure DX, yaaaaa llego del laburo y me lo pongo a bajar!!!! BUAAAAAAAA!!!!!!!!11

---

### Post by facundocorradini on 2008-03-13
no sé si lo dijiste en joda o no, pero tus palabras... 

> Ok, pero en este mundo libre no voy a usar un soft que haya q pagar. Muchas gracias. 

Me han hecho morir de risa. Estamos hablando de instalar office, un programa de USD 700... y te quejas de Crossover???? 


----------------------------
Por cierto, si sos de los que usan software comercial sin pagarlo, seguramente intuirás que podés hacer lo mismo con crossover.. no?
....................................

Por cierto 2, no termino de entender pq necesitas si o si office 2003. 

Open Office trabaja muy bien con ese formato de archivo, si es lo que te preocupa.

---

### Post by leo_rockway on 2008-03-13
> **malbecar said:**
> Ok, pero en este mundo libre no voy a usar un soft que haya q pagar. Muchas gracias.

libre != gratuito

---

### Post by leo_rockway on 2008-03-13
> **niko_3100 said:**
> Noooooo con playonlinux se puede jugar al Sonic Adventure DX, yaaaaa llego del laburo y me lo pongo a bajar!!!! BUAAAAAAAA!!!!!!!!11

<double post>
<thread hijacking>
Eso significa que ya podes formatear esa fea particion NFTS?
</thread hijacking>
</double post>

---

### Post by sajnox on 2008-03-13
PLAYONLINUX!!!!!! Es cierto!!! me olvide que trae opcion para ms office, hoy lo pruebo y les cuento.

Mis disculpas por el olvido....

---

### Post by h9005 on 2008-03-13
Si vous êtes sous une distribution debian-based, vous pouvez utiliser le dépot PlayOnLinux comme ceci : Entrez ces commandes dans un terminal

sudo wget [http://playonlinux.botux.net/playonlinux.list](http://playonlinux.botux.net/playonlinux.list) -O /etc/apt/sources.list.d/playonlinux.list

sudo apt-get update
sudo apt-get install playonlinux

Ou bien ajoutez à votre sources.list:

deb [http://playonlinux.botux.net/](http://playonlinux.botux.net/) gutsy main

No entiendo cual de los dos códigos son los que tengo que poner en los link de repositorio.

---

### Post by h9005 on 2008-03-13
Ah y no tengo la más pálida idea de que son los scripts.

---

### Post by sajnox on 2008-03-13
> **h9005 said:**
> Si vous êtes sous une distribution debian-based, vous pouvez utiliser le dépot PlayOnLinux comme ceci : Entrez ces commandes dans un terminal

sudo wget [http://playonlinux.botux.net/playonlinux.list](http://playonlinux.botux.net/playonlinux.list) -O /etc/apt/sources.list.d/playonlinux.list

sudo apt-get update
sudo apt-get install playonlinux

Ou bien ajoutez à votre sources.list:

deb [http://playonlinux.botux.net/](http://playonlinux.botux.net/) gutsy main

No entiendo cual de los dos códigos son los que tengo que poner en los link de repositorio.

Si bien Frances no entiendo, lo que te esta dando son dos opciones.

1) Agregar en forma automatica los repositorios de playonlinux
2) Agregar una linea en tu archivo sources.list (datos de todos los repositorios que tenes instalados)

apt-get update es para actualizar la lista de repositorios
apt-get install para instalar un programa

Espero te sirva

---

### Post by malbecar on 2008-03-14
> **facundocorradini said:**
> no sé si lo dijiste en joda o no, pero tus palabras... 



Me han hecho morir de risa. Estamos hablando de instalar office, un programa de USD 700... y te quejas de Crossover???? 


----------------------------
Por cierto, si sos de los que usan software comercial sin pagarlo, seguramente intuirás que podés hacer lo mismo con crossover.. no?
....................................

Por cierto 2, no termino de entender pq necesitas si o si office 2003. 

Open Office trabaja muy bien con ese formato de archivo, si es lo que te preocupa.

Justamente es por eso que no quiero pagar o bajar algun software pago por alguna red como emule o torrent. Para eso me quedo en el mundo windows jajaja.
De todas formas,  la licencia la tengo por le trabajo, por lo que no es un problema :D

Seguramente este probando playlinux el finde.
Saludos!

---

### Post by niko_3100 on 2008-03-14
> **leo_rockway said:**
> <double post>
<thread hijacking>
Eso significa que ya podes formatear esa fea particion NFTS?
</thread hijacking>
</double post>

Ojalaaa pero tambien tengo el sonic heroes jeje y encima la lexmark que tengo no hace nada en linnux no la pude instalar... :(

---

### Post by guisheca on 2008-03-14
Los scripts hay que guardarlos en modo texto y darle permisos de ejecución, después desde playonlinux se elige: ejecutar script no oficial, y elegir el scritp que bajamos.
Si tengo tiempo me hago un tuto sobre el tema.

---

### Post by malbecar on 2008-03-14
Muchachos les dejo un post de lifehacker que publicaron hoy sobre otra alternativa para correr aplicaciones de windows. Esta alternativa consiste en instalar windows en una virtual box. Es algo muy diferent a lo que veniamos hablando pero quizas alguno le sirva. Me parecio muy interesante. Y justo salió publicado hoy.
link
[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux")

Saludos!

---

### Post by sajnox on 2008-03-14
Malbecar,

La virtualizacion es la peor de todas las soluciones, por varios motivos

1) Aun estando virtualizada la maquina tenes que pagar una licencia de windows (aunque para muchos esto no sea un problema)
2) Para usar una maquina virtual con windows, me quedo con windows
3) Los programas sobre la maquina virtual corren mas lentos, ya que la maquina virtual es un programa corriendo sobre el SO

Y debe haber muchos motivos mas que desconozco

PD: Para los no avanzados como yo instalar una maquina virtual y tener dos SO corriendo nos hace sentir un hacker de primera, por lo que te invito a que lo pruebes. Eso si, abri un post nuevo sobre el tema para preguntar y antes de preguntar busca en el foro por que de esto se hablo un monton de veces

Saludos,

---

### Post by malbecar on 2008-03-14
> **sajnox said:**
> Malbecar,

La virtualizacion es la peor de todas las soluciones, por varios motivos

1) Aun estando virtualizada la maquina tenes que pagar una licencia de windows (aunque para muchos esto no sea un problema)
2) Para usar una maquina virtual con windows, me quedo con windows
3) Los programas sobre la maquina virtual corren mas lentos, ya que la maquina virtual es un programa corriendo sobre el SO

Y debe haber muchos motivos mas que desconozco

PD: Para los no avanzados como yo instalar una maquina virtual y tener dos SO corriendo nos hace sentir un hacker de primera, por lo que te invito a que lo pruebes. Eso si, abri un post nuevo sobre el tema para preguntar y antes de preguntar busca en el foro por que de esto se hablo un monton de veces

Saludos,

Toda la razon. Por eso aclare que era otra alternativa. Vi varios post sobre esto, pero me parecio interesante que justo lo comentaran en este blog q leo casi todos los dias.

Mi alternativa sigue siendo playonlinux que fue la que habia encontrado en otro blog,y fue el motivo de inicio de este post,
Espero poder probarla este finde en casa junto a otras cosas que estuve leyendo esta semana.

---

