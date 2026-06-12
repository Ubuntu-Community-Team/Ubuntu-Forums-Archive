---
title: "Presentación de Playonlinux"
date: 2008-02-12
forum: Argentina Team
---

### Post by faktorqm on 2008-02-12
Me parecio copado compartir esto con ustedes:

Playonlinux es un programa escrito en python pensado originalmente para facilitar la instalación de programas de Windows en GNU/Linux mediante la capa de abstracción Wine, siendo que hace especial énfasis en el terreno de los juegos. PlayonLinux cuenta con una GUI muy intuitiva (usa Wxwindows bindings) que lanza distintos scripts que guian la instalación de los programas soportados, dichos scripts que pueden ser actualizados desde un repositorio mantenido por los desarrolladores de la aplicación. Entre sus caracteristicas destaca: 

* Puede usar distintas versiones de Wine para diferentes programas. 

* Simula reinicios del PC. 

* Cada programa puede ser instalado en un directorio independiente de ~/.wine. 

* Puede generar test de velocidad: GlxGears, Glxmux, etc. 

* Es posible añadir automáticamente un acceso directo al escritorio o a los menús de 

Gnome o KDE o bien al menú de PlayOnLinux. 

* También se encarga de programas como MSOffice, IE y Google Sketch Up. 

Procedimiento para añadir Playonlinux al repositorio de tu ubuntu: 

simplemente añade esetas lineas a tu archivo sources.lst 

```
deb http://playonlinux.botux.net/ gutsy main
```

Y después puedes instalarlo mediante el gestor de paquetes o bien mediante consola. 

```
sudo apt-get install playonlinux playonlinux-dosbox-support
```

FUENTE ORIGINAL: [http://www.playonlinux.com/es/news-252.html](http://www.playonlinux.com/es/news-252.html)

Salu2!

---

### Post by niko_3100 on 2008-02-12
Por que version van? es nuevo el proyecto este??

---

