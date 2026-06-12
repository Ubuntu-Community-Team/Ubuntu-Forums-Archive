---
title: "Mi SO se ve horribleeeeeeee !!"
date: 2008-04-27
forum: Argentina Team
---

### Post by leonardo83 on 2008-04-27
buenas gente, hice macana y no se con que, pasa que estaba tratando de correr los efectos de compiz en ubuntu 7.10 con mi placa (riva tnt2 que aun no se si se puede o no) y cuestion que instale algo de los xorg por la info de un foro... apt/get install xorg, eso lo que me pidio es reinciar la pc, a partir de ahi nada fue lo mismo, el escritorio se ve como si le faltaran pedacitos de pixeles, por decirlo de alguna manera, cualquier opagina de internet carga pero por ejemplo es como si se colgara la palabra a buscar o aparecen como manchas, ya desinstale eso con lo mimso pero remove xorg, lo saco pero esto sigue, no se ve como antes!!!
tengo que cargar de nuevo el escritorio o que hago_
Les pondria una foto pero ni idea como se hace, ademas por ejemplo y con el cursor marco toda l apantalla apretando el boton izq, se ve como cuadritos vacios, como si estuviera andando mal gnome, que se yo. :(:(:(

si necesitan mas data porque no le paso a nadie avisenme.Gracias, saludos

---

### Post by sajnox on 2008-04-27
Generalmente cuando el xorg.conf se reconfigura hace un autobackup, por lo que en la carpeta /etc/X11/ debe haber varios archivos xorg."algo mas" podes probar renombrandolos a xorg.conf y reiniciar x ( ctrl + alt + backspace )

La otra que es realidad la que yo probaria es ejecutar en una consola

```
sudo dpkg-reconfigure -phigh xserver-xorg 

```
Este comando deberia detectar la placa y el monitor (entre otras cosas) y reconfigurar todo a como "se debe"

Despues de ejecutarlo tener que reiniciar las x para ver que settings tomo

---

### Post by leonardo83 on 2008-04-27
NOOOOO!!!!

No se que paso man pero lo unico que hice fue probar eso que me dijiste de apretar ctrl+alt+backspace y se puso todo negro y volvio a la pantalla de login (?) y cuando cargo mi user piensa un rato... y vuelve a la pantalla que me pide user, no ingresa nunca !!!!!!!!!

Tuve que entrar desde una terminal a prueba de fallos de gnome pero no se como arreglarlo, me parece que la embarre mas!!

Ayudaaaaa!! :(:(:(:(:(

NOTA: me fije en etc/x11 y em aparecen los archivos:
xorg.conf, xorg.conf.20080427221812 y xorg.conf.20080427223833 (????)

---

### Post by Hei Ku on 2008-04-27
ctrl+alt+backspace reinicia el X, asi que esta bien que te vuelva a la pantalla de login. El tema es si probaste reconfigurarlo, o volver a un backup anterior, copiando sobre el /etc/X11/xorg.conf

---

### Post by leonardo83 on 2008-04-27
No hice un backup porque ni idea com se hace eso.
QUe me aconsejas que haga?
Tengo que usar el xorg.conf de que manera? La verdad que no se mucho asi que no se como modificarlo :(

---

### Post by Hei Ku on 2008-04-27
segui las instrucciones de sajnox. paso a paso, no por partes.

---

