---
title: "How to Install Beryl"
date: 2006-12-14
forum: Argentina Team
---

### Post by jpoeta on 2006-12-14
Ayer de la nada navegando en internet me entere de la existencia de Beryl y lo quiero pero no se como instalarlo alguin porfavor que me ayude soy un noob. 
Que grandes efectos al lado de Beryl Vista es pura mierda!!!;) 

Ayudenme 
Asi toda mi familia se pasa a UBUNTU EDGY :mrgreen:

---

### Post by Nemesis Teufel on 2006-12-15
Bueno, quiero ante todo decir que no hice yo este how-to, asi que no me agradezcan nada. Agradecele a Quasar y Benux que les saque la info de su pagina; yo solo lo saco de ahi y lo pego.

Antes de empezar con la instalacion de Beryl, tenes que tener instalado los drivers 3D de tu placa de video. Si tenes nvidia lo haces desde automatix2, si tenes ati [www.usaelputogoogle.com](www.usaelputogoogle.com) 

_**Luego instalas XGL**_

Para instalar XGL abrimos una terminal y escribimos:

```
sudo gedit /etc/apt/sources.list
```

Agregamos los siguientes repositorios:

Para Ubuntu Dapper:
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
deb http://compiz-mirror.lupine.me.uk/ dapper main
```

Para AMD64
```

deb http://www.beerorkid.com/compiz/ dapper main main-amd64
deb http://xgl.compiz.info/ dapper main main-amd64
deb-src http://xgl.compiz.info/ dapper main main-amd64
deb http://compiz-mirror.lupine.me.uk/ dapper main main-amd64
```

Para Ubuntu Edgy

```
deb http://ubuntu.compiz.net/ edgy main-edgy
deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://media.blutkind.org/xgl/ edgy main-edgy
deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy

```
Para amd64

```
deb http://ubuntu.compiz.net/ edgy main-edgy main-edgy-amd64
deb http://www.beerorkid.com/compiz edgy main-edgy main-edgy-amd64
deb http://media.blutkind.org/xgl/ edgy main-edgy main-edgy-amd64
deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy main-edgy-amd64
```

Ahora escribimos la siguiente clave:
```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
wget http://compiz-mirror.lupine.me.uk/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -

```
esto simplemente es para las firmas.

Ya que tenemos los repositorios necesarios lo que Debemos hacer es actualizarlos desde el gestor de paquetes synaptic o desde la consola con el siguiente codigo:

```
sudo apt-get update
```

Ahora si a instalar los paquetes necesarios.

Primero lo mejor es actualizar nuestra distro para no tener ningun tipo de problema, esto toma tiempo y se realiza con el siguiente codigo:

```
sudo apt-get upgrade
```

Para aquellos que tengan flojera de actualizarlo y esten impacientes por tener su cubo funcionando pueden actualizar lo necesario que es el xserver-xorg, repito esto es para los flojos jajaja asi que los que no tengan flojera no hagan caso a esta parte.

Bueno despues de actualizar instalamos el siguiente paquete (xserver-xgl) ya sea desde synaptic o desde la terminal con:

```
sudo apt-get install xserver-xgl

```
Despues de haber instalado el xgl lo que tenemos que hacer es el script de inicio de la siguiente manera: abrimos una terminal y escribimos

```
sudo gedit /usr/bin/startxgl.sh
```

_**[COLOR="Red"]ORIGINAL:[/COLOR]**_[http://benux.wordpress.com/2006/10/10/como-instalar-xglberyl/](http://benux.wordpress.com/2006/10/10/como-instalar-xglberyl/)

_**Por último, instalar Beryl.**_

Para instalar Beryl en Dapper o Ubuntu usando XGL tenemos que tener estos repos en nuestro sources.list y ya instalados y configurados los drivers de nuestra placa de video y habilitada la extension de video compuesto.
Dapper:

```
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://compiz-mirror.lupine.me.uk/ dapper main
deb http://ubuntu.compiz.net/ dapper main
```

Edgy:

```
deb http://ubuntu.beryl-project.org/ edgy main
```

Despues bajemos las firmas de esos repos poniendo en una terminal:
```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
wget http://compiz-mirror.lupine.me.uk/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -
```

Updateamos la lista de repos:

```
sudo apt-get update
```

Instalamos Beryl y XGL:

```
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes

```
Configuramos GDM para que inicie XGL:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

Dentro de gedit:

> [daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

Si tenemos ATI necesitamos cambiar las lineas:

```
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

Por:
```

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl


[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer

```
Ahora solo reiniciemos asi GDM inicia XGL, una vez iniciada sesion abramos una terminal y ejecutemos:

```
beryl-manager
```

