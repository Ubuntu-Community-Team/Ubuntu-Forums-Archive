---
title: "Ayuda con Archivos tar.gz"
date: 2007-10-09
forum: Argentina Team
---

### Post by pablo0469 on 2007-10-09
Hola, gente, he leido unas cuantas formas de instalar archivos .tar.gz (todas en ubuntu-es.org), pero no hay caso. Por favor, si alguien con mas experiencia me aclara este punto, voy a estar mas que agradecido. Saludos.

---

### Post by scrooge_74 on 2007-10-09
Pero los archivos tar sólo son comprimidos.  Ubuntu te los abre por default, pones los directorios donde los quieres y luego trabajas con lo que tienes dentro.

Vas a compilar algo?

---

### Post by sajnox on 2007-10-09
Pablo,

Entiendo que bajaste un archivo y queres instalarlo en tu maquina.

Primer consejo: buscaste en los repositorios el programa que queres bajar?? (Sino sabes que son los repositorios [ACA]("http://es.tldp.org/Manuales-LuCAS/doc-guia-ubuntu-breeze/guia-ubuntu-htmls/repositorios.html") te dejo un link) Si esta en el repositorio es mejor instalarlo de ahi.

Para saber si esta en el repositorio

```
 $ sudo apt-cache search NOMBRE DEL PROGRAMA QUE BUSCAS
```

Si esta y para instalarlo

```
 $ sudo apt-get install NOMBRE DEL PROGRAMA
```

Si no esta en el repositorio lo mejor es ayudarte con el comando alien (no viene instalado por defecto en Ubuntu), para instalarlo:

```
 $ sudo apt-get install alien
```

Una vez que lo instalo haces lo siguiente

```
 $ alien NOMBRE DEL ARCHIVO TAR.GZ
```

Asegurate de que estas ejecutando alien en el directorio donde esta el tar.gz

Esto que hiciste te creara un archivo.deb (empaquetado para ubuntu), haces doble click sobre el archivo y te lo instala.

Espero te sirva, cualquier cosa postea como va

Saludos

---

### Post by facundocorradini on 2007-10-09
También puedes hacerlo de modo gráfico, sin recurrir a la consola:

abres el gestor de paquetes sinaptic, desde allí poner a buscar el nombre del paquete,  y si lo encuentra, solo le dás doble click, luego el boton aplicar y listo.


Si recién empiesas en linux, te recomiendo que siempre instales los programas desde los repositorios oficiales, de ser imposible, busca en repositorios de terceros, y sino busca archivos .deb.   
Compilar el código fuente puede ser medio complicado...

saludos

---

### Post by pablo0469 on 2007-10-09
Estoy tratando de instalar el tema Elegance Metacity 2, que baje de Gnome Look en un archivo elegance_metacity2.tar.gz. 

Hara como 5 meses que uso Ubuntu, pero no dispongo de mucho tiempo y voy aprendiendo de a poco, asi que aun me considero medio novato... pero aun a paso de hormiga las cosas mas basicas ya las sé.

Gracias a todos. Un abrazo.

---

### Post by facundocorradini on 2007-10-09
aaaaaaaaaaaaaaaaahhh

Entonces lo que tienes que hacer es ir a Sistema --> prerencias --> temas. 
Allí cliqueas instalar y seleccionas el archivo tar.gz (sin descomprimirlo ni nada).

---

### Post by sajnox on 2007-10-09
Hubieras empezado por ahi......

Abris la ventana que facundo menciona mas arriba y hasta podes arrastrar el archivo a la ventana, asi solito noma' te lo instala

---

### Post by manzuk on 2007-10-09
**UPDATE :: Posté tarde. Es lo que dicen los chicos arriba.**


Pablo, lo que tenes que hacer es lo siguiente:

**Menu Ubuntu > Sistema > Preferencias > Tema**

Se abrirá una ventana llamada "*_Preferencias del tema_*".

Ahora **arrastra** el archivo que bajaste de Gnome-Look (elegance_metacity2.tar.gz) y soltalo dentro de la ventana *_"Preferencias del tema_*". Deberías obtener un mensaje confirmándote que el tema se instaló correctamente.

Para utilizar Elegance, _elegí un tema cualquiera_ de la lista (por ejemplo "Human"), y presioná el botón "***Personalizar***" que se encuentra del lado derecho de la ventana "*_Preferencias del tema_*".

Se abrirá una ventana llamada "_*Detalles del tema*_". En la solapa "_Controles_" seleccioná de la lista la opción "***Elegance***". Hace lo mismo en la solapa "_Borde de la ventana_".

Esto debería funcionar.
Para que todo quede más bonito tendrías que encontrar unos iconos que peguen bien con el tema.

Saludos!

---

### Post by pablo0469 on 2007-10-09
Esto ultimo es lo que hice, cambie el criterio de busqueda en google (instalar nuevo tema ubuntu), y no sabia que era tan simple como arrastrar el archivo hacia la ventana de "Preferencias de Tema"...

Disculpen por no haber aclarado de antemano de que se trataba, pasa que hoy ando medio zombie.

Muchas Gracias a todos.

PD: igual despues voy a seguir investigando como se instalan aplicaciones .tar.gz o .tgz

---

### Post by lavaramano on 2007-10-10
te queda esa o:

$ cp tema.tgz ~/.themes
$ cd ~/.themes
$ tar xf tema.tgz

y despues desde Menu Ubuntu > Sistema > Preferencias > Tema, lo elegis.
ambas son validas.

---

### Post by Mataca on 2007-10-12
> **sajnox said:**
> 
Asegurate de que estas ejecutando alien en el directorio donde esta el tar.gz

Esto que hiciste te creara un archivo.deb (empaquetado para ubuntu), haces doble click sobre el archivo y te lo instala.

Saludos


Faaaa ni sabia que existía esto! yo me la pasaba con ./configure, make, install
Así es mas facilito no? lo voy a probar en cuanto llegue a casa =)

---

