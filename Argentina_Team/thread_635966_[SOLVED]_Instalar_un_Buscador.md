---
title: "[SOLVED] Instalar un Buscador"
date: 2007-12-09
forum: Argentina Team
---

### Post by Vero1 on 2007-12-09
Hola a todos,

Resulta que en el chat de ubuntu-es me recomendaron instalar un Buscador. Descargué el archivo(un plugin) en mi Carpeta Personal.
Segun las instrucciones debo "copiar" dicho archivo en /usr/share/firefox/searchingplugins, pero debido a mi desconocimiento en cuanto a copiar archivos, pues no sé como se hace.
Estuve mirando la guía Ubuntu, pero no saco nada en limpio.
Me dijeron que se hacía igual que en Windows, cosa que no me parece.
Busqué /usr/share... en Archivos y lo encontré pero en forma de árbol(no sé si me explico). Cuando le toca el turno a copiar desde mi carpeta personal, no me dá la opcion de pegar en /usr/share...

Alguien sería tan amable de explicarme el procedimiento?

Gracias y saludos:)

---

### Post by marianom on 2007-12-09
/usr/share es una carpeta que está fuera de tu /home, por lo tanto necesitas permisos de root para copiar (y es por eso que no te habilita la opcion para hacerlo).

Lo más rápido y sencillo, una terminal:

```
sudo cp /ruta/hasta/tu/archivo.nnn /usr/share/firefox/searchingplugins
```

---

### Post by Vero1 on 2007-12-09
Gracias. Trataré de hacerlo.

saludos

---

### Post by Vero1 on 2007-12-09
> **Vero1 said:**
> Gracias. Trataré de hacerlo.

saludos

marianom, me contesta:

 falta el operando archivo de destino después de `/home/veronica/Imagen:Buscador_opensearch_files/usr/share/firefox/searchplugins/Firefox'

Vos habías dicho que no está en mi home, pero al copiar el archivo me pone /home,

Originalmente yo había puesto así: :~$ sudo cp /home/veronica/Imagen:Buscador_opensearch_files/usr/share/forefpx/searchplugins
cp: falta el operando archivo de destino después de `/home/veronica/Imagen:Buscador_opensearch_files/usr/share/forefpx/searchplugins'

Qué hice mal o qué me falta poner?

---

### Post by Hei Ku on 2007-12-09
> **Vero1 said:**
> marianom, me contesta:

 falta el operando archivo de destino después de `/home/veronica/Imagen:Buscador_opensearch_files/usr/share/firefox/searchplugins/Firefox'

Vos habías dicho que no está en mi home, pero al copiar el archivo me pone /home,

Originalmente yo había puesto así: :~$ sudo cp /home/veronica/Imagen:Buscador_opensearch_files/usr/share/forefpx/searchplugins
cp: falta el operando archivo de destino después de `/home/veronica/Imagen:Buscador_opensearch_files/usr/share/forefpx/searchplugins'

Qué hice mal o qué me falta poner?

Tenes que poner un espacio entre el origen y el destino. No entiendo muy bien el origen, pero debe ser algo asi:
sudo cp /home/veronica/Imagen:Buscador_opensearch_files /usr/share/forefpx/searchplugins

Como se llama el archivo q bajaste a tu home?

---

### Post by Vero1 on 2007-12-09
El archivo que figura en mi home es

/home/veronica/Imagen:Buscador_opensearch_files

Ojo que me equivoqué al poner firefox pero despues lo corregí.

---

### Post by Hei Ku on 2007-12-09
> **Vero1 said:**
> El archivo que figura en mi home es

/home/veronica/Imagen:Buscador_opensearch_files

Ojo que me equivoqué al poner firefox pero despues lo corregí.

Entonces deberia ser:

sudo cp /home/veronica/Imagen:Buscador_opensearch_files /usr/share/forefox/searchplugins/Imagen:Buscador_opensearch_files

---

### Post by Vero1 on 2007-12-09
Hola Hei Ku

Me contesta:

cp: se omite el directorio `/home/veronica/Imagen:Buscador_opensearch_files'

Parece no tan fácil el asunto.

Gracias

---

### Post by Hei Ku on 2007-12-09
> **Vero1 said:**
> Hola Hei Ku

Me contesta:

cp: se omite el directorio `/home/veronica/Imagen:Buscador_opensearch_files'

Parece no tan fácil el asunto.

Gracias

No me digas que es una carpeta. :D

Entonces es asi:


sudo cp /home/veronica/Imagen:Buscador_opensearch_files /usr/share/forefox/searchplugins/  -R -v

Aclaración: todo muy lindo esto de aprender los comandos por terminal. Pero la verdad es que cuando tengo que copiar cosas como sudo, lo que hago es:

Alt+F2
sudo konqueror

listo, con eso arranco el konqueror con permisos de root y ya esta. :D
Para los gnomeros, deberia ser sudo nautilus

---

### Post by Vero1 on 2007-12-09
Hei Ku,

Pues no estamos de suerte :-) Sí es una carpeta que está en Mi Carpeta Personal.

Esta vez me contesta:

