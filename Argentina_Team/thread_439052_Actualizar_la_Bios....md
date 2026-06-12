---
title: "Actualizar la Bios..."
date: 2007-05-10
forum: Argentina Team
---

### Post by valucha on 2007-05-10
[COLOR="DarkOrchid"]Sirve de algo?...
Estaba navegando por la página de mi mother (Soyo SY- P4VGM) y encontré una actualización de la BIOS...
La verdad que no sé para qué serviría actualizarla. Encima te dan un .exe así que si me dicen que es necesario la pregunta siguiente sería ¿Cómo hago :)?.

Yo tengo un problema con Feisty que no termina de apagar mi computadora (para el cual ya probé configurando y desconfigurando de todo)... Si actualizo se solucionará?...

Bueno, muchas gracias desde ya...[/COLOR]

---

### Post by jayflower on 2007-05-10
No dice que ventajas o que cambios trae ese cambio de Rom? A veces conviene, por ejemplo para unos mothers viejos se necesitaba flashear la BIOS porque no reconocían discos grandes, a veces no trae muchas ventajas. Fijate que te dice de los cambios. Cualquier cosa PM te ayudo. Lo del apagado...Te fijaste en el Bios Setup una parte de APM?
Salutes

---

### Post by beuno on 2007-05-10
> **valucha said:**
> [COLOR="DarkOrchid"]Sirve de algo?...
Estaba navegando por la página de mi mother (Soyo SY- P4VGM) y encontré una actualización de la BIOS...
La verdad que no sé para qué serviría actualizarla. Encima te dan un .exe así que si me dicen que es necesario la pregunta siguiente sería ¿Cómo hago :)?.

Yo tengo un problema con Feisty que no termina de apagar mi computadora (para el cual ya probé configurando y desconfigurando de todo)... Si actualizo se solucionará?...

Bueno, muchas gracias desde ya...[/COLOR]

Generalmente conviene actualizar, pero es importante que sepas que si algo sale mal...    es muy dificil recuperar.
Dicho eso, es comun actualizar el BIOS, y no deberias tener problemas.

Suerte  ;)

---

### Post by alejandroharfuch on 2007-05-10
hay alguna aplicacion para actualizar el bios desde linux, algun equivalente al winflash o algo por el estilo que no involucre diskettes

---

### Post by kalel on 2007-05-10
> **alejandroharfuch said:**
> hay alguna aplicacion para actualizar el bios desde linux, algun equivalente al winflash o algo por el estilo que no involucre diskettes


el [Hiren]("http://homepage.ntlworld.com/hiren.thanki/bootcd.html") tiene ese tipo de aplicaciones, pero no te puedo asegurar nada pk jamas las probe, y se es un garron tener ke actualizar booteando de diskette aunke tb tenes cd de booteo que te levantan un command para poder ejecutar el winflash

---

### Post by valucha on 2007-05-10
> **jayflower said:**
> No dice que ventajas o que cambios trae ese cambio de Rom? A veces conviene, por ejemplo para unos mothers viejos se necesitaba flashear la BIOS porque no reconocían discos grandes, a veces no trae muchas ventajas. Fijate que te dice de los cambios. Cualquier cosa PM te ayudo. Lo del apagado...Te fijaste en el Bios Setup una parte de APM?
Salutes
[COLOR="DarkOrchid"]
La verdad que en la pág no dice nada al respecto, soloo dice que hay un upgrade:
[http://www.soyo.com/downloads/selectresults.php?language=&col3=BIOS%20Upgrade&col2=292](http://www.soyo.com/downloads/selectresults.php?language=&col3=BIOS%20Upgrade&col2=292)[/COLOR]

---

### Post by alejandroharfuch on 2007-05-11
por lo que vi ahí para flashear bios es el UniFlash 1.40
l resto son para guardar seteos y no se que mas
[http://www.uniflash.org/](http://www.uniflash.org/) parece funcar, despues habria que probar
lastima que mi mother no figura en la lista de hard compatible, sino le daía con toda confianza

---

### Post by jpmorelli on 2007-05-12
El Uniflash es una utilidad universal que sirve para flashear ( borrar la data anterior que esta en una Eprom en el mother y cargar la nueva ). Se le dice comunmente flashear porque el proceso que lleva a cabo anteriormente se llevaba a cabo aplicando una luz sobre la ventanita que contenía la eprom dentro del chip, eso hacía que se borre el contenido y quede libre para cargarle otra información. Obviamente esto se hacía sobre una plaqueta aparte de la computadora que efectuaba el proceso, Ahora como todo se evolucionó en el tema y el mother puede quedar durante unos segundos sin su bios ( ya que la PC ya arrancó y mantiene esos seteos hasta que la energía se corte nuevamente ) para poder cargar la nueva versión de bios que el fabricante publica.
Volviendo al uniflash, es un programa que se encarga de borrar y subir el archivo con el nuevo bios ( generalmente un archivo .bio o .rom ). Pero este proceso es peligroso ya que si uno le da un .bio o .rom que no corresponde exactamente con el mother, éste generalmente luego de resetear no arranca nunca más, en estos casos lo único que se puede hacer es: conseguir el mismo mother, sacarle el chip y usarlo en el viejo ( o sea entre dos mothers hacer uno ) o tirarlo a la basura :( ( hay más opciones pero bueno, ninguna sirve de mucho y son arriesgadas )
Resumiendo, si el fabricante pone en la web un archivo .exe con una nueva versión de bios para cierto mother, generalmente tiene ya incluído: un chequeador para saber si el modelo del mother que se quiere flashear es el correcto, el ejecutable que se encarga de hacer el flash ( uniflash, iflash, etc ) y el archivo del bios propiamente.
A veces el exe descomprime todas estas herramientas en un diskete para bootear desde ahi y automatizar el proceso y a veces ( caso intel ) tambien están los .exe para correr desde el entorno Win ( tiene un par de instrucciones que resetean la máquina y le hacen correr el update en el proximo booteo.
Espero haber sido claro porque escribí todo de corrido :P

---

### Post by valucha on 2007-05-13
[COLOR="DarkOrchid"]Claro como el agua...
en definitiva, no creo que lo haga, o tal vez lo mande a que alguien lo haga asi me aseguro que va a estar bien, y en el caso de que pase algo que se haga cargo :).... porque no es como instgalar ubuntu, o windows, es más peligroso.[/COLOR]

---

### Post by dGV on 2007-05-21
hola valucha, resulta que tengo el mismo problema que tu, mi compu no apaga con el ubuntu, llega hasta una pantalla negra que dice "system halted" y ya... si encontraste solución  me puedes avisar? gracias .... seguire buscando, si la encuentro aviso.. :D

---

