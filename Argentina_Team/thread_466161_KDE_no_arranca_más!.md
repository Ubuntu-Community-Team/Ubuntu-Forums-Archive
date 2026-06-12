---
title: "KDE no arranca más!"
date: 2007-06-06
forum: Argentina Team
---

### Post by manzuk on 2007-06-06
YA ESTA RESUELTO POR SUERTE. El problema era que no había espacio libre en el home (maldito Ktorrent)
----------------------------------------------------

Gente, ayer estaba lo más tranquilo usando la PC (Ktorrent, Amarok, y eso) cuando quise abrir el aMSN. Por alguna razón desconocida no queria arrancar. Aunque algo de Linux se, no soy muy pro, asi que lo único que se me ocurrió fue lanzarlo desde la consola para ver si me tiraba algún error o algo, pero nada... La consola quedaba ahí sin hacer nada. El proceso "wish" (que es algo asi como el GUI de Tcl/Tk creo) arrancaba, pero el aMSN bien gracias.

En fin, necesitaba conectarme, asi que a lo bestia dije "Aja! Voy a reiniciar y todo funcionará como dios manda". El tema es que cuando inició, cargó el KDM diez puntos, pero cuando metí mi info de login y le dí al enter, se puso como para iniciar el KDE, pero volvió a el KDM. Y de ahí no salió, amagando arrancar el KDE, pero volviendo a la pantalla de KDM.

Intenté meterme en una consola, loguearme y mandar un ```
startx
```, pero tampoco funcionó. Un error de X. Probé también ```
sudo startx
``` y ese llegó más lejos. Por lo menos vi la pantalla de "Iniciando KDE" pero nada más, ahi se clavó.

El incidente fue ayer a la noche. Probé hoy a la mañana y seguía pasando lo mismo. Con versiones anteriores me pasaba a veces que no iniciaba el X y me decia algo de que no tenía derechos sobre un archivo, pero con unas horas de descanso la PC se tranquilizaba y arrancaba de nuevo :D

No se que puede estar pasando; es una instalación relativamente nueva de Feisty. A alguién le pasó o tiene una idea? Gracias gente.

---

### Post by Al_maverick on 2007-06-06
Fijate que dice el log de X. Deberia estar en /var/log/x11.log.0

Postealo aca, quizas te podamos dar una mano. Cuando lo tratas de arrancar a mano desde la consola tira algun error?

---

### Post by Sicarul on 2007-06-06
Me parece que mas bien es /var/log/Xorg.0.log

---

### Post by gepatino on 2007-06-07
Proba de eliminar lo que haya en /tmp, en definitiva son solo archivos temporales. Puede ser que hay quedado algun archivo con configuraciones temporales por ahi dando vueltas, y eso esté generando el problema.

También verifica que tengas espacio libre en disco. Un motivo comun para que el X no inicie es quen o haya lugar en la particion donde esta el home del usuario, y a veces al colgarse el X se genera un Xerrror dentro del home del usuario que en algunos casos puede ocupar unos cuantos gigas (solo me paso una o dos veces, pero pasa).

---

### Post by manzuk on 2007-06-07
Justamente era eso, el espacio en disco! Lo hice andar ayer a la noche, pero no tuve tiempo de postear todavia. Aparentemente con las cosas que me estaba bajando con el Ktorrent, se me llenó el home y por eso no arrancaba. Borré una maquina virtual que tenia al **** total y el KDE inicio de diez.
La pregunta es, donde puede generar X esos archivos de erro super pesados? No vaya a ser que los tenga y ni me haya dado cuenta.

En fin, tema resuelto por suerte. Gracias a todos por los tips igual.

---

### Post by gepatino on 2007-06-07
los archivos de error deberian estar en tu home, pero ocultos (empiezan con un punto)

Me parece que el nombre del archivo es .xsessionerrors o  .xerrors

El resto de los archivos (y directorios) que comienzan con un punto, dejalos en su lugar porque son la configuracion de tu sesion y programas.

---

### Post by el_itur on 2007-06-07
solamente para aportar. lo de startx ya no se usa salvo para un entorno en donde no tenes un entorno gráfico (valga la redundancia). Por ejemplo. NO usas ni kde ni gnome ni xfce. Para eso inicias las x y algun script  que te levante tu manejador  de ventanas favorito y algunas herramientas mas.
Si tenes un entorno gráfico lo mejor es correr las X desde el gestor de display de ese entorno. El de KDE es KDM, así que en vez de tirar startx tiras /etc/init.d/kdm start o restart o lo que sea.

Esto no ubiese solucionado tu problema. Pero está bueno tener en cuenta cual es la manera correcta de hacerlo.

Me alegro que te hayas manejado para solucionar el temita.

---

