---
title: "[SOLVED] Espacio libre en disco"
date: 2007-08-31
forum: Argentina Team
---

### Post by Vero1 on 2007-08-31
Hola buenos días,

Tengo Ubuntu Feisty 7.04.

Quisiera saber cómo puedo ver el espacio que me queda libre en el disco.

gracias y saludos:)

---

### Post by por100pre1 on 2007-08-31
```
df
```

O instala Baobab (conocido como **Analizador de uso de disco**):

```
sudo apt-get install gnome-utils
```

---

### Post by Vero1 on 2007-08-31
Hola por100pre1,

Estoy un poco confundida. El comando df me tira el siguiente resultado:

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hda1              4806936   2565408   1997340  57% /
varrun                  257824       112    257712   1% /var/run
varlock                 257824         0    257824   0% /var/lock
procbususb              257824       112    257712   1% /proc/bus/usb
udev                    257824       112    257712   1% /dev
devshm                  257824         0    257824   0% /dev/shm
lrm                     257824     33788    224036  14% /lib/modules/2.6.20-16-generic/volatile

El resultado que debo tener en cuenta es dev/hda1? Porque dice que hay disponibles, creo casi 20 Gb. o sea me quedarían 57% de espacio libre?

gracias
El disco tiene una capacidad de 40(o casi).

---

### Post by por100pre1 on 2007-08-31
La respuesta es si.

Disculpa, olvide el parametro h (para lectura **h**umana):

```
df -h
```

---

### Post by kowal on 2007-08-31
Si vas a usar df.. es recomendable **df -h**  (*Human readable*: para que lo puedan leer los** H**umanos ;) )

Sino Filelight o Baobab son muy útiles (y gráficos)

---

### Post by gnusci on 2007-08-31
Tambien puedes usar:

**$ du -hs**

Con eso te da el total de espacio ocupado....

---

### Post by Vero1 on 2007-08-31
> **por100pre1 said:**
> La respuesta es si.

Disculpa, olvide el parametro h (para lectura **h**umana):

```
df -h
```

Lectura humana????? No entiendo. La otra lectura no es para humanos?:)

---

### Post by Vero1 on 2007-08-31
> **kowal said:**
> Si vas a usar df.. es recomendable **df -h**  (*Human readable*: para que lo puedan leer los** H**umanos ;) )

Sino Filelight o Baobab son muy útiles (y gráficos)

gracias kowal.
Baobab está instalado por defecto o hay que instalarlo?
Si es lo último, de dónde?

gracias y saludos:)

---

### Post by Vero1 on 2007-08-31
> **gnusci said:**
> Tambien puedes usar:

**$ du -hs**

Con eso te da el total de espacio ocupado....

Hola,

Me contesta 39M?????

No puede ser...

saludos

---

### Post by Vero1 on 2007-08-31
> **por100pre1 said:**
> ```
df
```

O instala Baobab (conocido como **Analizador de uso de disco**):

```
sudo apt-get install gnome-utils
```

Perdón, ya usé el Analizador pero es bastante confuso...

---

### Post by Vero1 on 2007-08-31
> **Vero1 said:**
> gracias kowal.
Baobab está instalado por defecto o hay que instalarlo?
Si es lo último, de dónde?

gracias y saludos:)

Hacé caso omiso de mi pregunta, pues ya utilicé el Analizador.

Gracias

---

### Post by por100pre1 on 2007-08-31
> **Vero1 said:**
> Lectura humana????? No entiendo. La otra lectura no es para humanos?:)

Significa mas facil de entender a simple vista, en pocas palabras.

---

### Post by Vero1 on 2007-08-31
Está bien, gracias. Traté de hacer un chiste.

saludos:popcorn:

---

### Post by Hei Ku on 2007-08-31
En realidad, el otro formato es mas facil de parsear para los programas, por eso la diferencia.
Por ejemplo, para que lo utilice el conky, o los plugins de superkaramba. Seria mas bien un format -p **P**rogram readable.

---

### Post by Vero1 on 2007-08-31
Hola Hei Ku,

Qué son conky y supercaramba?

saludos

---

### Post by por100pre1 on 2007-08-31
Superkaramba es un administrador de "screenlets" (programitas para poner cositas como clima, reloj, monitores de sistema, etc) al estilo de Windows Vista. Conky es un monitor de systema muy popular entre usuarios experimentados de Linux. [Aqui]("http://ubuntuforums.org/showthread.php?t=482328") deje una imagen y datos de configuracion que puedes utilizar. Busca el post #70. :)

---

### Post by Vero1 on 2007-09-01
Gracias por la info por100pre1,

Te pregunto: sirve para Ubuntu Feisty 7.04? Porque he leído algo en Google y habla sobre KDE(que no sé qué es). Si es el escritorio, yo tengo GNOME. Servirá para mi?

Gracias y saludos:)

---

### Post by Vero1 on 2007-09-01
> **Vero1 said:**
> Gracias por la info por100pre1,

Te pregunto: sirve para Ubuntu Feisty 7.04? Porque he leído algo en Google y habla sobre KDE(que no sé qué es). Si es el escritorio, yo tengo GNOME. Servirá para mi?

Gracias y saludos:)

Disculpá, me olvidé de decir que hablo de Superkaramba:)

---

