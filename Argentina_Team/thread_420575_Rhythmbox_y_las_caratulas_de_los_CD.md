---
title: "Rhythmbox y las caratulas de los CD"
date: 2007-04-23
forum: Argentina Team
---

### Post by loopeando on 2007-04-23
Hace unos meses cuando mi SO primario era Windows XP disfrutaba de iTunes y mas que nada de Cover Flow. Por lo tanto toda mi coleccion de mp3, 20GB+, esta con todos sus tags de forma inmaculada con la portada del album en una resolucion digna.

El tema es que hace poco me di cuenta que Rhythmbox en la seccion Complementos tiene una funcion que muestra la portada del CD y yo pense lo mas logico, que me lea el Cover Art del tag, pero no, los lee de Internet y por lo general estan erroneos o bastante pixelados.

¿Hay alguna manera de hacer que Rhythmbox lea el Cover Art de los tags ID3 en lugar de inet?

Desde ya, gracias!

P.D: Ando medio "difuso", si no se entiende algo avisenme.

---

### Post by lugonesjoaquin on 2007-04-23
Ni idea che.. Nunca eh usado ni iTunes ni Rhimbox, ¿Has probado con Amarok?

---

### Post by loopeando on 2007-04-23
Si, probe Amarok, Listen y Exaile pero como estoy familiarizado con iTunes, Rhythmbox es lo mejor para mi.

---

### Post by lugonesjoaquin on 2007-04-23
Por ahi leí que con Wine el iThunes anda de 10. Pero tambien lei que no anda.. Asi que .. Podrias probar no sé

---

### Post by marianom on 2007-04-23
Rhythmbox está buenísimo.
Anyway, estuve viendo tu problema: La existencia de un archivo llamado LocalCoverArtSearch.py en /usr/lib/rhythmbox/plugins/artdisplay (es python así que lo podés investigar) me da la pauta certera que se puede hacer lo que vos querés. Ahora, hacerlo de forma más fácil que meterse en el código fuente no veo la opción a simple vista.
Le voy a echar un ojo a estos files a ver que saco en concreto.

Si descubro algo digno te aviso.

---

### Post by loopeando on 2007-04-23
Interesante hallazgo Mariano.

Me voy a poner a meter mano por ahi a ver si logro algo.

Desde ya, gracias!

---

### Post by Tinchio on 2007-04-23
Amarok te muestra los covers, te da info de los temas, de muestra la letra de la cancion, te manda a la wiki de la banda, y mucho mas
[http://amarok.kde.org/](http://amarok.kde.org/)
probalo la verdad q es un muy buen reproductor, de lo mejor

---

### Post by sebas.rhcp on 2007-04-23
Los programas que funcionan mejor con KDE, arruinan la estetica cuando se los instalan en gnome... al menos en los que vi hasta ahora. Hay muchos programas nuevos de edicion (musica, sonido y video) la gran mayoria para KDE.

¿Es ese el caso de amarok tambien o se integra bien a gnome? (No se nota que uso el agregar/quitar programas, no?) :)

---

### Post by loopeando on 2007-04-24
Programas de KDE como Amarok no, porque aparte de arruinar la estetica, tienen que cargar librerias de KDE

---

### Post by kowal on 2007-04-24
**Amarok es EL reproductor**. No hay en otra plataforma algo que le haga aunque sea un poco de sombra. De hecho, conozco varias personas que se quedan en GNU/Linux cuando descubren las características de Amarok.

---

### Post by loopeando on 2007-04-24
Amarok es un gran reproductor. Es mas, si usase KDE probablemente usaria Amarok, pero como la interfaz GNOME es mi eleccion no me sirve Amarok ya que desentona con el resto del escritorio y tiene que cargar librerias extra.

Estuve probando Banshee. Muestra mis caratulas perfecto, pero el resto de los tags de todos mis mp3 les agrega comas. Quedan asi los tags en Banshee:

[IMG]http://img261.imageshack.us/img261/482/pantallazoox3.png[/IMG]

Con un exceso de comas en toda mi fonoteca.

Si alguien sabe como solucionar este problema me paso a Banshee. Caso contrario sigo renegando con Rhythmbox, porque editar de nuevo toda mi coleccion de mp3's no lo hago ni en ****.

Gracias!

---

### Post by sdm_cacto on 2007-04-24
Yo uso Gnome, una de las grandes razones por las q me pase a linux es AMAROK y realmente no hay mejor software de audio q éste, nose, lo unico q le agregaria es algo q "tunee" el sonido onda Jammix de winamp.

Alguien tiene idea de lo q hablo?? porq me parece q me explayé para el *** pero bueno, dsp posteo mejor

besitos

---

### Post by loopeando on 2007-04-24
Se entiende perfecto, pero aclaro por tercera vez

[SIZE="4"][SIZE="5"]AmaroK NO![/SIZE][/SIZE]

Gracias por su atencion.

---

### Post by sdm_cacto on 2007-04-24
OK tenes razon, te voy a responder...

La unica forma q conozco es q copies la tapa del disco a la carpeta donde esta el tema en particular, con el cnombre cover.jpg, es super engorroso pero es la unica forma q conozco. Vos decis q iTunes copia las tapas a la etiqueta??

---

### Post by marianom on 2007-04-24
sdm_cacto tiene razón de acuerdo al [FAQ]("http://live.gnome.org/Rhythmbox/FAQ") de la aplicación:
> Where are lyrics and artwork stored?

Lyrics are stored in ~/.lyrics and artwork in ~/.gnome2/rhythmbox/covers

From where is artwork fetched?

Rhythmbox uses Amazon to look up artwork. Depending on your locale, a different mirror is used. Currently supported are en_US, en_GB, de and jp.

If you have local image files, saved in the same directory as the album with the filename "cover, album, albumart, .folder or folder Rhythmbox will use them instead of looking up a cover on Amazon.

Covers embedded in songs are currently not supported.

(aunque a mi las instrucciones me parecen mal escritas y no entiendo exactamente que están tratando de decir).

---

### Post by loopeando on 2007-04-25
> Covers embedded in songs are currently not supported.

Eso responde mi pregunta inicial.

Gracias de todas formas!

---

### Post by sdm_cacto on 2007-04-25
OK, pero igual fijate q hay buenas alternativas a Rythmbox que corren en gnome, y son muy buenas, por ejemplo Listen!, Banshee y Exaile

---

