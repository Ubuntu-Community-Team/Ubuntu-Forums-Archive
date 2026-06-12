---
title: "Como modificar el menu_bar_screen?"
date: 2007-12-24
forum: Argentina Team
---

### Post by anka on 2007-12-24
Bueno, mi primer post pidiendo ayuda..

Les comento, estoy modificando bastante mi escritorio (con gnome), el tema, iconos.., cosas que un hace cuando esta aburrido. Tengo ubuntu 7.04, compiz, todas esas cosas. El caso en especial es este:

Modifique el ancho de los paneles, son mas angostos, de unos 20 px's, con eso los iconos que ahi estan se acomodan solos y quedan mas chiquitos.., barbaro. Modifique la tipografia, ahora esta en 8, queda my lindo. Cambie el tamaño de los iconos de la barra de herraminetas en las ventanas de navegacion de las carpetas (salte un bug bastante estupido.., pusieron un valor como entero cuando era string)., ahora el problema. El menu principal (el de Aplicaciones/Lugares/Sistema) cuando se despliega, las opciones me quedan muy anchas, en realidad, estan igual que siempre, no varian, pero contrastan con todo lo demas. [*fotingui*]("http://img134.imageshack.us/img134/8227/screenxc1.png")

La cosa es que no se si dependen del tamaño de los iconos (aunque lo dudo porque prove con otros mas pequeños y no cambió), de algun .xml en el gconf-editor (no encontre la opcion) o del gtk.

El menu en si se llama menu_bar_screen0 en gconf-editor, si alguien me tira una ayuda o me dice donde puedo buscar (ya pase por los irc -ar, -es, gnome, etc., ubuntu-es.org y nada) le estare muy agradecido..

Thanks!!

---

### Post by thenry on 2007-12-26
hola anka , mira muy clara no la tengo pero yo los logre cambiar en el archivo gtkrc del theme que estas usando. por ejemplo en el gtkrc de mi theme al final estaba escrito esto
(gtk-icon-sizes = "gtk-large-toolbar=28,28:panel-menu=18,18:gtk-menu=18,18") sin los parentesis, los 2 ultimos valores se los cambie yo o sea el panel-menu y el gtk menu estaban en 24 y los puse en 18  y ahi me quedaron bien. 
he visto que en otros archivos gtkrc estan tambien estos valores como por ejemplo en el del theme human , fijate si lo podes cambiar o agregarle esa linea que te pase a ver si se te pueden achicar tus iconos.
espero que te sirva.
cualquier otra cosa que averigue te lo hago saber.
salu2!

---

### Post by Mauro22 on 2007-12-26
El ancho se regula solo de acuerdo al texto mas largo del menu, en este caso "Herramientas del Sistema"


Yo lo que hice fue ir cambiando los nombres de los menúes a algo mas corto :P


Cambiando, "Audio y Video" por "Multimedia" y "Herramientas del sistema" por "De Sistema"

[IMG]http://www.pic2up.net/SyNF1iz.jpg[/IMG]

Esto se encuenta en Sistema -> Preferencias -> Menú Principal


Espero que te Ayude!

---

### Post by anka on 2007-12-29
Gracias Mauro22 y thenry por responder y aportar.

En realidad yo estaba buscando variar el alto de las opciones del menu, no el ancho, eso si varia segun el largo del nombre. Quedan muy anchas con respecto a los paneles que miden 20 px's, son como el doble de ancho. vamos a ver porque estoy muy metido con la cosa grafica (ahora terminando que ande compiz en una via :P )

Gracias, vamos a seguir probando, porque en algun lugar se tiene que poder hacer (aunque hay unas cosas que con el gconf-editor no se puede hacer, dice que seran posibles en proximas versiones :( )

Saludos y gracias!!, nos vemos en el irc

---

