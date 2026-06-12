---
title: "Nueva portátil Packard Bell."
date: 2007-09-02
forum: Argentina Team
---

### Post by hernan blau on 2007-09-02
Hola, les cuento que me compré una portátil packard bell en carrefour a 2550.Viene con W Vista. Le puse el disco Live Ubuntu y no funciona el audio de los ejemplos. Si bien detecta las redes wi-fi no puedo instalar ninguna. El dico rígido ya viene particionado con una de 8 Gb aprox. en primer lugar y luego otra con el resto con 17 Gb ya ocupados.. el disco es de 80. Ya les contaré cómo ma va con Ubuntu. Si alguien tiene experiencia con esta pc por favor chifle. Gracias.

---

### Post by hernan blau on 2007-09-02
posdata: el modelo es easynote mz375 ar

---

### Post by niko_3100 on 2007-09-02
Mira vos de paso comento que yo tambien hace poco me compre una notebook compaq v3415 a $2699 y le puse 1 gb mas de ram ahroa tengo 1,5 gb de ram y ubuntu levanto todo joya lo unico que me esta trayendo inconvenientes es el wifi broadcom que no lo puedo hacer andar despues tdo bien, hasta los botones de Fn para la reproduccion de la musica con el rythmbox. Aclaro que instale feisty fawn.

---

### Post by jsartti on 2007-09-04
Para solucionar el tema de los drivers Broadcom, tenés dos opciones:

1. Con ndiswrapper, usando los drivers nativos de windows.
2. Con bcm43xx-fwcutter, una herramienta que determina el tipo de chip de la tarjeta y te baja una versión libre de los drivers.

En ambos casos, instalá los paquetes correspondientes desde Synaptic.

En el caso de ndiswrapper, también hay un par de front-ends gráficos (ndisgtk y no me acuerdo el otro). OJO: en cada actualización del kernel, tenés que reinstalar el driver para que retome la funcionalidad.

En el caso de bcm43xx-fwcutter, lo corrés como root desde una terminal gráfica y baja e instala esos drivers libres desde una página alojada en berlios.de.

Personalmente (Acer Aspire 3002 LCi con Broadcom 4318) después de usar ambos me decidí por la 2º opción, por tres motivos
- No hay que reinstalar los módulos.
- Me funcionan los LEDs de conexión.
- Son libres, que en este caso es doblemente importante, porque Broadcom se ha empeñado en no dar ni un poquito de ayuda para la utilización de sus tarjetas en GNU/Linux.

Saludos
Juan

---

### Post by niko_3100 on 2007-09-04
Sip lo isntale con ndiswrapper al final lo bueno es que si me reconoce el led se pone el azul igual que en ventanas xp jaja!! Pero ahora el nm-applet la primera ves que me reconocio el wifi me pidio que ingrese uan contraseña para arrancar el nm-applet y no la puedo sacar quiero que se conecte sin contraseñas salvo las que esta configurada en el router para la red wifi, se entiende?

---

