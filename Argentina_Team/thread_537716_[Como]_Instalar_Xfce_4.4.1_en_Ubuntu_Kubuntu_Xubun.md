---
title: "[Como] Instalar Xfce 4.4.1 en Ubuntu Kubuntu Xubuntu 7.04 Feisty Fawn"
date: 2007-08-29
forum: Argentina Team
---

### Post by LikeVinyl on 2007-08-29
Hola amigos!

Hoy vamos a aprender "Cómo&#8221; instalar, de manera gráfica, la última versión del súper ligero manejador de escritorio Xfce; Es probable que muchos de nosotros nos hayamos iniciado con los conocidos Gnome o Kde pero gracias al pluralismo del movimiento GNU, podemos disfrutar más de un sabor a la hora de utilizar nuestro ordenador.

"Xfce es un ambiente de escritorio ligero para varios sistemas *NIX. Diseñado para la productividad, carga y ejecuta aplicaciones rápidamente preservando los recursos del sistema." - Olivier Fourdan, creador de Xfce.

Ubuntu 7.04, a través de sus repositorios oficiales, nos permite instalar Xfce 4.4.0 pero tal y como indicamos al comienzo instalaremos Xfce 4.4.1. Esta última versión, no trae grandes cambios visibles, nos brinda la posibilidad de lanzar una instalación gráfica que compila el paquete automaticamente haciendo que el entorno aproveche al ciento por ciento las capacidades físicas de nuestro ordenador y es con esta última funcionalidad que vamos a notar un magnífico desempeño.

Manos a la obra!

**Preparando nuestro sistema**

Lo primero que haremos será instalar las dependencias necesarias para evitar mensajes de error cuando iniciemos la instalación y/o durante la compilación.

Entonces, utilizar una terminal dentro de X e invocar el siguiente comando:

```
$ sudo aptitude install build-essential libglib2.0-dev libgtk2.0-dev libxml-dev libvte-dev libstartup-notification0-dev libhal-storage-dev libdbus-glib-1-dev libxrender-dev libxdamage-dev libjpeg62-dev libxml++2.6-dev
```

    * Recordar no incluir el signo $ ya que solo es utilizado para representar nuestro home.

**Descargando Xfce 4.4.1**

Una vez terminada la instalación, descargar el instalador gráfico con el siguiente comando desde una terminal dentro de X:

```
$ wget [http://mocha.xfce.org/archive/xfce-4.4.1/installers/xfce4-4.4.1-installer.run](http://mocha.xfce.org/archive/xfce-4.4.1/installers/xfce4-4.4.1-installer.run)
```

**Instalación**

Lanzar la instalación con el siguiente comando en un terminal, dentro de X:

```
$ sudo sh xfce4-4.4.1-installer.run
```

    * Recordar no incluir el signo $ ya que solo es utilizado para representar nuestro home.

Luego que finalice la descompresión -representada por un millón de puntitos- veremos una pantalla de bienvenida; Luego de pulsar ""next", hará una verificación de dependencias e indicará si falta alguna de ellas con una marca roja, si todo es correcto las marcas de verificación serán verdes, entonces pulsar "next" nuevamente.

**Opciones de instalación**

Marcar las siguientes opciones:

   1. Extensive Optimizations
   2. Setup Display Managers

Muy Importante: NO SELECCIONAR "Use ALSA for the Xfce Mixer" pues ya se encuentra instalado por defecto en Ubuntu; Si seleccionamos esta opción, es posible que ocasione un daño en la configuración actual.

Por defecto, la carpeta de instalación es /usr/local/

Como leímos al comienzo, el instalador compilará todos los paquetes y este proceso puede llevar entre 10 y 20 minutos dependiendo de nuestro sistema; Al completar la instalación, solo resta finalizar la sesión actual y en la pantalla de inicio de sesión seleccionar "xfce4" para probar este nuevo manejador de escritorio.

**Detalles:**

    * Si deseamos quitar Xfce, es muy fácil, seleccionar "software uninstaller" situado en sistema.

    * En nuestro inicio de sesión gdm, es posible que haya dos entradas para Xfce4 pero ambas apuntan a Xfce 4.4.1 -esto es así para evitar conflictos en caso que en el futuro querramos quitar Xfce 4.4.1 e instalar Xfce 4.4.0 incluído en nuestro Ubuntu 7.04 Feisty Fawn.

    * Si estamos utilizando Xubuntu 7.04 -Ubuntu con Xfce- por defecto, la versión que utiliza es la 4.4.0 por tanto este procedimiento también es válido para dicha versión-

    * Los usuarios de Kubuntu que no tengan GTK+ deberán instalar los paquetes requeridos.

    * Xfce 4.4.1 puede ser utilizado con la última versión de compizfusion o beryl con grandes resultados por arriba de gnome o kde.

**Notas finales**

Esta guía fué probada con el siguiente hardware:
Intel Pentium 4, 1gb Ram, Video  Geforce  FX5200.

Aquí terminamos, solo queda disfrutar nuestro nuevo manejador de escritorio.

Un gran abrazo a todos y hasta la próxima!

Fuentes y más información:
[http://www.xfce.org]("http://www.xfce.org")

::: LikeVinyl :::
Este documento es Copyleft, Miguel Angel Ríos, 2007
Tienes la Libertad de copiar, modificar y distribuír los contenidos de este documento.

---

### Post by por100pre1 on 2007-08-29
=D> ¡Excelente! Gracias. :)

---

