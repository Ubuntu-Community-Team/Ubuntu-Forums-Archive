---
title: "[SOLVED] Novato ... Molestando =)"
date: 2008-01-01
forum: Argentina Team
---

### Post by pep0_0 on 2008-01-01
Bueno ante todo Mis Saludoss a Todos en este Foro 

Bueno la verdad que cansado de Wind-us y devido a que arranco la carrera de Sistemas me viene perfecto aprender ...
La cosa es que Instale Ubuntu y no quiero desanimarme pero me surgieron un par de problemas ..
No me reconocio el mouse serial y ya se que no es algo nuevo pero la cosa es que no se como, ni donde, coloco una linea de comandos para modificar el problema :confused::confused::confused:

Aclaro que no conozco nada de linux (ubuntu) asiq les pido ayuda

Desde ya Muchas Gracias !

---

### Post by lordpuppet on 2008-01-01
A mi tampoco me reconocía el mouse serial, pero dejé de usarlos hace mucho por que realmente son muy viejos, de cualquier forma buscando un poquito por google salen las respuestas,

[http://www.google.com.ar/search?q=mouse+serial+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:es-AR:official&client=firefox-a](http://www.google.com.ar/search?q=mouse+serial+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:es-AR:official&client=firefox-a)

Nota, para editar el archivo "/etc/X11/xorg.conf" poné en el terminal

```
sudo gedit /etc/X11/xorg.conf
```

Con "sudo" estas identificandote como superusuario (luego te pide la contraseña) y Gedit es el comando para que abra el archivo xorg.conf con el editor Gedit.

---

### Post by User21 on 2008-01-02
SI eres nuevo y dispones de una buena conexión a Internet, y una vez hayas solucionado el problema del mouse, puedes conseguir ayuda en [http://www.guia-ubuntu.org](http://www.guia-ubuntu.org) o en [http://doc.ubuntu-es.org](http://doc.ubuntu-es.org) !

** SUERTE, BIENVENIDO y FELIZ 2008 Junto a Ubuntu!**
Si no te das por vencido en los primeros meses (esperemos que no) verás que buena comunidad hay detrás de todo esto, y qué satisfacción dá usar Software Libre! :) 

Te esperamos, de todas formas en* irc.freenode.net *, en la sala de *#ubuntu-ar*. Si aún no instalaste ningún cliente irc, podes ingresar desde [http://www.ircatwork.com](http://www.ircatwork.com) !

---

### Post by tzulberti on 2008-01-02
> 
Nota, para editar el archivo "/etc/X11/xorg.conf" poné en el terminal

```
sudo gedit /etc/X11/xorg.conf
```

Con "sudo" estas identificandote como superusuario (luego te pide la contraseña) y Gedit es el comando para que abra el archivo xorg.conf con el editor Gedit.

En vez de editar el archivo a mano podes usar el comando:
```
 sudo dpkg-reconfigure xserver-xorg 
```

te directamente es un "wizard" (pero muy bueno a diferencia de los de Windows). En algun momento te pregunta a que puerto esta conectado tu mouse. Despues, para reinicar el X (Gnome) y ver si lo configurastes bien escribi:
```
 sudo /etc/init.d/gdm restart 
```

---

### Post by pep0_0 on 2008-01-02
Bueno Gracias por la Ayuda y las racomendaciones, pero la cosa es me surgio el siguiente problema 

Al ir a la terminal (Ctrl+Alt+F1) si es que es la mejor forma de acceder me pide antes que nada que me Loguee y lo que me pasa es que puedo poner el pass

Aclaro que luego de poner el nombre de usuario presiono Enter, aviso ...

Gracias !

---

### Post by facundocorradini on 2008-01-02
no, con "abri un terminal" nos referimos a que vayas a aplicaciones-->accesorios-->terminal.

---

### Post by pep0_0 on 2008-01-02
> **facundocorradini said:**
> no, con "abri un terminal" nos referimos a que vayas a aplicaciones-->accesorios-->terminal.

Gracias por responder, pero sin el mouse no se como acceder a APLICACIONES, lo veo arriva a la izquierda pero no se como aceder sin poder usar el mouse, solo con el teclado

---

### Post by faktorqm on 2008-01-02
apreta ALT + F2, y te aparece un cuadro para ejecutar un comando. ahi escribis "xterm" (asi se llama el programa que es la terminal para entorno grafico) y listo el pollo. salu2!

---

### Post by pep0_0 on 2008-01-02
[SIZE="4"][COLOR="Red"]

Muchisimas Gracias a todos los que colaboraron con mi pequeño tropiezo con la iniciacion de explorar Linux UBUNTU, les cuento que mi Mouse ya Anda !!!!   :):):)  y les aviso que no sera la ultima vez que me veran por aca !!! 

GRACIAS !!!!

[/COLOR][/SIZE]

---

### Post by faktorqm on 2008-01-02
ke bueno, segui preguntando. salu2 y suerte!

---

### Post by tzulberti on 2008-01-03
> **pep0_0 said:**
> 

Al ir a la terminal (Ctrl+Alt+F1) si es que es la mejor forma de acceder me pide antes que nada que me Loguee y lo que me pasa es que puedo poner el pass

Gracias !

En linux cuando estas en consola, nunca vas a ver la contraseña que escribis. Ese puede llegar a ser tu problema. Es decir, cuando ingresas el nombre de usuario, y te pide la contraseña por mas de que escribas no vas a ver nada pero la estas escribiendo...

Decime si ese era tu problema.

---

### Post by vk-cdg on 2008-01-03
> **pep0_0 said:**
> [SIZE="4"][COLOR="Red"]

Muchisimas Gracias a todos los que colaboraron con mi pequeño tropiezo con la iniciacion de explorar Linux UBUNTU, les cuento que mi Mouse ya Anda !!!!   :):):)  y les aviso que no sera la ultima vez que me veran por aca !!! 

GRACIAS !!!!

[/COLOR][/SIZE]

Marcá el post como [Solved] ya que el problema se solucionó. Lo hacés desde el menú Threads Tools arriba a la derecha.
Preguntá lo que quieras o necesites, para eso estamos, pero recordá, para tener una mayor participación en el topic de poner un tútulo que sea representativo del problema y de hacer un topic por cada problema de diferente magnitud.

---

### Post by pep0_0 on 2008-01-03
> **tzulberti said:**
> En linux cuando estas en consola, nunca vas a ver la contraseña que escribis. Ese puede llegar a ser tu problema. Es decir, cuando ingresas el nombre de usuario, y te pide la contraseña por mas de que escribas no vas a ver nada pero la estas escribiendo...

Decime si ese era tu problema.

Si, ese era parte del problema, Gracias.

---

