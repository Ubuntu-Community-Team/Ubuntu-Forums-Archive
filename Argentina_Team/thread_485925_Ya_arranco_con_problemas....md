---
title: "Ya arranco con problemas..."
date: 2007-06-27
forum: Argentina Team
---

### Post by Emiliano_Lando on 2007-06-27
Buenas a todos!
Mi nombre es Emiliano y soy lo mas nuevo que se puede ver en el mundo de Linux. Por recomendación de un amigo que esta en este foro instalé UBUNTU 7.04
Mi primer problema es que reconocio mi placa de video (fx 5200 de nvidia), pero cuando quiero activar la aceleracion no me da pelota. 
Cuando voy a la seccion de modulos restringidos (o desatendidos será) y quiero habilitar la placa no me da bola.
¿Que tengo que hacer?
Gracias y disculpen si les parece muy salame mi pregunta

Lando

---

### Post by clasificado on 2007-06-27
Salame es el que NO pregunta.

¡Bienvenido a Uluga! Mi pecé está funcionando con un KUBUNTU 7.04, que usa un frente gráfico distinto (KDE) y vi bastaaaante poco al compañero Ubuntu por lo que, para no responder pavadas, te voy a dejar picando la respuesta para ver si aparece algun Amigo que conozca un poco más tu situación.

Ahora, si no aparece, te reviento con comandos de consola para ver si podemos arreglar tu problema :D

Clasificado

---

### Post by gepatino on 2007-06-27
Que haces Emi, estuve buscando un poco de info y encontre esto, a ver si te ayuda:

[http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04)

Si eso no ayuda, edita el archivo /etc/X11/xorg.conf con el comando:

sudo gedit /etc/X11/xorg.conf

y fijate de tener alguna seccion parecida a esta:

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
        BusID   "PCI:02:09:0"
EndSection

Puede ser que en vez de nvidia tengas nv (o envy, no me acuerdo). Ese es el driver a cargar, me parece que nvidia es el que mejor anda, pero toco de oido porque ni siquiera tengo aceleracion en mi vieja maquina :(

Despues de eso, reinicia las X (ctrl+alt+backspace desde el login grafico) y a ver que pasa.


Saludos,

---

### Post by Al_maverick on 2007-06-27
En principio, una cosa muy importante es que pongas todos los errores que te da.
A diferencia del de las ventanitas, en Linux los errores tienen su significado y de acuerdo a eso te podemos ayudar y orientar mejor.

Una de las cosas que seria util que pusieras es el contenido de dos archivos, el /etc/X11/xorg.conf y el /var/log/Xorg.0.log

El primero es la configuracion del X, el manejador del entorno grafico y donde se configura la placa de red. El segundo es el log del mismo X

No conozco esa placa especificamente, pero por lo que vi las NVidia son mucho mas facil de configurar, asi que supongo que muchos habran pasado por lo mismo. Y si, el tema de las aceleradoras graficas es uno de los puntos debiles, pero no te preocupes que seguro te la hacemos funcionar.

---

### Post by Emiliano_Lando on 2007-06-28
Buenisimo muchachos!!! pero gracias a Speedy recién ahora veo las respuestas, asi que probaré lo que dice mi amigo patiño y sino bajaré en mi pen drive los archivos solicitados por el amigo Al-Maverick y los postiaré aca. Los drivers vienen por default o tengo que entrar a bajarlos por internet? porque de ser asi voy a tener que bajarlos en el laburo e instalarlos a mano, me c@€~en Speedy...

---

### Post by quaid on 2007-06-28
instalaste los drivers de nvidia tb?

---

### Post by faktorqm on 2007-06-28
Hola, permitanme corregir ciertos errores y orientar aca al muchacho en cuestion. 

> Puede ser que en vez de nvidia tengas nv (o envy, no me acuerdo). Ese es el driver a cargar, me parece que nvidia es el que mejor anda, pero toco de oido porque ni siquiera tengo aceleracion en mi vieja maquina

Envy es un script de instalacion del driver de Nvidia/ATI, que por cierto es muy bueno. Pasa por alto muchos de los errores que cualquiera de nosotros podriamos tener si quisieramos hacerlo a mano (yo intente, y entre pito y flauta lo termine solucionando mitad con el envy y mitad a mano). no debe ir en la seccion driver del xorg.conf, debe decir o bien "nv" o bien "nvidia".

La página del chabon que hizo esto es (y su correspondiente download es):

[http://www.albertomilone.com/](http://www.albertomilone.com/)

> El primero es la configuracion del X, el manejador del entorno grafico y donde se configura la placa de red. El segundo es el log del mismo X

Pequeño bug!! donde dice red debe decir video.

Pasos a seguir que hice yo con mi placa:

Si estas en un terminal hace esto: (sino anda al paso 4)

1) logueate con tu usuario.

2) ```
sudo nano /etc/X11/xorg.conf
``` (si te pide contraseña metela)

3) movete con las flechas del teclado hasta donde dice section "device" (algo parecido a):

> Section "Device"
Identifier "Device0"
Driver "nvidia"
Screen 0
Option "NoLogo" "true"
Option "RenderAccel" "true"
BusID "PCI:02:09:0"
EndSection


y donde dice  DRIVER PONÉ "NV". Tomando el ejemplo de arriba te deberia quedar:

> Section "Device"
Identifier "Device0"
Driver "nv"
Screen 0
Option "NoLogo" "true"
Option "RenderAccel" "true"
BusID "PCI:02:09:0"
EndSection



Apreta CTRL + O, luego enter para guardar, luego CTRL + X para salir
y luego en el terminal escribi:

```
sudo reboot
```

4) logueate en tu escritorio sin aceleracion grafica, baja el envy e instalalo de esta direccion:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

5) Anda a aplicaciones -> herramientas del sistema -> envy

el programa es super facil de usar, asi que no vas a tener problemas, espera a que termine, y una vez que supuestamente ya esta, reinicia tu compu y si anda, felicitaciones! sino, escribinos copiando el xorg.conf y el xorg.0.log como te dijeron antes y lo arreglamos. Salu2 y suerte!!

---

### Post by Emiliano_Lando on 2007-06-28
Mirá, no cazo u folbo en esto del linux, vengo de xp y mi amigo patiño me carcomiop la cabeza para ke al menos lo pruebe. supuestamente esta reconocida la placa, de ahi a que sepa si estan los drivers correctos es como decirme que para jugar al pacman tengo que pensarlo en "inverse kinematics". Espero que no moleste mi falta de conocimientos.
Saludos!!

---

### Post by faktorqm on 2007-06-28
todo bien, pero simplemente es seguir la guia que te puse arriba para que todos sepamos que ya tenes el driver instalado y configurado correctamente, luego de eso se viene la etapa xgl, luego beryl :) esto es no mas el principio. si lo haces y no te anda nada, postea y ya.

---

### Post by Emiliano_Lando on 2007-06-28
No habia visto tu respuesta faktorqm , esto del envi me lo instala desde internet o me pregunta donde lo tengo? porque tengo dramas con internet y parece que sin conexion voy muerto. recien baje el envy y el supuesto paquete de drivers correspondiente, ahora deberia saber como instalar a mano. Me voy a volver chango pero lo voy a lograr... THIS IS LINUXXXXXXXXXXX!!!!!!!

---

### Post by faktorqm on 2007-06-28
Hola, mira yo a mano no pude, obviamente por ignorante me paso, :P pero bueno, la cosa es asi, o al menos lo que pude averiguar yo. Para que funcione el driver, vos cuando lo instalas, instalas el driver para el xorg. y tambien un modulo para el kernel. no se bien como es la movida con placas viejas, que cambian la version del modulo y como son incompatibles, te saca la roja. (yo tengo una GForce 4 MX) Con las placas nuevas se ***** de risa, instalan el ultimo driver y anda perfecto, y usan beryl y se siguen riendo, pero con las viejas como la mia, hay mala onda. entonces no supe nunca como compilar solo el modulo del kernel para el video, entonces ahi no me kedo mas opcion que darle al envy, y el ****** lo compila! GGRRR!! ya voy a aprender yo tb como se hace eso. xD con las placas nuevas, le das al instalador de nvidia con las fuentes, y listo.

Con respecto a la conexion a internet, el envy si mal no recuerdo te baja el driver de nvidia automaticamente. si no lo queres bajar y/o no podes escribime a ver si te puedo dar una solucion para hacerle creer al envy que ya lo tenes bajado. (lease, ponerlo en algun directorio del envy para ke no lo baje y use ese). Salu2!

---

### Post by gepatino on 2007-06-28
Gracias faktorqm por las correcciones... si bien hace rato que ando linuxeando, hace poco que le estoy tomando la mano a todo lo que sea configuación gráfica, soy mas bien un consolero o administrador de servers.

Menos mal que hay gente que presta atención...

Saludos,

---

### Post by Emiliano_Lando on 2007-06-28
ya estoy en casa y aprovecho ke estan todos mirando el partido. TENGO INTERNET!!!
en cuanto termine de bajar las actualizaciones veo ke hago con la placa. despues les digo
Salud y aguante Argentina y Banfield!!!

---

### Post by Emiliano_Lando on 2007-06-29
Bueno, aprovechando que tuve internet les cuento que no tuve mayores problemas. Se descargaron todas las actualizaciones necesarias y hasta los drivers de nvidia, asi que salio andando solo. lo único que tuve que agregar en el xorg.conf fie la linea "Option "RenderAccel" "true"" y salio como por un tubo.
Ahora bien, instale el Beryl pero nunca lo pude hacer andar, los efectos de Compiz anduvieron, pero nunca supe como hacer andar el Beryl.

---

### Post by faktorqm on 2007-06-29
> **gepatino said:**
> Gracias faktorqm por las correcciones... si bien hace rato que ando linuxeando, hace poco que le estoy tomando la mano a todo lo que sea configuación gráfica, soy mas bien un consolero o administrador de servers.

Menos mal que hay gente que presta atención...

Saludos,

Todo bien! si sos server admin debes ser grosso vos! salu2!

El beryl yo no me acuerdo como, pero fijate en mi post "dudas sobre xgl, beryl y chipset" que los chicos pusieron varios "como's" que ahi te dice como mandarlo al inicio. salu2!!

---

### Post by spg76 on 2007-06-29
Para iniciar Beryl, si esta bien instalado, hace ALT+F2 y pone "beryl-manager" y listo.
Para que inicie con las sesion anda a "Sistema>Preferencias>Sesiones" y agrega "beryl-manager" a "Programas al inicio".
Espero que te sirva.
Saludos.

---

