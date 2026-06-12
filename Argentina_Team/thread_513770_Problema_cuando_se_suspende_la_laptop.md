---
title: "Problema cuando se suspende la laptop"
date: 2007-07-30
forum: Argentina Team
---

### Post by seba2611 on 2007-07-30
cuando dejo de usar la notebook un rato y se suspende que queda la luz de encendido en amarillo, deberia arrancar al mover el mouse o apretar de nuevo ese mismo boton pero lo que hace es volverse a poner en verde como si estuviese activa pero la pantalla no se enciende, eso pasa cuando la dejo un rato q se pone sola en ahorro de energia , ahora quise hacerlo desde el menu y me pasa lo mismo con el vista q viene de fabrica no lo hace y arranca normalmente asi q con el ubuntu tambien deberia poderse hacer alguna idea o alguien que tenga el mismo problema...

---

### Post by tony_feisty on 2007-07-30
Fijate en ubuntu en la parte de configuración de ahorrro de energia, debe venir de ahi el problema yo habia tenido un problema similar y lo solucione de esa forma.

Saludos.

---

### Post by seba2611 on 2007-07-31
Desde gestion de energia no puedo hacer nada como para solucionarlo , lo unico que puedo hacer ahi es poner el tiempo q quiero q tarde en suspenderse o si quiero q hiberne en vez...el tema es que se suspende pero cuando quiero arrancarla la pantalla no vuelve a encenderse y por lo q veo tampoco hay actividad en el disco...

---

### Post by sdm_cacto on 2007-07-31
cuando estas en Grub, trata de acregar los comandos "-noacpi" y "noapic", esto desabilita la gestion de energia

---

