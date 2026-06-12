---
title: "administracion remota"
date: 2008-02-25
forum: Argentina Team
---

### Post by Mauro22 on 2008-02-25
Hola! Como andan??



Tengo una consulta y quiero saber si alguien me puede ayudar (o explicar).

Ayer convenci a dos personas de pasarse a linux (tras haber perdido toda la info del xp por un error).


Ahora bien, para los que recien empiezan resulta "confuso" y las explicaciones a distancia no son muy practicas.


Como se puede hacer para "ver el escritorio" de la otra pc. Algo como la utilidad que trae XP.
Estoy seguro que se puede, pero como?

Estuve leyendo algo pero se me complica...



:guitar:
Mil gracias al que se tome tiempo para contestar

---

### Post by euzkoarima on 2008-02-25
Hola, te contesto de memoria xq estoy en un cyber con ventantas, pero en el menu de aplicaciones -> internet -> escritorio remoto. Ahi tenes varias opciones de conexion, supongo que la que queres vos es rdp (o rdp5) al menos eso es lo "nativo" en xp hasta donde yo se (nunca use ventanas como mi sistema operativo principal).
Otra que pueden estar usando es vnc, que tambien es una opcion del programa.
Suerte

---

### Post by newtonfn on 2008-02-25
Ubuntu biene por default con VINO que es un servidor de VNC que te permite ver y/o manejar la pantalla a distancia.

Para activar esta administración debes ir a Systemas-Preferencias-Administración Remota. (en la pc que querés manejar)

Al entrara verás una ventana, ahí debes activar las opciones de permitir ver el escritorio, si lo quieres también el de permitir controlarlo e ingresar una contraseña.

Luego, desde cualquier pc con VNC (Ubuntu lo tiene en su Terminar Server Client o más directamente en la linea de comando con vncviewer <ip>, y en Windows puedes buscarlo en Google que es una descarga gratuita el RealVNC u otro similar) te puedes conectar a la pc remota, ingresar la contraseña y listo.

El unico detalle, debe haber un usuario logueado en la PC remota, ya que de esta manera simple no podes controlar la ventana de GDM.

Adjunto una ventana de como tengo yo configurado mi administración remota.

[ATTACH]60830[/ATTACH]

---