### Post by rojojuan on 2007-08-29
Ví que Synaptic tiene la posibilidad de instalar XFCE directamente; no lo instalé pero ví que se puede hacer automáticamente (te marca todo lo necesario para instalarlo. Sería así más fácil o tendría problemas?

---

### Post by ubuntu27 on 2007-08-29
> **rojojuan said:**
> Ví que Synaptic tiene la posibilidad de instalar XFCE directamente; no lo instalé pero ví que se puede hacer automáticamente (te marca todo lo necesario para instalarlo. Sería así más fácil o tendría problemas?

es mas facil instalar desde el repositorio (con el terminal o synaptic)

aqui esta el comando para el terminal:

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

si deseas, haslo con Synaptic. Aunque yo recomiendo usar el terminal y instalar con synaptic.

---

### Post by LikeVinyl on 2007-08-29
> **rojojuan said:**
> Ví que Synaptic tiene la posibilidad de instalar XFCE directamente; no lo instalé pero ví que se puede hacer automáticamente (te marca todo lo necesario para instalarlo. Sería así más fácil o tendría problemas?

En realidad, esta guía sirve para instalar la última versión de Xfce (4.4.1). Si deseas instalar, desde los repositorios la versión previa (4.4.0.) puedes utilizar synaptic, aptitude o apt-get. -pero instalarás una versión más antigua-

Un abrazo :)

---

### Post by LikeVinyl on 2007-08-29
> **ubuntu27 said:**
> es mas facil instalar desde el repositorio (con el terminal o synaptic)

aqui esta el comando para el terminal:

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

si deseas, haslo con Synaptic. Aunque yo recomiendo usar el terminal y instalar con synaptic.

Por favor, permitíme corregirte, esta guía sirve para instalar la última versión (4.4.1) y tu comentario sirve para instalar, desde los repositorios, la versión previa (4.4.0.) Atención a los títulos ;)

Un abrazo.

---

### Post by ubuntu27 on 2007-08-30
Gracias LikeVinyl por el How-to. 

y que hay de nuevo en Xfce 4.4.**1** ? 

La gente nueva no debe de complicarse la vida por pequenyos cambios :D

---

### Post by LikeVinyl on 2007-08-30
> **ubuntu27 said:**
> Gracias LikeVinyl por el How-to. 

y que hay de nuevo en Xfce 4.4.**1** ? 

La gente nueva no debe de complicarse la vida por pequenyos cambios :D

Hola Ubuntu27!

Gracias a vos; Relacionado con Xfce 4.4.1, creo que no has leído detenidamente el tutorial. De todos modos, te comento que sí hay grandes cambios relacionados con el desempeño, soportes y corrección de unos cuantos errores. Sería ideal no agregar comentarios sin antes probar el tutorial ya que de esta forma, se confunde al nuevo usuario y creo que la idea es acercar, incentivar o informar sobre las posibilidades que ofrece el software libre. 

Por otro lado, todos tenemos la Libertad de probar todo lo que deseemos probar si nos sentimos seguros con el apoyo de todos los integrantes de la comunidad. Lo demás, solo son apreciaciones personales que no vienen al caso.

Sin otro particular, me despido atte.

Aquí está la lista de cambios, me diras si existen o no cambios importantes. 

[http://www.xfce.org/documentation/changelogs/4.4.1]("http://www.xfce.org/documentation/changelogs/4.4.1")

Un abrazo!

Fuentes: 
[http://www.xfce.org/]("http://www.xfce.org/")

Este documento es copyleft, Miguel Angel Ríos, 2007
Tienes la Libertad de copiar, modificar y distribuír los contenidos de  este documento.

---

### Post by por100pre1 on 2007-08-30
> **ubuntu27 said:**
> Gracias LikeVinyl por el How-to. 

y que hay de nuevo en Xfce 4.4.**1** ? 

La gente nueva no debe de complicarse la vida por pequenyos cambios :D

Creo que LikeVinyl ya habia aclarado en su HOW-TO (o guia de como hacer algo) que los cambios son visualmente minimos y que son fundamentalmente internos. Ademas, lamento tener que informarte que persistir en argumentar en un HOW-TO se considera un atraco al mismo ([hijacking a how-to]("http://ubuntuforums.org/showthread.php?t=537149")), y se considera una falta de cortesia en los Foros de Ubuntu.

---

### Post by ubuntu27 on 2007-08-30
Ah, perdon por no leer bien lo que decia en el How-to :D
NO me habia dando cuenta que era una nueva version. :)

Bueno, suerte. Y gracias por crear un how-to. Eso ayuda a muchos..

De cierto, LikeVinyl:  los comandos de terminal, ponlo en un cuadro para que se vea mejor (atractivo, y no se pierden)

[ CODE] codigo [/ CODE]


```
este es un codigo
```

Y veras que se vera hermoso. :)

---

### Post by LikeVinyl on 2007-08-30
> **ubuntu27 said:**
> Ah, perdon por no leer bien lo que decia en el How-to :D
NO me habia dando cuenta que era una nueva version. :)

Bueno, suerte. Y gracias por crear un hwo-to. Eso ayuda a muchos..

De cierto, LikeVinyl:  los comandos de terminal, ponlo en un cuadro para que se vea mejor (atractivo, y no se pierden)

[ CODE] codigo [/ CODE]


```
este es un codigo
```

Y veras que se vera hermoso. :)

Ahora sí nos entendemos; Verás que escribo para muchos sitios y cada foro tiene funcionalidades diferentes. ;) Muchas gracias por el aporte. 

Un abrazo.

---

