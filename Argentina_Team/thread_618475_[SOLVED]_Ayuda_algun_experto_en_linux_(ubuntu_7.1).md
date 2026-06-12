---
title: "[SOLVED] Ayuda: algun experto en linux (ubuntu 7.1)"
date: 2007-11-20
forum: Argentina Team
---

### Post by juani on 2007-11-20
Hola me instale el linux ubuntu 7.10 el fin de semana.si,,, no hay otra forma de decirlo soy un terrible newbie :P,
weno estuve revisando varios foros, pero todas las explicaciones son para gente un poco mas avanzada q yo en el tema. y yo tengo varias preguntas q me resulta muy incomodo postear : $

we les dejo mi msn para los q me kieran ayudar

desde ya gracias =]

ps. rapido q me pongo nervioso:(

---

### Post by sajnox on 2007-11-20
Hola Juani,

Bienvenido!!! 

Te comento que te edite el post por que el tamaño de la letra y el color solo lo usamos para resaltar alguna parte especifica del texto, no todo.

Estoy seguro que aca somos varios los que te vamos a dar una mano respecto a Ubuntu, pregunta sin problemas!!!

Para hacerte la entrada un poco mas facil te aconsejo que te de una vuelta por la guia ubuntu [www.guia-ubuntu.org](www.guia-ubuntu.org) Ahi encontraras mucho material respecto a Ubuntu partiendo desde lo mas basico

Y tranquilo.... no te pongas ansioso que no ayuda.

Bueno, contanos que dudas tenes y vemos en que podemos ayudarte

---

### Post by Mafber on 2007-11-20
Hola Juani!! Podes preguntar sin miedo ¿acaso vos pensás que todos nacimos sabiendo linux? pregunta que no molesta, probablemente otras personas tengan tus mismas inquietudes.

---

### Post by juani on 2007-11-20
Muchas gracias! : D 

me olvide de poner el mail xd
 [email]j_badano@hotmail.com[/email]

weno voy a revisar la guia q me paso sajnox, pero mientras tanto les dejo mis inquietudes mas urgentes:

-necesito compartir internet de mi linux a una pc con windows xp 
pero no se compilar y casi no tengo idea de los comandos de la terminal
-necesito un programa para bajar musica tipo ares, pero q no baje tan lento como el emule
-y x ultimo q alguien me esplique como optimizar mi placa de video ati radeon 9250 128mb

weno eso x ahora xd

---

### Post by juani on 2007-11-20
me olvidaba de una cosa!! 

a veces me suena el speaker (x ejemplo cuando termino de borrar y vuelvo a tocar el backspace)
no se si hay algun driver para mi placa de sonido onboard via 8237
y ademas bajo el volumen y solo me baja el volumen de los altavoces principales y no del surround osea si pongo mute con el teclado los parlantes traseros siguen funcionando

listooo ; D

---

### Post by Mafber on 2007-11-20
Hola, Sobre el Ares, mirá esta paginas que esplican como instalarlo y como solucionar los problemas que te pueden suceder:
[http://www.ubuntu-es.org/index.php?q=node/48194](http://www.ubuntu-es.org/index.php?q=node/48194)
[http://kubuntu-chile.blogspot.com/2007/03/ares-en-ubuntu.html](http://kubuntu-chile.blogspot.com/2007/03/ares-en-ubuntu.html)
creo haber vista un ares que es para ubuntu pero no estoy seguro. si lo encuentro lo posteo.

---

### Post by User21 on 2007-11-20
Si queres desprenderte del yugo Micro$oft, en lugar de usar Ares, podrias usar una alternativa libre como [FrostWire]("http://www.frostwire.com/") . para instalarlo solo haz clic en el gigantesco boton que dice "[Download Now]("http://www.frostwire.com/download/?os=ubuntu")". Yo lo uso desde hace un tiempito, aunque soy mas amigo de la descarga directa..! De todas formas, este programa, a mi gusto y experiencia, es una MUY BUENA ALTERNATIVA! Suerte con el....
NOTA: requiere JAVA en tu Ubuntu.

---

### Post by leo_rockway on 2007-11-20
> **User21 said:**
> Si queres desprenderte del yugo Micro$oft, en lugar de usar Ares, podrias usar una alternativa libre como [FrostWire]("http://www.frostwire.com/") . para instalarlo solo haz clic en el gigantesco boton que dice "[Download Now]("http://www.frostwire.com/download/?os=ubuntu")". 

frostwire esta en los repos.

EDIT: y agrego lo siguiente: para la red ares se puede usar gift con giftoxic o con apollon.

---

### Post by sajnox on 2007-11-20
Para sacarle el jugo a tu placa ati, te recomiendo que instales el driver con Envy.

Envy lo podes bajar de [ACA]("http://www.albertomilone.com/nvidia_scripts1.html")

Y el archivo que tenes que bajar es envy_0.9.8-0ubuntu13_all.deb

Seguramente lo descargue en tu carpeta home, con el navegador haces doble click y te lo agrega en Aplicaciones/Herramientas del sistema

---

### Post by ubuntu27 on 2007-11-22
> **User21 said:**
> Si queres desprenderte del yugo Micro$oft, en lugar de usar Ares, podrias usar una alternativa libre como [FrostWire]("http://www.frostwire.com/") .



Yeah, aunque Ares Galaxy (conocido mas como Ares)  es OpenSoruce, solo esta dinsenyado para el Sistema Operativo Windows (y nadies quiere portar a otra plataforma) >< 

Yo tambien recomiendo FrostWire. Para mi es uno de los pejores p2p.

@juani: Para isntalar FrostWire, primero isntala Java de Sun. Esta en el repositorio. 

Abre el terminal que se encuentra en el menu Aplicaciones/Accesorios/Terminal

y escribe lo siguiente (o solo copia y pega)
```
sudo apt-get install ubuntu-restricted-extras
```

ese codigo es para bajar y instalar formatos restrictivos tales como MP3,  Flash, Quicktime, WMA and WMV, Java, etc.  

Ahora que has instalado Java, puedes instalar FrostWire. Yo estoy usando Debian, asi que no se si Ubuntu 7.10 lo tiene en su repo o no. 

```
sudo apt-get install frostwire
```  

Lograste instalar FrostWire con ese comando? no? Ok, entonces no esta en el repositorios, asi que anda a la pagina oficial de FrostWire.

[http://www.frostwire.com/](http://www.frostwire.com/)

click en Download Now. y bajate el archivo deb   (es algo parecido a exe de windows, pero para Debian y Ubuntu)

doble click en el deb, y listo! :D

---

### Post by leo_rockway on 2007-11-23
> **ubuntu27 said:**
> 

```
sudo apt-get install frostwire
```  

Lograste instalar FrostWire con ese comando? no? Ok, entonces no esta en el repositorios

```
$ apt-cache search frostwire
frostwire - A Truly Free and Open Source Peer to Peer client

```

---

### Post by juani on 2007-11-23
la verda q me costo pero ya instale el frostwire y se conecta :P
gracias muchachos ;D

el envy no es compatible con mi hardware, instale manualmente pero no me lo tomo, asik volvi a instalar los libres, igual me dijieron q los libres de mi placa (ati radeon 9250) son bastante buenos asik eso no lo cambio. lo q necesesito son algunos tips para mejorar el rendimiento tanto de la placa como de la pc en general, como en window$ el msconfig para configurar las aplicaciones y servicios q se inician al logear, o algunas opciones q quitan mucho rendimiento a la pc para q desactive.
weno en fin tirenme sus settings xd
mis fps actuales son entre 700-750

compartir internet no pude, igual no importa x q ya me compre un router, gracias igual : D

weno si tengo alguna otra duda la posteo aca : )

gracias a todos

---

### Post by ubuntu27 on 2007-11-23
> **juani said:**
> 
weno si tengo alguna otra duda la posteo aca : )

gracias a todos

Yeah, si encuentras algun problema, postea en el Foro. 
Pero, debes de crear UN THREAD por cada problema o diferente asunto. Si continuas preguntando en este mismo thread, la gente no necesariamente va a visitarlo, ya que van a creer que el problema que tenias (de tu primer post) ya fue solucionado.


Otra cosa mas. :)  Cuando el problema que tenias ha sido solucionado marca tu thread como "Solved" (Solucionado) Asi la gente sabra que el problema o pregunta ha sido resuelto.  Tambien Sirve para que la gente que busca algun la solucion de algun problema, vea que tu thread tiene alguna solucion que podra ayudarle. :) 