Si todo salio bien deberiamos estar corriendo Beryl ya, y si salio bien agreguemos beryl-manager al inicio de sesion de gnome.


_**[COLOR="Red"]ORIGINAL:[/COLOR]**_[http://quasarfreak.com.ar/wordpress/?page_id=19](http://quasarfreak.com.ar/wordpress/?page_id=19)

---

### Post by felipelerena on 2006-12-15
> [www.usaelputogoogle.com]("http://www.usaelputogoogle.com") jua, ayer respondi lo mismo (los foros son la ultima opcion, pone un poco de volutad al respecto e investiga).

para,. para beryl tenes que usar el repo OFICIAL que es este

```
deb http://ubuntu.beryl-project.org/ edgy main
```por que 
1) es el oficial
2) se actualiza "cuando sale el release"

saludos

edit:  ese tutorial es VIEJISIMO, tiene como 6 meses.

---

### Post by Nemesis Teufel on 2006-12-15
> para,. para beryl tenes que usar el repo OFICIAL que es este

Code:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main



Listo!

> edit: ese tutorial es VIEJISIMO, tiene como 6 meses.

Bueno, puede ser, pero mal no esta. Cualquier cosa que haya que cambiarle avisen.

---

### Post by jpoeta on 2006-12-15
Gracias amigos disculpen las molestias una pregunta mas necesito tener tarjeta de video=?
pues yo la tengo integrada en la placa madre.

Tengo 3.0ghz
256mb ram
no tengo tarjeta de video independiente
podre hacerlo aun asi?:confused:

---

### Post by spg76 on 2006-12-15
> **jpoeta said:**
> Gracias amigos disculpen las molestias una pregunta mas necesito tener tarjeta de video=?
pues yo la tengo integrada en la placa madre.

Tengo 3.0ghz
256mb ram
no tengo tarjeta de video independiente
podre hacerlo aun asi?:confused:

