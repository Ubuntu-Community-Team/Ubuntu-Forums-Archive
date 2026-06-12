---
title: "Falla en la instalacion en Olibook 610"
date: 2007-07-17
forum: Argentina Team
---

### Post by jorgito on 2007-07-17
Hola a todos!

Intente instalar con el LiveCD del 7.04 en una Olibook 610 (con 256 Megas de RAM), pero no llegue a ningun lado. Estuvo alrededor de 4 horas dale que te dale al disco y lo unico que consegui es una pantalla marron clarito.
Supongo que puede ser por la poca memoria, asi que estoy pensando instalar desde el alternate CD que parece requerir menos recursos.
Alguien tiene algun consejo o link a informacion acerca de con que me voy a encontrar al instalar en modo texto? Particularmente me inquieta el tema de elegir el teclado.... si le erro, despues lo puedo arreglar?

Bueno, gracias por adelantado y saludos a todos los que leen!

---

### Post by faktorqm on 2007-07-17
Hola, mira, yo no pude en ninguna pc con 256 mb instalar el live cd, siempre necesite el alternate. De todas maneras, siempre uso ese por que me pone nervioso bootear "lento" para darle a un icono feo que dice "instalar".
En el alternate cd, te vas a encontrar con una instalacion de lo que se llama en modo texto digamos, difiere en algunas cosas pero para mi ke soy re cuadrado me da igual, mientras ande rapido, no me importa si se ve lindo o feo, o si en lugar de un boton 3d hermoso tengo que apretar ctrl + E. no se si me expliko.

Si le erras al teclado, lo mas malisimo que te puede pasar es que la tecla del acento no funcione, y tengas que usar la de arriba, que es el acento al reves. Despues obvio que se cambia y es una pavada. (sistema -> preferencias -> teclado)

No te asustes y dale tranquilo, que es lo mismo pero sin ventanas! salu2!

---

### Post by jorgito on 2007-07-17
Gracias faktorqm!

Todo parece andar bien! Tendré que probar grabar CD y wifi en cuanto pueda.
Ahi quedo bajando 165 megas de actualizaciones.
Al menos no voy a tener que escuchar a mi esposa diciendome que le estropee la maquina!

De paso aviso que el tema de la resolucion de la pantalla (que quedaba erroneamente en 1024x768) lo arregle haciendo 
sudo apt-get install xserver-xorg-video-intel

Cuando lo arregle en la otra notebook (una Olibook 820) aviso en el post correspondiente.

Gracias de nuevo y seguramente voy a seguir molestando ( y si puedo ayudando ).

Jorgito

---

### Post by faktorqm on 2007-07-17
de nada, pregunta trankilo, estamos para eso. salu2!

---

### Post by Hex_Mandos on 2007-07-19
Grosso, otro Olibookero (yo tengo una 810). Yo para el video use el paquete 915resolution. Otra cosa: fijate el DVD, que a mi me vino seteado en zona 1, y no podía ver algunas películas ni que le instalara todos los libdvdcss del mundo. El paquete para setear la región es dvdregionset, creo.

A mi la máquina me anda perfecta... es interesante que no tenga ninguna calcomanía tipo "Designed for Windows".

---

### Post by jorgito on 2007-07-19
Hola Hex_Mandos!

Si, creo que fue gracias a tu post que me anime a comprar no una sino dos Olibook , una 610 para mi esposa y la 820 para mi. Lo notable es que va a resultar que ella necesita mas máquina que yo, porque le hace correr tantas cosas a la vez que se pone re-pesada (la maquina, no ella).
Ya estoy viendo de ponerle dos gigas a la 610 a ver si compensa un poco.
Gracias por el dato del DVD. La verdad es que todavia ni lo probe, pero seguramente me va a ahorrar un monton de mala sangre.

Un saludo, y gracias de nuevo!

---

### Post by Hex_Mandos on 2007-07-19
Ja, SICSA debería pagarme una comisión! Conozco varias personas que están pensando en comprar una... lo que está bueno, porque el día que los convenza de pasarse a Linux ya van a tener una máquina con un excelente nivel de compatibilidad.

---

### Post by ubuntero_arg on 2007-07-21
Hola muchachos!!! Soy otro feliz usuario de la Olibook 610. Aprovecho el post para preguntarles si alguno pudo solucionar el problema de sacar el sonido por los auriculares unicamente, cuando los enchufamos obviamente. Aparte de esto, todo anduvo perfecto y de una, como tiene que ser. Bueno, un abrazo!!!

---

### Post by ubuntero_arg on 2007-07-21
Ahora que me acorde les comento otra duda. No se porque cuando uso la notebook sin estar conectada a la red se pone muy lenta, y no hablo del arranque, sino en general una vez arrancado el entorno gráfico. ¿Alguien sabe que puede estar pasando?. Saludos!!!

---

### Post by jorgito on 2007-07-23
Hola!

Sabes que yo creia que debia ser solo impresion mia, pero se ve que no!
Me imagino que la pobre debe estar todo el tiempo buscando la red que no esta mas....
Por algun lado lei algo de usar perfiles para la conexion de red, de manera de no tener,  por ejemplo, habilitada la placa wifi si no hay señal en donde estas.
Creo que habria que empezar por ahi, si es que nadie tiene la posta, o al menos una mejor teoria.

Saludos!!!

---

### Post by ubuntero_arg on 2007-07-23
Hola de vuelta! El tema de la red ya lo solucione. Es un problema general en Ubuntu. La solución es editar el archivo /etc/hosts y en la línea:

127.0.0.1 localhost

agregar el nombre de tu pc al final, para que quede asi

127.0.0.1 localhost el_nombre_de_la _pc

Guardar y reiniciar. Con eso se soluciona el problema de la velocidad para abrir programas y demás.
Lo que me queda como duda todavía es el tema de los auriculares. Por ahi leí que hay que compilar los drivers, pero no me causa gracia, aunque ya lo hice para otras cosas. 
Bueno, saludos!!!

---

