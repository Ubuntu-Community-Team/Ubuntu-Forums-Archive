---
title: "Me Presento y hago unas consultas"
date: 2007-07-25
forum: Argentina Team
---

### Post by bernardocodesido on 2007-07-25
Hola gente soy nuevo en esto, instale ubuntu anoche. Si bien tengo algunos conocimientos generales, con otras cosas se me complica. 
Que programa para reproducir musica se puede usar?
Que servidor utilizo para bajar el amsn?, desde anoche estoy intentando bajarlo (desde amsn project) y no hay forma

Muchas gracias
Saludos
Berna

---

### Post by marianom on 2007-07-25
Yo uso el Rhythmbox que es simple, ya viene por defecto y no molesta.

En un ratito nomás ya viene la tribu del Amarok a comentarnos cuan maravilloso pedazo de software es. 

La forma más fácil de instalar amsn es, desde una terminal:

```
sudo apt-get install amsn
```

Es posible que tengas que habilitar el repositorio universe en los sources.
Eso lo haces con

```
sudo vim /etc/apt/sources.list
```
y removiendo el # que está delante del repositorio universe:

Antes:
```
# deb http://ar.archive.ubuntu.com/ubuntu/ feisty universe
# deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty universe

```

después:
```
deb http://ar.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty universe

```

Grabás el cambio y reintentás.

---

### Post by kowal on 2007-07-25
> **marianom said:**
> 

En un ratito nomás ya viene la tribu del Amarok a comentarnos cuan maravilloso pedazo de software es. 


Jajaja.. somos varios los fieles seguidores de San Amarok ;)

bernardocodesido: Hay varios reproductores y para todos los gustos.. Amarok, Rhythmbox, XMMS, BMP, Exaile, Songbird.. etc, etc.

---

### Post by tony_feisty on 2007-07-25
Con respecto a los reproductores tenes varios, el que trae por defecto, el xmms y el amarok, ademas acordate que tener que descargar los codec para mp3, 
codec para mp3: gstreamer0.8-mad

Para reproducir DVD tenes el Kaffeine 
codec para DVD: libxine-extracodecs

y como te comentaron el Amsn.

Fijate que si tenés hecha la conexión de internet todo esto lo bajas de los repositorios, 
Entras al gestor de paquetes los seleccionas y listo y automaticamente te los descarga
con las dependencias que posea.

saludos..

---

### Post by User21 on 2007-07-25
>  En un ratito nomás ya viene la tribu del Amarok a comentarnos cuan maravilloso pedazo de software es.Aca tenes otro indio de la tribu! Amarok es lo maximo! JAJAJAJA :P

  Una ves ke te instales amsn, si es la version 0.97 o superior, kizas tengas problemas con TLS, ke te lo pide instalar. Si es asi, intenta con esto: 

Descarga el tls-1.5.0 aparte, lo descomprimes y lo copias a tu directorio /usr/lib/tls1.50.  con permisos de root .
Como hacerlo desde la consola?

Asi:

```
 1) wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz)
2) tar xvzf tls-1.5.0-linux-x86.tar.gz
3) sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/

```Deberia funcionar ahora. Cuidado ke no se abrevie la URL... y ke la version de TLS no haya cambiado, sino, este enlace seria obsoleto.

Si todavía te dá problemas, entra a amsn, abre preferencias> avanzadas> otras, y donde dice TLS le indicas la ruta donde descomprimiste el tar.gz. Cierra completamente el aMSN y vuelve a iniciarlo.
Aun con problemas ? Estamos en irc.freenode.org en la sala #ubuntu-ar .

Todo esto, si llegase a darte problemas, OBVIO!

---

### Post by spg76 on 2007-07-25
Yo uso alternativamente Amarok y Rhythmbox.
Amarok es impresionante si queres ver mucha información sobre tu colección (Letras, info de los artistas o discos, etc.) y tiene muchisimos plugins para agregarle funcionalidades.
Rhythmbox es más simple y, si "solo" queres escuchar música sin más vueltas, es quizas la opción que más conviene porque ya viene instalado. Ojo, igual tien un montón de opciones.
Lo único que no encuentro en ningún reproductor es poder agregar CD o DVD con MP3 a las colecciones sin copiarlos al disco y pudiendo ver el contenido de los CDs, algo que el viejo y querido [Mediamonkey]("www.mediamonkey.com") puede hacer, aunque solo funciona en Windows. Ya que estamos, ¿alguien sabe de algo reproductor que pueda hacer esto?

---

### Post by marianom on 2007-07-25
Yo tengo un DVD a full con mp3, ogg, flacs y lo toma el Rhythmbox sin problemas. La primera vez lo puse, seleccioné la colección (importé la carpeta), la cargó y listo. Si el dvd no está, no muestra nada, si está me muestra la colección y puedo escuchar de ahí sin problemas.
Fijate bien pero no debería ser un problema en formar alguna.

---

### Post by spg76 on 2007-07-25
> **marianom said:**
> Yo tengo un DVD a full con mp3, ogg, flacs y lo toma el Rhythmbox sin problemas. La primera vez lo puse, seleccioné la colección (importé la carpeta), la cargó y listo. Si el dvd no está, no muestra nada, si está me muestra la colección y puedo escuchar de ahí sin problemas.
Fijate bien pero no debería ser un problema en formar alguna.

Si pongo un CD o DVD con mp3 no hay problema Lo cargo en Rhythmbox (o en Amarok) y lo escucho.
Lo que yo quiero (que es lo que hace Mediamonkey) es agregar los CDs o DVDs a la colección y que los muestre aunque no están en la unidad y así puedo buscar en el mismo programa sin tener que poner cada CD para encontrar lo que quiero.

---

### Post by bernardocodesido on 2007-07-25
Bueno... lo de los codecs me di cuenta despues de un rato y ya puedo usar el Rhythmbox, que ahora me pondre a investigarlo y sacarle su jugo.
Y en cuanto al amsn ya encontre un tutorial y lo pude instalar...
Igualmente muchas gracias por su ayuda..
Slds
Berna

---

### Post by bernardocodesido on 2007-07-26
Ahora cuando reinicio o apago la maquina, todos los cambios realizados (fondo de pantalla, puntero mouse, etc) desaparecen.
Saben poque puede ser eso??

---

### Post by Nemesis Teufel on 2007-07-26
> **bernardocodesido said:**
> Ahora cuando reinicio o apago la maquina, todos los cambios realizados (fondo de pantalla, puntero mouse, etc) desaparecen.
Saben poque puede ser eso??
Eso es xq no instalaste el sist. operativo todavía. Lo estas corriendo en LiveCD.
Hay varios tutoriales que te indican como instalar Ubuntu haciendo particiones y dual boot con windows. Busca la ubuntu guide q es buenisima!

Cuando lo tengas instalado, no se te van a borrar las configuraciones y va a ir muuucho mas rapido :)

---

