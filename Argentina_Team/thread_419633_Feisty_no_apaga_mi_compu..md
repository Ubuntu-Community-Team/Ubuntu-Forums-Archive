---
title: "Feisty no apaga mi compu."
date: 2007-04-23
forum: Argentina Team
---

### Post by valucha on 2007-04-23
[COLOR="DarkOrchid"]El tema es así.
El sabado, despues de 10 intentos falidos pude instalar feisty con el alternate cd.
Apenas la prendí después del formateo, hizo unos pitidos raros, (eraon como 4 o 5), pero después inició sin problemas y nunca mas los hizo.
El tema es que no puedo apagar la ocmpu debidamente :S.
Siempre se me va el escritorio, y se queda el fondo con el mouse trabado y la compu haciendo nada...
Y lo apago así nomás..
Tengo miedo de ***** algo si sigo hacinedo eso.
¿Qué me recomiendan?. Ya probé con [esto]("http://www.ubuntu-es.org/index.php?q=node/28630") pero sigue sin funcionar.

Le hice varias cosas como para optimizarla que aparecen en esta guia [http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html](http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html)
capas tenga algo que ver..
BUeno, espero su respuesta.
Gracias [/COLOR]

---

### Post by lugonesjoaquin on 2007-04-23
Tambien puede ser un bug de la ùltima version de Ubuntu, ¿Porque no te quedas con la version anterior? Si te andaba bien.. En todo caso instalas la anterior y desde ahi actualizas a Feisty.

---

### Post by beuno on 2007-04-23
Fijate si tiene algo que ver con esto: [http://ubuntuforums.org/showthread.php?t=419809](http://ubuntuforums.org/showthread.php?t=419809)

---

### Post by BlackHero on 2007-04-23
sudo shutdown -r now

---

### Post by valucha on 2007-04-25
[COLOR="DarkOrchid"]mmm, me parece que es algun tipo de incopatibilidad, porque instalé Kubuntu feisty e igualmente sigue mi problema.
Detodos modos aveces sì apaga :S... es cuestión de suerte jajaj[/COLOR]

---

### Post by atari130xe on 2007-04-27
Hola Valucha
el post al que hacés referencia en el tuyo es mío tuve ese problema y lo solucioné con eso pero hay un pequeño detalle EL ORDEN en el que ponés los datos:

cuando lo escribís hacélo en este orden:

apm power_off=1 (EN PRIMER LUGAR)
lp
fuse

y luego me funcionó.

suerte!

---

### Post by valucha on 2007-04-27
[COLOR="DarkOrchid"]Perooo, ahora por ejemplo tengo Kubuntu
y si le mando sudo gedit /etc/modules me dice que no està instalado, asi que supongo que serà otro comando.. o tengo que instalarlo?[/COLOR]

---

### Post by kowal on 2007-04-28
[quote=valucha]Perooo, ahora por ejemplo tengo Kubuntu
y si le mando sudo gedit /etc/modules me dice que no està instalado, asi que supongo que serà otro comando.. o tengo que instalarlo?[/quote]


En lugar de **gedit** (editor GTK de Gnome) en el entorno KDE está **kate**. O sea:

```
sudo kate /etc/modules
```

Enrealidad debería usarse kdesu y no sudo. Cuando se usan permisos de superusuario en modo gráfico es recomendable usar kdesu (o gksudo en Gnome).

---

### Post by valucha on 2007-04-28
[COLOR="DarkOrchid"]Mmmm, bueno, igualmente no funciona todavía...
¿Cuánto tiempo podré estar así sin estropear nada?
debo volver a edgy?[/COLOR]

---

### Post by atari130xe on 2007-04-28
probaste a modificar tu bios? o sea el "power management" si tenes activado o desactivado esa opcion?

---

### Post by valucha on 2007-04-28
[COLOR="DarkOrchid"]El tema es que con edgy si me apagaba...
Lo último que voy a tocar es la bios,  porque quiero primero descartar todas las posibilidades dentro de kubuntu.[/COLOR]

---

