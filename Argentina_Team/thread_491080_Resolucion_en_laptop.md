---
title: "Resolucion en laptop"
date: 2007-07-03
forum: Argentina Team
---

### Post by Volkl on 2007-07-03
Hola,

soy nuevo tanto en linux como en el foro y quisiera preguntarle como puedo cambiar mi resolucion de pantalla de una laptop Hp 1625la la placa de video es Intel® Graphics Media Accelerator 950.
Solo me deja seleccionar 1024x768 - 800x600 - 640x480. Cuando se puede seleccionar hasta 1280x960. Estuve buscando en el foro, pero encontre para laptop Dell y ademas no eran para la misma placa.

Muchas gracias!! :p

Saludos!!

---

### Post by gepatino on 2007-07-03
La forma más limpia debería ser ejecutando en una consola:

sudo dpkg-reconfigure xserver-xorg


Y en algun momento debería preguntarte que resoluciones queres habilitar. Ahi seleccionas las que quieras y al reiniciar el X te debería tomar la resolución más alta que soporte tu equipo.

...

mmm.... ahora recuerdo que había leído varias veces sobre este problema con las placas intel, me parece que hay un paquete que se llama 915resolution o algo similar, que configura correctamente la resolucion nativa para las placas intel. Buscalo en el synaptic.

---

### Post by Volkl on 2007-07-03
Entre al Xorg y hay una sola resolucion habilitada, la cual es la que quiero, pero sin embargo no me la muestra.

Anduve por la web de intel  y me mando a una web en donde se congirua. Veremos que pasa.

> 
mmm.... ahora recuerdo que había leído varias veces sobre este problema con las placas intel, me parece que hay un paquete que se llama 915resolution o algo similar, que configura correctamente la resolucion nativa para las placas intel. Buscalo en el synaptic.


Eso como lo hago?? Perdon es que recien empiezo con linux!

---

### Post by marianom on 2007-07-03
Para buscar el paquete en Synaptic, anda a Sistema->Administración->Gestor de paquetes Synaptic y una vez abra con Control+F podrás escribir el nombre de lo que estás buscando para que te lo muestre y puedas instalar.

---

### Post by manzuk on 2007-07-03
Fijate esto [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Yo tengo una laptop con esa placa de video, y con el 915resolution pude utilizarla con la resolución adecuada.

---

### Post by Volkl on 2007-07-03
> **marianom said:**
> Para buscar el paquete en Synaptic, anda a Sistema->Administración->Gestor de paquetes Synaptic y una vez abra con Control+F podrás escribir el nombre de lo que estás buscando para que te lo muestre y puedas instalar.

> **manzuk said:**
> Fijate esto [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Yo tengo una laptop con esa placa de video, y con el 915resolution pude utilizarla con la resolución adecuada.

Gente: muchisimas gracias!!

Hoy a la tarde lo pruebo y les comento que tal me fue!!

Gracias!!!!:D

---

### Post by jajajavi on 2007-07-03
A mí me funcionó con esto
```
sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution

```

y reiniciar X (ctrl+alt+del)!!

---

### Post by Volkl on 2007-07-03
No me fue nada bie.

Sigo con esa resolucion. Ya he probado miles de coas y nada :(

Que mas puedo hacer??

---

### Post by jajajavi on 2007-07-04
No se me ocurre, tal vez el problema esté en /etc/X11/xorg.conf en la Section "Screen" donde deberías tener los modos de pantalla, tipo "1280x1024" "1152x864" ...

---

### Post by Volkl on 2007-07-04
> **jajajavi said:**
> A mí me funcionó con esto
```
sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution

```

y reiniciar X (ctrl+alt+del)!!

Eso no mie sirvio.

Tambpoco la instalacion del 915resolution.

Hay una parte en la que tengo monitor generico y estan las resoluciones de la pantalla, pero deje solamente la que me servia, sin embargo no me deja elegir la confiuracion adecuada para mi laptop.
Hoy a la tarde posteare mi xorg.conf.

---

### Post by Volkl on 2007-07-05
Encontre el problema!!

Lo que paso fue que la laptop tiene la salida de video dual. Una salida al lcd y otra para conectar un monitor cualquiera u otro dispositivo.
Lo que esta haciendo es ajustarme la resolucion como si estuviese usando la salida para otro dispositivo.

Hay alguna forma de cambiar eso? No puedo cambiarlo desde el bios, ya probe y el boot device display no esta.

Saludos!!

---

