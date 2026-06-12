---
title: "Problema con Ubuntu Studio"
date: 2007-05-15
forum: Argentina Team
---

### Post by Gasker on 2007-05-15
Hola, les cuento que instale el Ubuntu Studio, todo bien, sin problemas, pero cuando reinicia la pc despues de terminar la instalacion, es como que quiere entrar a GDM y se muere el monitor, intente de todo pero no pude hacer andar, tengo una placa madre DFI AD77 Infinity, con una placa de video Nvidia FX 5200.

trate de editar el xorg.conf pero no hay caso, me imagino que sera que no tengo instalado los drivers de nvidia o no los tengo activados.

Por ahi lei que se puede borrar el xorg.conf y que reiniciando se regenera nuevamente pero no me animo, alguien sabe algo?

desde ya muchas gracias,

---

### Post by Al_maverick on 2007-05-15
anda a la linea de comando y reconfigura el xorg.conf

```
sudo dkpg-reconfigure xserver-xorg
```

Por supuesto, hace backup del xorg.conf antes.

---

### Post by Gasker on 2007-05-15
gracias por responder, te cuento que ya intente hacer eso, y en la lista de drivers no figura nvidia, solo figura nv, que me imagine que seria el driver de nvidia, pero despues de reconfigurar el xorg.conf, cuando reinicio la pc, me sale un error.
La verdad es que no se que mas hacer.

---

### Post by Al_maverick on 2007-05-15
te diria que lo hagas arrancar con el driver vesa. asi una vez adentro del X podes ver mejor cual es el problema.

Ese seguro tiene q estar en la lista. Capaz que no te instalo los drivers nvidia o algo similar.

---

### Post by lavaramano on 2007-05-15
proba con los drivers nv, que son los libres de Nvidia (tengo entendido) para arrancar al menos.
y sino tb podes elegir vesa que son los genericos y tb probablemente te funcionen.
 
[http://ubuntuforums.org/showthread.php?t=80314](http://ubuntuforums.org/showthread.php?t=80314)
fijate ahi, que explican basicamente como hacerla funcionar
suerte con eso.

---

### Post by guillermolisi on 2007-05-17
Gasker

Tengo la imagen ISO del Ubuntu Studio en el disco, casi 900 Mb con lo cual no entra en un CD de 700Mb maximo. Lo quise grabar en un DVD y no me habilita el boton de Burn (estoy usando K3b para grabarlo bajo Ubuntu 7.04 Server con KDE). Consulte en la wiki de Ubuntu Studio y efectivamente se genera un DVD de inicio.

Probe con otros archivos que no son ISO y no tuve problemas con DVD.
A vos te paso algo similar ?

Luego, llegaste a probarlo como para decir si vale la pena o no ?


Gracias y saludos

---

### Post by Gasker on 2007-05-18
guillermo, te cuento que yo grabe el ubuntu studio desde la windola, con nero, efectivamente en un DVD y no tuve problemas, lo grabo bien y todo perfecto.

Con respecto a si vale la pena o no, te cuento que yo soy cineasta y hace un tiempo ya habia empezado a migrar a linux, a medida que las aplicaciones para mi rubro iban progresando.
El Ubuntu studio esta pensado mas que nada para musicos, pero tambien tiene aplicaciones para editar video y ese tipo de cosas.
Yo migre de 3d max a blender hace un tiempo asi que al instalar el ubuntu studio mucho no me costo. por otro lado, las herramientas de edicion de video como pitivi o kino (que vienen instaladas) las estoy descubriendo de a poco.

Espero que te haya servido y estoy a tu disposicion para lo que necesites.


Un abrazo.

---

### Post by guillermolisi on 2007-05-18
Si, perfecto. Aclaraste mis dudas mas alla de lo que esperaba.

Muchisimas gracias y en cuanto lo comience a usar te cuento como me va.

Otro para vos.

---

