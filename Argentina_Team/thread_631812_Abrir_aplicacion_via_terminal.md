---
title: "Abrir aplicacion via terminal"
date: 2007-12-04
forum: Argentina Team
---

### Post by benzema on 2007-12-04
Oigan hace rato que no uso ubuntu y la verdad no recuerdo como era,abajo redacto el inconveniente:

Me baje una aplicacion para ubuntu (7.10) es un zip lo descomprimo hasta ahi bien despues cuando la voy a abrir le ago doble click y no pasa nada , abro la terminal pero no se como es el comando para abrir la aplicacion,pesa 1 mb no se instala ni nada solamente se abre y se usa ,saludos

---

### Post by marianom on 2007-12-04
Muy posiblemente te falte instalar el zip (no viene por defecto).

Desde una consola:
```
sudo apt-get install zip unzip
```

No estoy seguro que sean 2 programas separados y/o que no se instalen juntos pero bueno, vemos.

Luego de eso podes intentar por consola
```
unzip miarchivo.zip
```

---

### Post by benzema on 2007-12-05
> **marianom said:**
> Muy posiblemente te falte instalar el zip (no viene por defecto).

Desde una consola:
```
sudo apt-get install zip unzip
```

No estoy seguro que sean 2 programas separados y/o que no se instalen juntos pero bueno, vemos.

Luego de eso podes intentar por consola
```
unzip miarchivo.zip
```

Creo que no me supe explicar bien,pero ire mejorando con el tiempo,tengo todos los formatos de compresion rar,zip,etc, mi problema es que no se abrir los programas,osea bajo un programa que viene en un zip,lo descomprimo,veo todas las carpetas y todos los archivos (aca el problema) no se abrir los ejecutables porqe no se abren con doble click,capaz que ahora entendes un poco mejor la pregunta , Saludos

Te dejo una screen para ser mas claro  