cp: el destino, `/usr/share/forefox/searchplugins/', no es un directorio: No existe el fichero ó directorio

No puedo usar Konqueror. Lo cierto es que había instalado KDE pero me desconfiguró la pantalla, el teclado, etc. y lo desinstalé.

Ahora, me hablas de permisos de root. Hay un terminal root. No se puede usar?

Bueno, veo a ver qué me decís ahora.:)

Gracias

---

### Post by clasificado on 2007-12-09
¿no tenes kde?

¡no hay problema! Podes usar el equivalente en Gnome
```
gksudo nautilus
```

Dentro de este navegador de archivos vas a poder copiar y borrar todo lo que haya en el disco sin limitaciones.

Tan pocas limitaciones tiene, que mejor usalo para copiar y cerralo despues.

clasificado

---

### Post by Vero1 on 2007-12-09
Hola clasificado,

No sé si salió bien. Fijate lo que informa la terminal root:

[http://paste.ubuntu-nl.org/47594/](http://paste.ubuntu-nl.org/47594/)

Me fijé si se había agregado y sí se agregó lo que copié, pero me queda la duda de si está todo bien :-(

Gracias

---

### Post by Hei Ku on 2007-12-09
> **Vero1 said:**
> Hei Ku,

Pues no estamos de suerte :-) Sí es una carpeta que está en Mi Carpeta Personal.

Esta vez me contesta:

cp: el destino, `/usr/share/forefox/searchplugins/', no es un directorio: No existe el fichero ó directorio.

Gracias

pusiste forefox, no firefox. por eso es que no anduvo :D

---

### Post by Vero1 on 2007-12-09
Ay Dios, Hei Ku, creo que me estoy volviendo mona...

No me extraña, ya ni sé lo que escribo. Di tantas vueltas...

Bueno, lo intentaré una vez mas:)

---

### Post by Vero1 on 2007-12-09
Hei Ku,

fijate por favor en el Pastebin a ver si sacás algo en limpio. Yo no veo cambios en el navegador.

[http://paste.ubuntu-nl.org/47624/](http://paste.ubuntu-nl.org/47624/)

gracias

---

### Post by Vero1 on 2007-12-09
> **Vero1 said:**
> Hei Ku,

fijate por favor en el Pastebin a ver si sacás algo en limpio. Yo no veo cambios en el navegador.

[http://paste.ubuntu-nl.org/47624/](http://paste.ubuntu-nl.org/47624/)

gracias

Hei Ku, acabo de comprobar que NO se ha instalado :-(

---

### Post by Hei Ku on 2007-12-09
> **Vero1 said:**
> Hei Ku, acabo de comprobar que NO se ha instalado :-(

Pone la pagina de donde lo sacaste, a ver si en las instrucciones dice algo mas.

Te fijaste que en caja de busqueda no te aparece la nueva opcion? Es la caja a la derecha de donde pones las direcciones URL.

---

### Post by Vero1 on 2007-12-10
Sí me fijé pero no se instaló.

Ahora, en Terminal dice algo que de que share no está habilitado en Nautilus...

Te pongo la página de donde saqué el link:

[http://doc.ubuntu-es.org/Imagen:Buscador_opensearch.txt](http://doc.ubuntu-es.org/Imagen:Buscador_opensearch.txt)

---

### Post by Vero1 on 2007-12-10
> **Vero1 said:**
> Sí me fijé pero no se instaló.

Ahora, en Terminal dice algo que de que share no está habilitado en Nautilus...

Te pongo la página de donde saqué el link:

[http://doc.ubuntu-es.org/Imagen:Buscador_opensearch.txt](http://doc.ubuntu-es.org/Imagen:Buscador_opensearch.txt)

acá está el primer link donde explica lo que hay que hacer:

[http://doc.ubuntu-es.org/doc.ubuntu-es:Buscador](http://doc.ubuntu-es.org/doc.ubuntu-es:Buscador)

---

### Post by Hei Ku on 2007-12-10
Proba con este comando:

sudo wget [http://doc.ubuntu-es.org/images/1/12/Buscador_opensearch.txt](http://doc.ubuntu-es.org/images/1/12/Buscador_opensearch.txt) -O /usr/share/firefox/searchplugins/Buscador_opensearch.xml

---

### Post by Vero1 on 2007-12-11
Hei Ku, 
Evidentemente no hay suerte con el bendito buscador y eso que me comentaron algunos que lo han instalado que no tuvieron ningun problema...

~$ sudo wget [http://doc.ubuntu-es.org/images/1/12...opensearch.txt](http://doc.ubuntu-es.org/images/1/12...opensearch.txt) -O /usr/share/firefox/searchplugins/Buscador_opensearch.xml
--14:25:45--  [http://doc.ubuntu-es.org/images/1/12...opensearch.txt](http://doc.ubuntu-es.org/images/1/12...opensearch.txt)
           => `/usr/share/firefox/searchplugins/Buscador_opensearch.xml'
Resolviendo doc.ubuntu-es.org... 150.128.97.77
Conectando a doc.ubuntu-es.org|150.128.97.77|:80... conectado.
Petición HTTP enviada, esperando respuesta... 404 Not Found
14:25:48 ERROR 404: Not Found.

:confused:

---

### Post by Hei Ku on 2007-12-11
Por lo que veo en lo que copiaste, dejaste un espacio en medio del nombre de archivo, por eso no lo encuentra. Proba de vuelta:

sudo wget [http://doc.ubuntu-es.org/images/1/12/Buscador_opensearch.txt](http://doc.ubuntu-es.org/images/1/12/Buscador_opensearch.txt) -O /usr/share/firefox/searchplugins/Buscador_opensearch.xml

---

### Post by Vero1 on 2007-12-12
VIVA HEI KU!

Lo extraño es que cuando lo pegué en Terminal el espacio no existía...

En fin, te doy las gracias por tu santa paciencia.

Por fin se instaló el bendito buscador:)

saludos y gracias nuevamente.

---

