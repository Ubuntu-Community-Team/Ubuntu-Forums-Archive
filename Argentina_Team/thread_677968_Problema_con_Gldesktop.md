---
title: "Problema con Gldesktop"
date: 2008-01-25
forum: Argentina Team
---

### Post by h9005 on 2008-01-25
Entro a sistema/preferencias/gldesktop pero no inicia nada. De vez en cuando al entrar en vez de iniciarme con el modo de ubuntu studio marca un error con gnome y carga otra visualización.

---

### Post by euzkoarima on 2008-01-25
Ojo! a mi me pasó lo mismo, entonces lo corrí desde una terminal, ahí si apareció un cartel que me preguntaba si quería mantener esta configuración o volver a la anterior????
Creí que el GLDesktop había tocado algo y consideré más seguro decirle que volviera a la anterior: ERROR!! tenía 4 escritorios y volvió a los 2 de la instalación original, lo que no importa, pero lo grave es que me desestabilizó todo el entorno, los paneles comenzaron a desaparecer aleatoriamente, los cambios de un escritorio a otro funcionaban mal (a veces cambiaba a veces no), ventanas que las minimizaba y nunca más las podía volver a hacer visibles, etc, etc.
Para colmo la es la PC de mi puesto de trabajo, que el viernes pasado reemplazo a una vieja mac, al final del día le instale el ubuntu y el lunes rompí todo :-(
Para salir del paso (y que nadie en la oficina me venga a decir que tengo problemas por usar linux) lo que hice fue en preferencias -> apariencia: solapa efectos visuales, poner "ninguno". Listo, todo estable, todo funciona.

De paso aprovecho a preguntar: supongo que para poder volver a poner los efectos personalizados y que vuelva a funcionar va a requerir hacer sudo dpkg-reconfigure algunos-paquetes, pero cuales????
Si alguno tiene otra idea también soy todo oídos.

Saludos

---

### Post by niko_3100 on 2008-01-26
Supongo que los de compiz, y emerald. Tendrian que fijarse si el xorg esta bien, o parece estar bien.

---

### Post by euzkoarima on 2008-01-28
en /etc/x11/xorg.conf (digo, si te referis a eso) no encuentro nada raro, ni nada que hable compiz o fusion, solo lo normal, monitor, teclado, placa. Además supongo que debe estar bien porque con los efectos desactivados todo anda de 10.

Por otro lado, los paquetes que parecen candidatos a reconfigurar (despues de mirar en synaptic que tengo instalado que se refiera a compiz son:

gnome-compiz-manager, que depende de
compiz, que depende de
compiz-gnome

Alguna sugerencia de orden, es decir, conviene en el orden de dependencias o me tiro directo a reconfigurar compiz-gnome??

Saludos

---

### Post by h9005 on 2008-01-29
Ni idea reperdido tengo funcionando el compiz fusion de 10, me anda el cubo de escritorio, los efectos y todo. Solo tengo problemas con las funciones pantalla completa, hay un parpadeo bastante molesto por ejemplo cuando abro open office, o cuando pongo el visor de fotos a pantalla completa. Creo q es compiz el que provoca esto.

---

