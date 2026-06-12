---
title: "Ayuda Con las x semimuertas"
date: 2007-04-07
forum: Argentina Team
---

### Post by Sgt. Pepper on 2007-04-07
Tengo las x semivivas
Esto es lo que pasa
1-entro al login(màs precisamente uso el login de enlightenment)
2-inserto el pass y el user todo bien
3-cuando intento entrar al escritorio el monitor brilla se apaga brilla se apaga y vuelvo al login!
4-hago ctrl+alt+f1
5-configuro xorg
6-apago prendo pasa lo mismo
7-hago ctrl+alt+f1 y configuro mal xorg para que las x no se inicien
8-apago prendo configuro bien xorg
9-entro a gnome pero antes de entrar me da un error que no puede lockear xauthorisation file o algo asì pero entro y asì estoy posteando esto
10-salgo apago prendo vuelve a empezar todo de vuelta
ah y no puedo entrar a ningun otro escritorio que el de gnome,cuando intento cambiar el sistema de login me da este error

Failed to run gdmsetup as user root.

Unable to copy the user's Xauthorization file.

Help!ademàs si hago sudo startx al intentar entrar a gnome esta todo el fondo lluvioso y el cursor es una x
Al intentar actualisar me da este error

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '52428803' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpYsp4Lt' as user root.

Unable to copy the user's Xauthorization file.

Ayudaaa ni da hacer todo ese proceso para entrar a gnome x.x

---

### Post by gepatino on 2007-04-07
Me maree un poco con los pasos que indicas... no entiendo bien el porque de configurar mal el x para reiniciar (supongo que la maquina)... pero por el mensaje de error que te da parecería que hay algun problema con el archivo .Xauthorization

Este archivo debería estar en tu home (y comienza con un punto). Si tiene como propietario a tu usuario, asignaselo y asegurate que tenga permisos 600.

Si está como te digo y sigue fallando proba de eliminarlo (o renombrarlo) a ver si al iniciar una nueva sesion de gnome te lo crea bien de entrada.

Una vez que tengas funcionando bien el gnome, recién ahí trata de entrar al enlightenment, pero leete bien la documentación, posiblemente este modificando algunos archivos de configuracion del usuario que esten compartidos por gnome y de ahí el problema. Lamentablemente no uso enlightenment desde red hat 5.1, asi que mucho no te puedo ayudar con eso.

Saludos,

---

### Post by valucha on 2007-04-09
[COLOR="DarkOrchid"]Te pasaba lo mismo que a mi [acá]("http://ubuntuforums.org/showthread.php?t=389537") probaste entrando desde otra sesión?... Porque a mi me dijeron que era un problema de permisos...
Bueno fijate ahi, sino no tengo idea.[/COLOR]

---

### Post by jpmorelli on 2007-04-11
Es un problema de permisos, seguramente borraste el usuario que creaste con la instalación o intentaste copiar un usuario a otro. Yo lo solucioné borrando todos los archivos que están ocultos... o sea :    sudo rm -Rf .*

De más está decirte que se te borran todas las configuraciones hechas hasta el momento, pero bueno, a mi me sirvió para aprender más sobre el tema. Si te copás y le ponés paciencia buscá exactamente cual es el archivo que genera el error, que seguramente es .Xauthority y como dicen mas arriba, con borrarlo o renombrarlo se crea uno nuevo.

---