### Post by Ptero-4 on 2007-09-01
Vero1. KDE es un escritorio, es muy parecido a Ruindoze en cuanto a su configuración inicial y a la filosofía de diseño de sus fabricantes, pero es bastante configurable.

Oops lo olvide. Puedes instalar KDE usando 
```
sudo aptitude install kde-core
``` o 
```
sudo aptitude install kubuntu-desktop
```
dependiendo de si buscas solo el escritorio en si o si quieres instalar sus programas añadidos de golpe.
Una vez instalado puedes alternar entre los dos escritorios desde la pantalla donde pones tu nombre y contraseña.

---

### Post by Hei Ku on 2007-09-01
Sirve para el Kubuntu, que viene con KDE por defecto. El Ubuntu, que tiene Gnome, creo que tiene los gdesklets, o algo así.

---

### Post by por100pre1 on 2007-09-01
> **Vero1 said:**
> Disculpá, me olvidé de decir que hablo de Superkaramba:)

Puede funcionar sin problemas, pero si usas GNOME te conviene mejor usar gdesklets que hace lo mismo pero usando las librerias de GNOME. Superkaramba usa las librerias de KDE. :)

---

### Post by rretamar on 2007-09-01
Si usas Kubuntu, hay un utilitario llamado KwikDisk. Se instala en el área de notificación y te permite ver gráficamente el espacio en todos los puntos de montaje activos. 

También está kdf, que muestra información sobre los puntos de montaje activos y da la posibilidad de montarlos o desmontarlos "a golpe de ratón". Ambos ocupan muy pocos recursos y son muy prácticos.

Ambas utilidades están en el mismo paquete:

apt-get install kdf

Saludetes !

---

### Post by marianom on 2007-09-01
Según me parece, los GDesklets están muertos y enterrados. La onda ahora son los Screenlets.

---

### Post by Vero1 on 2007-09-01
Hola,
Agradezco tus comentarios pero uso Ubuntu-Feisty Fawn.

saludos:)

---

### Post by Vero1 on 2007-09-01
> **marianom said:**
> Según me parece, los GDesklets están muertos y enterrados. La onda ahora son los Screenlets.

Hola,
Deben perdonar "toda" mi ignorancia con respecto a Ubuntu...

En lo que respecta a los Screenlets lo tengo instalado pero al querer usarlo me dice algo de daemon y no funciona.

Qué hago?

gracias y saludos:)

---

### Post by Vero1 on 2007-09-01
> **por100pre1 said:**
> Puede funcionar sin problemas, pero si usas GNOME te conviene mejor usar gdesklets que hace lo mismo pero usando las librerias de GNOME. Superkaramba usa las librerias de KDE. :)

Hola Por100pre1,

Debo debo ya unas cuantas:)

Pero como le dije a marianom, no me funcionan los screenlets porque me dice algo de daemon y no sé qué tengo que hacer.

gracias:)

---

### Post by por100pre1 on 2007-09-01
Yo personalmente lo que uso es Conky, como puedes ver en el post que señalé previamente. Incluso dejé una copia de mi archivo .conkyrc que se guarda en la carpeta de usuario. Conky es mi favorito y resulta en mi humilde opinión mucho más original y llamativo que todos los programas de desklets. Lo malo es que hace falta tiempo y esfuerzo para configurarlo a gusto. Nada, que aqui estamos a la orden y a la vez aprendo mucho pues yo soy tan solo un neófito aprendiendo esto de Linux y Ubuntu.

:popcorn:

---

### Post by SLA_leandrin on 2007-09-01
> **Vero1 said:**
> 

En lo que respecta a los Screenlets lo tengo instalado pero al querer usarlo me dice algo de daemon y no funciona.

Qué hago?

Posteá el error aquí así vemos cual es el problema...

---

### Post by nest on 2007-09-02
> **marianom said:**
> Según me parece, los GDesklets están muertos y enterrados. La onda ahora son los Screenlets.

la onda ahora es conky.

---

### Post by Vero1 on 2007-09-02
> **por100pre1 said:**
> Yo personalmente lo que uso es Conky, como puedes ver en el post que señalé previamente. Incluso dejé una copia de mi archivo .conkyrc que se guarda en la carpeta de usuario. Conky es mi favorito y resulta en mi humilde opinión mucho más original y llamativo que todos los programas de desklets. Lo malo es que hace falta tiempo y esfuerzo para configurarlo a gusto. Nada, que aqui estamos a la orden y a la vez aprendo mucho pues yo soy tan solo un neófito aprendiendo esto de Linux y Ubuntu.

:popcorn:

Gracias y no te preocupes. Me estoy arreglando con Art de Gnome:)

saludos y hasta cualquier momento.:popcorn:

---

### Post by Vero1 on 2007-09-02
> **SLA_leandrin said:**
> Posteá el error aquí así vemos cual es el problema...

Hola, gracias por tu interés, pero lo desinstalé y me estoy arreglando con Art de Gnome.

saludos:)

---

### Post by Vero1 on 2007-09-02
:popcorn:

---

### Post by gnusci on 2007-09-07
> **Vero1 said:**
> Hola,

**$ du -hs**

Me contesta 39M?????

No puede ser...

saludos

Es correcto, 

**$ du -hs**

el comando te regresa el espacio ocupado en el directorio actual, si quieres todo el disco de vas a **/**.

---

### Post by Vero1 on 2007-09-07
Muchas gracias.

saludos:)

---

