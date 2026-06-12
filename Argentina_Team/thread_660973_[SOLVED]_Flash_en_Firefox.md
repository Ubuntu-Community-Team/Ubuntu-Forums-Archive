---
title: "[SOLVED] Flash en Firefox"
date: 2008-01-07
forum: Argentina Team
---

### Post by vk-cdg on 2008-01-07
Buenas, al principio pensé que iba a ser cosa de 5 minutos pero me está costando mas de la cuenta.

La consulta es simple, cuando instalé Gusty puse como reproductor flash el gnash. El problema es que algunas web no me andaban bien así que lo desinstalé e instalé el flash player de Macromedia. La cosa es que al navegar una web con flash me sigue pidiendo que instale el flash, hago todos los pasos y nada, lo sigue pidiendo.

Probé desinstalar el flash player, reinstalarlo, quité el gnash, pero nada, el Firefox no toma como reproductor o plugin flash al Flash player.

Estuve mirando pero no encuentro en el Firefoz donde cambiar la asociacion de pligins

---

### Post by faktorqm on 2008-01-07
bajate el flash de la pagina de adobe, descomprimilo y te aparecen 2 o 3 archivos nada mas. agarra el que se llama flashpalayerplugin.so (o similar, igual hay un solo .so, so significa static option, vendrian a ser como las dll's en güindous) y lo pegas en la carpeta
"/usr/lib/firefox/plugins". abris el firefox y listo. (necesitas permisos de administrador para escribir, asi que podes hacer "sudo nautilus" o konqueror o thunar o el que vos kieras)
salu2!

---

