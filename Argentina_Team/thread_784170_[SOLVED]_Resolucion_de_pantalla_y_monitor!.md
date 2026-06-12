---
title: "[SOLVED] Resolucion de pantalla y monitor!"
date: 2008-05-06
forum: Argentina Team
---

### Post by vk-cdg on 2008-05-06
Anoche noté un pequeño problema que no descubro como solucionarlo con la resolucion de la pantalla o el tamaño del monitor. 

Paso a contar.
Cuando arranco Ubuntu, en la pantalla donde pongo el usuario y luego la password, no veo la "barra" de abajo donde está el botón de opciones como para apagar o reiniciar sin haberme logueado. También noté que el logo de Ubuntu está como desplazado hacia la derecha. 
Eso me hace pensar que me falta una franja inferior y lateral derecha de la pantalla inicial.

Probé varias cosas, resolucion de pantalla desde el menú Preferencias/Resolucion de pantalla, está en 1280x960. Probé con el nvidia-settings y también está en 1280x960 y además probé la interfaz desde donde especifico que monitor tengo (en Gutsy tenía lanzador) que ahora en hardy de accede por consola ya que no tiene lanzador 

```
sudo displayconfig-gtk
```

La cosa es que en todos lados está especificado como que la resolución es 1280x960, pero sigo viendo la pantalla recortada. 
Recién cuando en esta última interfaz digo que me clone la pantalla principal en el otro monitor es cuando la pantalla de bienvenida se "acomoda" pero el problema es que configurado así, no puedo cambiar la resolución de pantalla porque me dice que no es compatible con el modo dual monitor....

Alguna sugerencia o idea?

---

### Post by faktorqm on 2008-05-07
Me sumo al reclamo aca del sr. vk-cdg. En la compu del trabajo no me pasa, me pasa en casa, cuando le puse 1600x1200 @ 75hz le encantó y todo bien, pero cuando reinicie.... :O:O sorpresa! yo veo el cartel donde pones user y pass casi abajo a la derecha, cuando en teoria deberia verlo al medio, y con los botones para apagar y esas cosas ni las veo. 
Me ha ocurrido en largas noches de configuraciones de xorg.conf que hay veces que se ve asi, y cuando pones el mouse sobre los bordes vas como "navegando" entre el cartel de login. Este no fue el caso, simplemente esta "clavado".
Igual, como me puedo loguear, esta todo ok, casi nunca uso los botones que aparecen en el login, y si quiero apagar, apreto el botón y empieza a apagarse solita como si yo apretara apagar, asi que es lo mismo.
Seré curioso, no se me habia ocurrido hacerlo antes, no funcionará el truquito de apretar "CTRL + ALT + +" y "CTRL + ALT + -" para ajustar la configuracion on-the-fly? (al vuelo, a tiempo real)
Cuando llego a casa lo pruebo.
Para mi hay que toquetear el gdm.conf o alguna de esas bellezas. (¿?) Salu2!

---

### Post by vk-cdg on 2008-05-07
Bueno, uno mas al que le pasa. Pensé que estaba loco! jajajaja

> **faktorqm said:**
> Seré curioso, no se me habia ocurrido hacerlo antes, no funcionará el truquito de apretar "CTRL + ALT + +" y "CTRL + ALT + -" para ajustar la configuracion on-the-fly? (al vuelo, a tiempo real)
Cuando llego a casa lo pruebo.

Tampoco se me había ocurrido.
Contame si te andubo, anoche en casa no entré al foro así que no vi este post tuyo.

Yo veo la pantalla completa cuando configuro para que me clone el segudo monitor, pero es un espanto, ver en los dos lo mismo. Cuando pongo que los haga independientes no la veo completa.

---

### Post by Mauro22 on 2008-05-07
Encontre tres cosas, asi que si pueden pruebenlas:

1) Editar Xorg.conf y poner en la parte de screen:

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Monitor        "SAMTRON 55V"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1024x768" 
        **Virtual      1024 768**
    EndSubSection
EndSection

```

la palabra Virtual y la resolucion que deseen sin la x ni ""


2)

Editar uslash.conf

```

# Usplash configuration file
xres=1024
yres=768

```

O la que quieran

3)
```

 sudo dpkg-reconfigure gdm

```




:lolflag:

---

### Post by rodrii on 2008-05-07
tengo otra pregunta referida a los monitores

tengo una placa nvidia 6200 con salida dvi y vga 

tengo conectados 2 monitores buscando en internet vi como

se podia hacer para poner los 2 monitores el problema es que

como los monitores son distintos edite el Xorg.conf y hasta la 

la pantalla de ubuntu que carga esa del fondo negro ahi se ve en 

los 2 bien pero cuando entra solo se ve el dvi y el otro se ve como 

fuera de rango osea no muestra nada solo colores

---

### Post by faktorqm on 2008-05-07
Loco tenes bien merecida la medalla.
No me habia fijado, pero el nvidia-settings me descontrolo el xorg.conf y tenia seteado el virtual en 2035 por 1536. Asi que le puse 1600 por 1200 asi como me dijiste vos (y como estaba) y arranco de pm. primero probe el del usplash, pero ese no es, encima decia en el archivo que habia que hacer update-initramfs y lo hice :S pero no cambio nada, asi que esa no es solucion. 
Gracias loco de vuelta!

EDITO: la solucion 3 me dio miedito y no la quise ni tocar. ya rompi el ubuntu del laburo y no queria romper el de casa que anda re bien. la solucion del xorg ANDA. salu2!!

---

### Post by Mauro22 on 2008-05-07
De nada, amigo!


Esperemos que al amigo vk-cdg, tambien le funcione!


:popcorn:

---

### Post by vk-cdg on 2008-05-08
Confirmadísimo. Andó bien! (como dice mi sibrinita)

Mil gracias!

---