Yo tengo video integrado y funciona muy bien.
Lo que te conviene es usar AIGLX en lugar de XGL.
Como ya viene instalado en Edgy, lo unico que tenes que hacer es instalar beryl (asi que te ahorras configurar la placa de video).
Tenes que hacer lo siguiente (esta basado en el HOWTO del wiki de Beryl que podes leer [acá]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX")):

Editar al archivo sources.list

```
sudo gedit /etc/apt/sources.list
```

Agregar esta línea:

```
deb http://ubuntu.beryl-project.org/ edgy main
```

Bajar la clave GPG:

```
sudo wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

Actualizar la lista de paquetes:

```
sudo apt-get update
```

Instalas Beryl con:

```
sudo apt-get install beryl
```

Instalas los temas:

```
sudo apt-get install emerald-themes
```

Para iniciar Beryl, solo tenes que ejecutar elm comando **beryl** o usar el administrardor con **beryl-manager**

Espero que te sirva.
Saludos.

---

### Post by QUASAR_FREAK on 2006-12-15
**ojo ke las guias de mi pagina estan desaktualizadas!!**

Usen las guias ke estan en el foro de Beryl, en lo posible usando Aiglx.

Cuando las updatee posteo aka un howto tambien pero por ahora ando sin tiempo =/

---

### Post by DuckMan on 2006-12-15
o si son pajeros como yo, y ademas no les funciono con ninguna de las mil guias q hay, como a mi :P

automatix2bleeder =) me funciono de 10

---

### Post by jpoeta on 2006-12-15
Soy un total noob segui tus pasos amigo spg76 pero me sale este error
no se que hacer 
ayudenme 
Talvez me falte instalar un Driver del cual ni se de su exustencia pues solo tengo el de video.

esto me sale en terminal:
 >  root@jpoeta-desktop:/home/jpoeta# beryl-manager
root@jpoeta-desktop:/home/jpoeta# libGL warning: 3D driver claims to not support visual 0x46
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
libGL warning: 3D driver claims to not support visual 0x46
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


Nota: En la parte superior me sale un diamante.
Le hago click seleccionar el gestor de ventanas Beryl y me sale en Terminal PARECE QUE EL SERVIDOR X FUE APAGADO O EL GESTOR DE VENtaNAS FUE DESTRUIDO .
y Cierra sesión.

---

### Post by felipelerena on 2006-12-15
para, empecemos de cero, contame... que placa de video tenes?

---

### Post by jpoeta on 2006-12-15
Hola Felipe gracias disculpa la molestia  Yo tengo S3 UniChrome" graphics video en mi placa PCChips :confused: algo más? :confused:

Es intergrada

---

### Post by spg76 on 2006-12-15
> **jpoeta said:**
> Yo tengo S3 UniChrome" graphics video en mi placa PCChips :confused: algo más? :confused:

Es intergrada

Aparentemente, aunque tengas instalados los drivers correctos tu placa no soporta todavía las caracteristícas necesarias para correr Beryl segun lo leí en [esta págína]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus") de openChrome, que es un proyecto de código abierto dedicado a UniChrome.

---

### Post by jpoeta on 2006-12-15
weno entonces no podre gozar de eso hasta navidad que me compre una tarjeta aceleradora de cuanto tendría que ser? 256?;)  que marca me recomiendan que marcas son mas linuxcompatibles:confused:

---

### Post by felipelerena on 2006-12-15
NVIDIA, TODA LA VIDA. no ati

---

### Post by jpoeta on 2006-12-15
NVIDIA entonces pero de cuanto ? cuanto es lo ideal o cuales serian los reuerimiento ideales necesito mas memo ram ? tengo 256  o con la tarjeta nvidia basta:confused: 
Gracias;) 
NAVIDAD NAVIDAD y Mañana es mi cumpleaños:rolleyes:

---

### Post by Benji86 on 2006-12-15
Con una 5200 beryl anda de 10 lei x ahi (yo tengo una 7600 y vuela :P)

---

### Post by QUASAR_FREAK on 2006-12-15
> **DuckMan said:**
> o si son pajeros como yo, y ademas no les funciono con ninguna de las mil guias q hay, como a mi :P

automatix2bleeder =) me funciono de 10

no lo konocia =)

---

### Post by Nemesis Teufel on 2006-12-15
Mira, con una placa geforce 2 de 32 mb "deberia" andar, x lo menos asi lo dice.. pero bue.. no es  nada utilizable.. yo con una gforce 4 64 mb 440mhz me andaba muuuy bien. Ahora con una 6200 de 256mb me cago de la risa.

---

### Post by DuckMan on 2006-12-16
yo tengo una gforse 2 de 32 mb y me funciono, por ahi se te hace pesado pero funciona, por lo menos con el automatix

---

### Post by BlackHero on 2006-12-17
que vamos a hacer con las remeras??????

otra cosa nvidia sucks ATI IS THE BEST =)

---

### Post by beuno on 2006-12-17
> **BlackHero said:**
> que vamos a hacer con las remeras??????

Es uno de los temas a charlar la reunion del Martes    :D

---

### Post by quaid on 2006-12-19
Automatix funciona en Edgy? porque a mi em dice q no lo soporta y jamas se actualizo. 

Igualmente estoy pensando en pasarme a aiglx

---

### Post by spg76 on 2006-12-19
> **quaid said:**
> Automatix funciona en Edgy? porque a mi em dice q no lo soporta y jamas se actualizo. 

Igualmente estoy pensando en pasarme a aiglx

Si, funciona. Fijate si tenes los repositorios correctos.
Si actualizaste desde Dapper, vas a tener que deinstalar la versión que tenes (podes hacerlo con Synaptic), agregar los repositorios de Edgy e instalar.
Podes seguir los pasos [acá]("http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt").
Saludos.

---

### Post by Shyno31 on 2007-11-21
hola.. soy algo nuevo en esto... pero me llamo mucho la atencion cambiarme de "guindous" a ubuntu fue por el beryl...
actualmente estoy usando Ubuntu Gutsy y estuve leyendo todos los post y ninguno veo que diga para gutsy, me podrian por favor asistir en como puedo instalar el Beryl en el Gutsy?
De antemano, gracias por la ayuda....

---

### Post by Hei Ku on 2007-11-21
Busca por Compiz-Fusion, que es el nombre del proyecto luego que Beryl y Compiz se volvieran a unir. 

Compiz era el proyecto original, y Beryl se separo para darle mas enfasis a la parte de efectos. A principios de año se volvieron a unir bajo el nombre Compiz-Fusion.

Compiz-Fusion esta en los repositorios de Gutsy, y de hecho se puede activar automaticamente desde la parte de efectos. Y la mayoria de los consejos que encuentres para Beryl se pueden aplicar tambien a Fusion, incluyendo plugins, temas de Emerald, etc.

---

### Post by sajnox on 2007-11-21
Te agrego al aporte de Hei Ku una guia para instalar compiz fusion

[http://ubuntuforums.org/showthread.php?t=611923&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=611923&highlight=compiz+fusion)

---

### Post by rbarbe on 2007-11-22
Muchachos, ¿me pueden decir cual es el comando para que te muestre en la Terminal el harwadere que te reconocio Linux?

Gracias

---

### Post by faktorqm on 2007-11-22
podes usar "lspci", "lsusb" o fijarte en /var/log a ver cuando arranco el sistema que te tomo y que no. salu2!

---

