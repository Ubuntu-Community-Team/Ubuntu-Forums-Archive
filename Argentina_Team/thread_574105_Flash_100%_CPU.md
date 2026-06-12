---
title: "Flash: 100% CPU"
date: 2007-10-12
forum: Argentina Team
---

### Post by UBUjuan on 2007-10-12
Cuando entro en una página que tiene videos de flash, ya sea youtube o video google (y otros) el cpu esta al 100%, es un problema de configuración o es normal? Digo porque cuando veo videos con el mplayer no es así, a pesar de que son videos de mayor resolución. Hay otros Thread sobre el mismo tema: [http://ubuntuforums.org/showthread.php?t=297921](http://ubuntuforums.org/showthread.php?t=297921)
[http://ubuntuforums.org/showthread.php?t=487929](http://ubuntuforums.org/showthread.php?t=487929)
[http://ubuntuforums.org/showthread.php?t=414145](http://ubuntuforums.org/showthread.php?t=414145) pero no hay respuesta, nadie sabe porqué?

---

### Post by nest on 2007-10-12
El player de flash para linux no está perfectamente desarrollado. Muchas personas tienen este problema y en muchos casos no hay solución más que aguantar hasta que hagan algo los de Adobe.

A mí por ejemplo, en muchas oportunidades, simplemente se cuelga cuando terminan los videos de youtube.

---

### Post by Oktubre on 2007-10-12
A mi me pasa lo mismo, a veces consume mucho y luego se normaliza. 
En otras ocasiones, se llega a cerrar el Firefox.

Saludos,

---

### Post by rretamar on 2007-10-12
El reproductor de Flash es un buen ejemplo de sufrir en carne propia lo que puede representar el software privativo.

¿ Falla ? Claro que sí: altísimo consumo de recursos, inestabilidad, falta de una versión decente para 64 bits, retraso en la salida. ¿ Y qué es lo que podemos hacer, como usuarios ?

No mucho:

1) Protestar por lo bajo, reiniciar el navegador cuando se congela, o pasar de flash, lo que nos privará el acceso a muchos sitios.

2) Rogar a Adobe para corrija los bugs (cuando se le antoje) o para que libere el código (una utopía...Adobe nunca mostró el menor interés por el software libre, ya que su modelo de negocios se basa en vender licencias). Al no disponer del código fuente, solo Adobe puede corregirlo/mejorarlo.

Hay una tercera opción que es intentar colaborar con los desarrolladores del player libre llamado Gnash.

Para saber más:
[http://es.wikipedia.org/wiki/Gnash](http://es.wikipedia.org/wiki/Gnash)

Saludetes ! :(

---

### Post by juanman on 2007-10-12
La version del flash player 9 para linux no es estable, recien el 1 de octubre salio la release candidate... Si bien a Adobe mucho no le interesa el soft libre, este año liberaron Flex, y tienen [un blog en el q tratan las novedades q sacan para Linux]("http://blogs.adobe.com/penguin.swf/")...

El tema de la cpu al 100%, creo q hay 2 formas de utilizar el plug in (o yo lo tengo asi):
1) En mi kubuntu de 64 bits tengo a swiftfox de 32 instalado via automatix con el plug in. La cpu no se va al 100, pero cuando se cuelga flash me cuelga el swiftfox...
2) Tambien uso el opera de 32b, pero este tiene una interfaz en el medio para el uso del plug in (ndiswrapper?), lo q hace q la cpu se vaya al 100 cuando reproduce... pero si se tilda el flash no me cuelga el programa (solo tengo q actualizar la pagina)...
La verdad q no se como hacer para decirle al navegador q forma usar, pero si se te va al 100 la cpu, seguramente estas usando esta interfaz en el medio...

Saludos

---

### Post by Hei Ku on 2007-10-13
El nspluginwrapper te permite utilizar los plugins de 32 bits en un browser de 64. Yo utilizo eso con el firefox, y hasta ahora no habia tenido problemas de ese tipo.

La otra posibilidad es que uses el Gnash, pero como no es compatible con Flash 9, no vas a poder ver los videos. De todas maneras, yo miraría el procesador en ese momento, para identificar exactamente qué es lo que se te va al 100%. Quizas con una reinstalación del plugin alcanza.

---