[Como marcar el thread como "Solucionado"]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Bueno, bienvenido a Ubuntu! :guitar: Junto vamos a rockear ^^

---

### Post by sajnox on 2007-11-23
> **leo_rockway said:**
> ```
$ apt-cache search frostwire
frostwire - A Truly Free and Open Source Peer to Peer client

```

Leo,

Que repo me estoy comiendo?? No tengo frostwire
```

miguel@miguel-desktop:~$ sudo apt-cache search frostwire
miguel@miguel-desktop:~$ 
```

---

### Post by Hernán-Amaya on 2007-11-23
por el tema de la optimización de tu placa entra [acá]("http://nadock.wordpress.com/2007/08/08/como-optimizar-el-rendimiento-de-una-ati-radeon-92009250-en-ubuntu-gnulinux/"), yo duplique los fps con estos consejos, espero que te sirva!

para optimizar tu pc en su momento había algo en la [www.guia-ubuntu.org](www.guia-ubuntu.org) 
y si no habrá que googlear un rato seguramente encontraras algo interesante

suerte!

pd: contanos como te fue

---

### Post by santiagoward2000 on 2007-11-23
> **sajnox said:**
> Leo,

Que repo me estoy comiendo?? No tengo frostwire
```

miguel@miguel-desktop:~$ sudo apt-cache search frostwire
miguel@miguel-desktop:~$ 
```

A mí también me aparece como a Leo, ¿pero no será porque ya está instalado? Yo instalé el mío con el .deb de [www.frostwire.com]("www.frostwire.com")

Saludos!

---

### Post by sajnox on 2007-11-23
Seguro que es por eso, yo tambien recien lo instale con el deb de la pagina

---

### Post by leo_rockway on 2007-11-24
> **sajnox said:**
> Seguro que es por eso, yo tambien recien lo instale con el deb de la pagina

puede ser que sea eso... yo ya ni me acuerdo como instale frostwire en su momento, jaja

---

### Post by ubuntu27 on 2007-11-24
los programas instalados con *.deb son automaticamente agregados a la lista de programas disponibles in Synaptic. De esta manera da facilidad de desinstalacion. :)

---

