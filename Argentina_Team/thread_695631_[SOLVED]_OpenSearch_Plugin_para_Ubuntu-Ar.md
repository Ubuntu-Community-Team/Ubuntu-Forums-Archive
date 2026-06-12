---
title: "[SOLVED] OpenSearch Plugin para Ubuntu-Ar"
date: 2008-02-13
forum: Argentina Team
---

### Post by User21 on 2008-02-13
**LES TENGO TRABAJO:**
Si alguien sabe como lograr, despues de leer este [COMO]("http://developer.mozilla.org/en/docs/Creating_OpenSearch_plugins_for_Firefox"), acerca de crear un Plugin de Busqueda OpenSearch para Firefox, pues, que se ponga en acción, porque yo no tengo NI IDEA, jejeje! 

Aca les dejo de que se trata: [https://addons.mozilla.org/en-US/firefox/browse/type:4](https://addons.mozilla.org/en-US/firefox/browse/type:4)

En la barra de herramientas de Ubuntu-Ar que hace poco puse a conocimiento publico, usé la url [http://ubuntuforums.org/search.php?f=189&q=SEARCHTERM&do=process](http://ubuntuforums.org/search.php?f=189&q=SEARCHTERM&do=process)
por si les sirve de algo!
Ademas, luego, pueden enlistarlo en el directorio de motores de busqueda de Mozilla.  VAS A SER FAMOSO!!!  :lolflag:

---

### Post by faktorqm on 2008-02-13
Sigo sin entender que es realmente lo que queres, pero con mis dotes de chorizo :P copio y pego el texto de ejemplo y adapto: ¿funcionara?

```

<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/"
                       xmlns:moz="http://www.mozilla.org/2006/browser/search/">
<ShortName>Ubuntu-ar-search</ShortName>
<Description>Motor de búsqueda de Ubuntu-ar</Description>
<InputEncoding>iso8859-15</InputEncoding>

```
en lo del inputenconding tenia una duda, irá asi no mas, o habra que poner chrset=iso8859-15? para mi hay que dejarlo asi, pero bueno....
Hasta acá facilongo venia el tema, ahora no sigue tanto, tenes ke ir a esta direccion

[http://software.hixie.ch/utilities/cgi/data/data](http://software.hixie.ch/utilities/cgi/data/data)

y poner ahi la direccion de donde tengas hosteada la foto, seleccionar la casilla base64, asegurarte de tenga 16x16 pixeles, y donde dice "VA ACA" tendrias que poner lo que te devuelve el boton generate de la pagina anterior.

```
<Image width="16" height="16">data:image/x-icon;base64,VA ACA</Image>
```

Bien, a partir de aca la cosa es asi, en donde dice url type, podes poner 2 cosas, text/html, que es normal digamos, o application/x-suggestions+json, que es para que te aparezcan las palabras sugeridas a medida que vas escribiendo o cuando ya terminaste. yo puse texto plano, para no complicarla. Despues que el desarrollador de la barra se arregle...... :P
En donde dice method hay que poner o get o post, pero como post no lo soporta el ie7, y estamos haciendo un plugin para firefox, no se para que lo aclaran la verdad. va post, por que? no se.
template, tenes que poner la direccion de busqueda en el foro, ya te estaras preguntando como es que le pasa lo que tipo ingreso al buscador del foro, muy simple, con el siguiente conjunto de letras y signos: "{searchTerms}". Entonces lo que sigue deberia quedar algo asi como:

```
<Url type="text/html" method="post" template="http://ubuntuforums.org/search.php?f=189&q={searchTerms}&do=process">
```

Lo de los param's en la documentacion dice que es opcional, asi que lo saco. Lo ultimo que queda, es lo que va dirigido cuando uno apreta la lupita:

```
<moz:SearchForm>http://ubuntuforums.org/search.php?f=189</moz:SearchForm>
```

Ahi vamos, cerramos con ```
</OpenSearchDescription>
``` y listo el pollo!! ya estamos.
Se pueden hacer 15000 mejoras, pero eso lo dejamos para la segunda versión. Salu2 a todos!!

PAGINA CON LA DOCUMENTACION: [http://www.opensearch.org/Specifications/OpenSearch/1.1](http://www.opensearch.org/Specifications/OpenSearch/1.1)

---

### Post by User21 on 2008-02-13
El amigo Faktorqm logró terminar el OpenSearch Plugin para Firefox!

Copien y guarden este código como UbuntuARSearch.xml en la carpeta ~/.Mozilla/Firefox/BLABLA.Default/searchplugins, donde BLABLA es una carpeta aleatoria, al parecer...

```
<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/"
                       xmlns:moz="http://www.mozilla.org/2006/browser/search/">
<ShortName>Ubuntu-AR-Search</ShortName>
<Description>Motor de búsqueda de Ubuntu-ar</Description>
<InputEncoding>UTF-8</InputEncoding>
<Image width="16" height="16">data:image/x-icon;base64,R0lGODlhEAAQAIQfAPrTyv2xSP7r4%2Fzh1%2B2TivSyqPhzO%2FyPAfqYb%2F3Kkeh4c%2Fipjv7z7P%2F59P2qO9MDA%2FzLpdomJvRHANcZGf66YfzNuf3EfPyfJ%2F7dtPVQCvZfH99PT%2F7UpP7hvPdjI%2F%2F%2F%2FyH%2BEFVidW50dS1JQ08gMTZ4MTYALAAAAAAQABAAAAVd4CeOZGmeqMgARQU8ytk0iyRlxUScx8EJwIVHMzAdLgJSRYIgIRaHhMljINkuGNOgONIYoqbJhiRgHBmkV6zUgzDKuQfARHEMInhYITUoEAgABxQpJA0UHYSJiiIhADs%3D</Image>
<Url type="text/html" method="post" template="http://ubuntuforums.org/search.php?f=189&amp;q={searchTerms}&amp;do=process"></Url>
<moz:SearchForm>http://ubuntuforums.org/search.php?f=189</moz:SearchForm>
</OpenSearchDescription>

```Ahora si, ya pueden hacer búsquedas en el foro directamente desde Firefox! u otro browser compatible con los plugins OpenSearch! :D 

[IMG]http://img137.imageshack.us/img137/3055/opensearchpluginparaubuie5.jpg[/IMG]

---

### Post by euzkoarima on 2008-02-13
Acabo de probarlo, busca pero en todos los foros!! no solo en este. A alguien más le pasa lo mismo o busco que hice mal (para copiar-pegar y guardar se supone que todavía me da, pero nunca se sabe ;-)

---

### Post by spg76 on 2008-02-13
Tenés razón, euzkoarima.
Lo arreglé un poco y ahora solo busca en nuestro foro.
Copio y pego:

```
<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/"
                       xmlns:moz="http://www.mozilla.org/2006/browser/search/">
<ShortName>Ubuntu-AR-Search</ShortName>
<Description>Motor de búsqueda de Ubuntu-ar</Description>
<InputEncoding>UTF-8</InputEncoding>
<Image width="16" height="16">data:image/x-icon;base64,R0lGODlhEAAQAIQfAPrTyv2xSP7r4%2Fzh1%2B2TivSyqPhzO%2FyPAfqYb%2F3Kkeh4c%2Fipjv7z7P%2F59P2qO9MDA%2FzLpdomJvRHANcZGf66YfzNuf3EfPyfJ%2F7dtPVQCvZfH99PT%2F7UpP7hvPdjI%2F%2F%2F%2FyH%2BEFVidW50dS1JQ08gMTZ4MTYALAAAAAAQABAAAAVd4CeOZGmeqMgARQU8ytk0iyRlxUScx8EJwIVHMzAdLgJSRYIgIRaHhMljINkuGNOgONIYoqbJhiRgHBmkV6zUgzDKuQfARHEMInhYITUoEAgABxQpJA0UHYSJiiIhADs%3D</Image>
<Url type="text/html" method="post" template="http://ubuntuforums.org/search.php?f=189&amp;q={searchTerms}&amp;do=process&amp;forumchoice%5B%5D=189&amp;childforums=1&amp;exactname=1&amp;showposts=0"></Url>
<moz:SearchForm>http://ubuntuforums.org/search.php?f=189</moz:SearchForm>
</OpenSearchDescription>
```

---

### Post by User21 on 2008-02-13
FANTASTICO! :D  Ya mismo lo estoy editando en mi Firefox!
Update: FUNCIONA PERFECTAMENTE LA EDICION DE spg76 Y BUSCA EN NUESTRO FORO! :D APROVECHO Y APLICO EL CAMBIO EN LA [**UBUNTU AR TOOLBAR**]("http://ubuntuforums.org/showthread.php?t=695521")!

---

### Post by euzkoarima on 2008-02-14
Anda de 10!!!
Gracias

---

### Post by faktorqm on 2008-02-14
Más modificaciones:
- El ultimo tag no tenia &amp; sino que tenia el "?" directamente, y ademas se agrego para que busque en nuestro foro cuando vayas con la lupita y no en todos. (gracias spg76)
- Se saco el tag de la codificacion de caracteres, segun la documentacion por defecto es utf-8 para input y output.
- Se agrego el campo developers, con los nombres de los desarrolladores.
- Se cambio el tag descripcion, para que otro sepa para que sirve ;)

```

<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/"
                       xmlns:moz="http://www.mozilla.org/2006/browser/search/">
<ShortName>Ubuntu-AR-Search</ShortName>
<Description>Plug-in para búsqueda en foro de Ubuntu Argentina Loco Team</Description>
<Image width="16" height="16">data:image/x-icon;base64,R0lGODlhEAAQAIQfAPrTyv2xSP7r4%2Fzh1%2B2TivSyqPhzO%2FyPAfqYb%2F3Kkeh4c%2Fipjv7z7P%2F59P2qO9MDA%2FzLpdomJvRHANcZGf66YfzNuf3EfPyfJ%2F7dtPVQCvZfH99PT%2F7UpP7hvPdjI%2F%2F%2F%2FyH%2BEFVidW50dS1JQ08gMTZ4MTYALAAAAAAQABAAAAVd4CeOZGmeqMgARQU8ytk0iyRlxUScx8EJwIVHMzAdLgJSRYIgIRaHhMljINkuGNOgONIYoqbJhiRgHBmkV6zUgzDKuQfARHEMInhYITUoEAgABxQpJA0UHYSJiiIhADs%3D</Image>
<Url type="text/html" method="post" template="http://ubuntuforums.org/search.php?f=189&amp;q={searchTerms}&amp;do=process&amp;forumchoice%5B%5D=189&amp;childforums=1&amp;exactname=1&amp;showposts=0"></Url>
<moz:SearchForm>http://ubuntuforums.org/search.php&amp;f=189&amp;forumchoice%5B%5D=189</moz:SearchForm>
<Developer>Ubuntu Argentina Loco Team; FreeDownload, spg76, faktorqm</Developer>
</OpenSearchDescription>

```

Salu2!

---

### Post by marianom on 2008-02-14
¡Qué trabajo en equipo!
Pregunta: se puede agregar para que también busque en los archivos del mailing list o utiliza algun feature propio del foro que impide agregar esa funcionalidad?

---

### Post by User21 on 2008-02-14
Usa URLs propias del foro! Pero que buena idea esa de buscar en el historial del mailing list!!! Pero puede que se pueda implementar en la barra, via Google, restringiendo las busquedas al foro! Dejame ver que onda, si se puede aplicar!
Que loco, como una simple idea se convierte en una iniciativa coordinada que genera cambios importantes en nuestras vidas! xD

---

### Post by spg76 on 2008-02-14
Lo pedís, lo tenés :)
Hice un OpenSearch para buscar en los archivos de la lista utilizando Nabble ([http://www.nabble.com/Ubuntu-Argentina-f17402.html](http://www.nabble.com/Ubuntu-Argentina-f17402.html))
Copio y pego:

```
<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/"
                       xmlns:moz="http://www.mozilla.org/2006/browser/search/">
<ShortName>Ubuntu-AR-Mail List Search</ShortName>
<Description>Plug-in para b\u00fasqueda en la lista de correo de Ubuntu Argentina Loco Team</Description>
<Image width="16" height="16">data:image/x-icon;base64,R0lGODlhEAAQAIQfAPrTyv2xSP7r4%2Fzh1%2B2TivSyqPhzO%2FyPAfqYb%2F3Kkeh4c%2Fipjv7z7P%2F59P2qO9MDA%2FzLpdomJvRHANcZGf66YfzNuf3EfPyfJ%2F7dtPVQCvZfH99PT%2F7UpP7hvPdjI%2F%2F%2F%2FyH%2BEFVidW50dS1JQ08gMTZ4MTYALAAAAAAQABAAAAVd4CeOZGmeqMgARQU8ytk0iyRlxUScx8EJwIVHMzAdLgJSRYIgIRaHhMljINkuGNOgONIYoqbJhiRgHBmkV6zUgzDKuQfARHEMInhYITUoEAgABxQpJA0UHYSJiiIhADs%3D</Image>
<Url type="text/html" method="get" template="http://www.nabble.com/forum/Search.jtp?forum=17402&amp;local=y&amp;query={searchTerms}"></Url>
<moz:SearchForm>http://www.nabble.com/forum/Search.jtp</moz:SearchForm>
<Developer>Ubuntu Argentina Loco Team; FreeDownload, spg76, faktorqm</Developer>
</OpenSearchDescription>
```

Si conocen de otro buscador mejor, avisen que vemos como lo modoficamos.

---

### Post by User21 on 2008-02-14
Parece ser ideal, mas allá de las diferencias de formato, y todo eso, pero son detalles, nada mas. Funciona de lujo, y ya fue añadido además, a la barra de herramientas! :D Gracias nuevamente!!!

---

### Post by Mataca on 2008-02-15
> **User21 said:**
> Parece ser ideal, mas allá de las diferencias de formato, y todo eso, pero son detalles, nada mas. Funciona de lujo, y ya fue añadido además, a la barra de herramientas! :D Gracias nuevamente!!!

Que bueno que esta el opensearch.!!! la verdad que se pasaron :) ahora hay q comunicarlo a todos, apoyo la moción de marianom para publicarlo en la lista.

---