[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1706960Pantallazo.png[/IMG]

Aclaracion:[http://s1.subirimagenes.com/imagenes/previo/thump_1706960Pantallazo.png](http://s1.subirimagenes.com/imagenes/previo/thump_1706960Pantallazo.png)

---

### Post by facundocorradini on 2007-12-05
Lo más probable si tenés un zip es que hayas bajado el código fuente del programa. Tendrías que compilarlo. 


Igualmente, compilar debería ser la última opción para un usuario "comun". 

Lo recomendable es que **siempre** busques primero si la aplicación que te interesa está en los repositorios (con añadir/quitar o sinaptic), ya que te permite tener la versión optimizada para tu ubuntu, y actualizar automáticamente el programa.

Si no está en los repos, podrías buscar un archivo .deb (ejecutable con doble click, un aceptar y listo). Podés buscar por ejemplo en [getdeb]("http://www.getdeb.net/")

Y en ultima instancia, compilar el código fuente. 


Que programa es el que querés instalar?

---

### Post by marianom on 2007-12-05
No llego a ver nada en ese printscreen pero más allá de eso, si tenes el zip instalado y en funcionamiento, si haces
```
unzip miarchivo.zip
```
por consola, debería descomprimirlo o darte un error que nos permita diagnosticar el problema que tenés

---

### Post by Alejandro Vidal on 2007-12-05
No se bien de qué archivo o programa se trata, pero si ya esta compilado deberías poder ejecutarlos con ./programa dentro del directorio en el que se encuentra el programa.
Saludos.

---

### Post by marianom on 2007-12-05
Lo que pasa es que todavía no lo puede descomprimir como para ejecutarlo.

---

### Post by benzema on 2007-12-05
> **marianom said:**
> Lo que pasa es que todavía no lo puede descomprimir como para ejecutarlo.


Miren es el quake 3 ya lo instale y todo pero ahora lo tengo que abrir voy a la carpeta donde esta instalado pero al hacerle doble click no abre ,se que hay muchos archivos que se abre por terminal pero no se como de ahi viene este post
Saludos

Dejo una screen en la carpeta donde esta lo que quiero

[IMG]http://www.subirimagen.es/07/1205/7572/Pantallazo.png[/IMG]

Referencia:[http://www.subirimagen.es/07/1205/7572/Pantallazo.png](http://www.subirimagen.es/07/1205/7572/Pantallazo.png)

---

### Post by marianom on 2007-12-05
Uhhhhh que mal que leí de entrada. Y seguí insistiendo con lo mismo. Mucha vergüenza (no hay emoticón que me represente).

---

### Post by Hernán-Amaya on 2007-12-05
para cambiar de directorio en la terminal usas el comando cd

entonces abrí la terminal y escribí  
```

cd /usr/local/games/quake3/baseq3

```

ahora para ejecutar cualquiera de los tres archivos que tenés en ese directorio simplemente escribí el nombre del archivo y listo!

suerte!

---

### Post by benzema on 2007-12-05
> **Hernán-Amaya said:**
> para cambiar de directorio en la terminal usas el comando cd

entonces abrí la terminal y escribí  
```

cd /usr/local/games/quake3/baseq3

```

ahora para ejecutar cualquiera de los tres archivos que tenés en ese directorio simplemente escribí el nombre del archivo y listo!

suerte!

Buena,igual no me anda seguro que instale mal algo pero en la consoola me tiro el error del juego es un gran paso saludos y gracias

---

### Post by Hernán-Amaya on 2007-12-05
postea el error tal vez en el foro haya algún gamer que te pueda dar una mano

---

### Post by facundocorradini on 2007-12-05
De ultima, instalate por synaptic el OpenArena, es un clon de Q3 que está barbaro.

---

### Post by benzema on 2007-12-05
> **facundocorradini said:**
> De ultima, instalate por synaptic el OpenArena, es un clon de Q3 que está barbaro.

Recien termino de instalarlo al OpenArena y si esta muy bueno,ya lo conocia de cuando tenia windows pero no sabia que estaba para linux tmb y menos que estaba en synaptic, de haberlo sabido antes hubiera bajado esos 70 mb antes que los 600 del Q3A , Gracias x todo

Edit: Algun otro juego copado para ubuntu  ?

---

### Post by Hei Ku on 2007-12-05
Pregunta tonta, le diste permisos de ejecucion al archivo, no?
Porque mencionaste que lo descomprimiste, pero no que le hayas cambiado el permiso de ejecución, y puede ser eso, porque en linux ningun archivo se puede ejecutar salvo q lo autorices explicitamente.

sudo chmod +x <nombre del archivo>

---

### Post by kowal on 2007-12-06
> **benzema said:**
> Recien termino de instalarlo al OpenArena y si esta muy bueno,ya lo conocia de cuando tenia windows pero no sabia que estaba para linux tmb y menos que estaba en synaptic, de haberlo sabido antes hubiera bajado esos 70 mb antes que los 600 del Q3A , Gracias x todo

Edit: Algun otro juego copado para ubuntu  ?

[http://www.ubuntugames.org/en/UbuntuGames](http://www.ubuntugames.org/en/UbuntuGames)
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by facundocorradini on 2007-12-06
> Edit: Algun otro juego copado para ubuntu ?

Decime que tipo de juego te interesa. Juegos "para ubuntu" hay muchísimos...

---

### Post by vk-cdg on 2007-12-06
Estuve viendo y hay dos o tres FPS que son mis preferidos. El fin de semana que viene los bajo (este no ya que me faltan solo dos finales para recibirme y me parece que si los bajo este fin de semana hago macanas)

Si saben de algún FPS mas chiflen!

---

### Post by marianom on 2007-12-06
> **vk-cdg said:**
> me faltan solo dos finales para recibirme

Vaya para vos mi sana envidia y toda la suerte para que termines la carrera con éxito.

---

### Post by vk-cdg on 2007-12-06
Muchas gracias.
Esperemos que la asunción del nuevo gobierno me deje poder rendir los finales en paz!

---

### Post by facundocorradini on 2007-12-06
FPSs q conozco para ubuntu:

- OpenArena, clon de Quake 3.  (en los repos)

- Tremulous, fps online humanos contra aliens muy viciante. (en los repos)

- Enemy Territory, juego de la segunda guerra. Muy jugado, pero para mi gusto es demasiado rapido e ireal. (bajar .run de la web)

- True Combat Elite: uno de mis favoritos de todos los tiempos. MOD de Enemy Territory, terroristas contra fuerzas especiales.  super-realista, al punto que se debe apuntar con la mira del arma (se pone "el ojo en la mira" con un boton), casi siempre una o dos balas te matan, etc etc... 

- America's army: Segun dice, uno de los mejores fps de la historia. Online, gratuito. Pesa como dos o tres gigas que hay que bajar de internet...

---

