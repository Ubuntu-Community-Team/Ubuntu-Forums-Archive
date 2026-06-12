---
title: "Informe meteorológico"
date: 2008-03-23
forum: Argentina Team
---

### Post by mcongom on 2008-03-23
En el panel superior puse el icono del informe meteorologico, pero cuando cambio la locacion a La Plata, que es de donde soy yo, no me muestra nada, alguien sabe como hacer para ver la temperatura de mi ciudad???
gracias

---

### Post by pol666 on 2008-03-23
mira yo no se como se hace bien..

A mi me funciona el del panel y el del AWN pero no el del Screenlet

le pongo Aeroparque,
Buenos Aires
Buenos Aires, Argentina

etc.etc. y no funca :(

---

### Post by malbecar on 2008-03-25
Have you try using the city code?
Try with this: ARBA0043

---

### Post by mcongom on 2008-03-25
> **malbecar said:**
> Have you try using the city code?
Try with this: ARBA0043
where shall i use that code?? in the zone search bar?? i couldnt.......

---

### Post by sajnox on 2008-03-25
Gente obvio que no hay problemas en usar el idioma Ingles, pero tambien pongamoslo en castellano

Folks, obviusly there is no problem with posting in english but please do it also in spanish

---

### Post by malbecar on 2008-03-25
perdon, estaba respondiendo otros post.

y te funciona con buenos aires?
podes poner un screen de pantalla donde lo estas ingresando?
yo estoy usando el screenlet con el codigo y me funciona, si te sirve te hago un screen.

---

### Post by felipelerena on 2008-03-26
ay! ellos, que hablan tantos idiomas!
jajajaja

ojo con baires que no hay "buenos aires" hay aeroparque y ezeiza por ahi tenes que buscar el aeropuerto de LA PLATA

---

### Post by jpmorelli on 2008-03-27
Yo lo tengo funcionando desde hace mil, el tema es que soy de Capital Federal y acá para aeroparque pongo ARDF0127.
Tenés que buscar el código en:

[http://espanol.weather.com/search/drilldown/?geoCd=4&geoCdChild=1&itemCd=AR&countryCd=AR&itemName=Argentina&countryName=Argentina&what=Weather36HourUndeclared&x=0&y=0]("http://espanol.weather.com/search/drilldown/?geoCd=4&geoCdChild=1&itemCd=AR&countryCd=AR&itemName=Argentina&countryName=Argentina&what=Weather36HourUndeclared&x=0&y=0")

El código de 4 letras y 4 números que está al final de link de cada ciudad ( antes del signo de interrogación ) es el código que hay que poner. Por ejemplo el de LA PLATA es: ARBA0043

---

### Post by InsektO on 2008-03-27
Creo que el post original se refiere a la miniaplicación de Informe meteorológico que va en el panel (de hecho eso dice :P - ver adjunto -), en cuyo caso, no se ingresan códigos de ciudades (eso va para los screenlets o desklets que sacan la info de [www.weather.com](www.weather.com)).

En la miniaplicación, en cambio, hay que elegir la estación correspondiente que ofrecen en el menú desplegable. No sé particularmente si hay algo cerca de La Plata (La Plata específicamente no está listada)... Tal vez algo cercano de un valor aproximado...

Saludos!

---

### Post by jpmorelli on 2008-03-27
Uff ! Tenés razón Insekto, y también yo me refería a ese, pero me mareé y terminé explicando sobre el screenlet que también tengo en el escritorio :P , mea culpa.

---

### Post by mcongom on 2008-04-02
> **jmorelli said:**
> Uff ! Tenés razón Insekto, y también yo me refería a ese, pero me mareé y terminé explicando sobre el screenlet que también tengo en el escritorio :P , mea culpa.

en realidad es como dice InsektO, es para la miniaplicacion. Pero sino se puede asi, como es eso del screenlet??

---

### Post by InsektO on 2008-04-02
> **mcongom said:**
> en realidad es como dice InsektO, es para la miniaplicacion. Pero sino se puede asi, como es eso del screenlet??

Lo de la imagen que sigue es un desklet:

[ATTACH]64693[/ATTACH]

Para instalar gDesklets (está en el repositorio), lo hacés directamente desde **Añadir y quitar**, o en consola con:

```
sudo apt-get gdesklets
```

Luego de instalado, vas a Aplicaciones > Accesorios > gDesklets, y ahí te aparecen los distintos desklets que tenés para usar (algunos están buenos, otros realmente no; yo el único que uso de esos es el del clima, que se llama GoodWeather).

Si querés que se cargue automáticamente cada vez que reiniciás la pc, tenés que agregarlo a las opciones de inicio de sesión (Sistema > Preferencias > Sesiones > Añadir, el comando es gdesklets).

Esto otro es un screenlet:

[ATTACH]64694[/ATTACH]

No es que se vea así feo, pero los screenlets se ven mejor con Compiz activado (y yo no lo estoy usando porque me trae problemas con los juegos). Para instalar Screenlets, vas a tener que descargarlo desde GetDeb...

[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

Instalás el que sea para tu versión de Ubuntu, lo iniciás, y ya viene también con varios screenlets precargados para elegir.

En cualquiera de los 2 casos, para configurar la ciudad, tendrás que dar doble clic e ingresar el ZIP code correspondiente. Este ZIP code lo sacas de la página de [www.weather.com](www.weather.com) buscando la ciudad que te interesa y extrayendo el código correspondiente de la dirección... Por ejemplo, para Buenos Aires, el link es [http://www.weather.com/outlook/travel/businesstraveler/local/](http://www.weather.com/outlook/travel/businesstraveler/local/)**[COLOR="Red"]ARBA0009[/COLOR]**?from=search_city, y lo que marqué es el código que necesitás. Ingresás ese código en la aplicación, y listo.

Saludos!

---

