---
title: "Ubunto lo mejor: Ayuda."
date: 2007-12-11
forum: Argentina Team
---

### Post by soadfanatic on 2007-12-11
hola a todos me presento soy elias de argentina. Hoy instale  ubuntu por primera vez, despues de renegar años con ventanas. Me parecio exlente, es mejor el ambiente que se siente ahora cuando estoy frente a la pc. Con las ventanas estaba acostumbraso un muy buen sonido. Algo con lo que linux nose quedo atras. Pero de todas formas no pude hacer funcionar el sonido 5.1, nisiquiera el subwofer. Solo los 2 parlantes frontales. Revise por internet hasta el cansancio. pero no encontre solucion a mi problema. Tengo una placa madre Chipset modelo M909G V5. Quisiera saber si me pueden ayudar con mi problema. Ya que trabajo con sonido. Y linux me parecio la mejor alternativa para SO. Muchas gracias por su atencion. soadfanatic

---

### Post by alfredo_cba on 2007-12-11
jaja estamos en la misma, con feisty fawn me andaba barbaro el sonido 5.1, desde que instalé gusty me pasa lo que a vos, solo tengo sonido en los parlantes delanteros. Probe habilitando todos los otros desde la administracion de sonido, pero si suerte. Igual no desespero, siempre tarde o temprano alguién aparece con la solucion a tus problemas. 
Adiero a tu pedido-

---

### Post by Hei Ku on 2007-12-11
En KDE tenes la opcion de duplicar frontales, con eso aprovechas el sonido por todos los parlantes. Cuando escucho un DVD o algo similar, le quito la opcion para escuchar con surround. Supongo que gnome tiene algo similar en el equivalente al kmixer.

---

### Post by facundocorradini on 2007-12-11
Pues siguiendo con la idea de Hei Ku, 

En Gnome (el entorno gráfico default de ubuntu) tenés que ir al control de volumen (doble click en el icono del parlantito), allí vas a editar--> preferencias y pruebas un par de opciones de ahí...


vi por ejemplo que tenés "chanel mode", que al activarlo te da una pestaña "opciones" desde donde puedes cambiar el modo de canales. 

Tambien puede interesarte las opciones "duplicate front" (lo que te decía hei ku),  "Sorrund" y "Sorround Jack Mode"

( todo eso va desde la teoría, ya qu yo apenas tengo los parlantitos horribles de la notebook... :(    )

Bueno Elías, espero que con eso puedas resolver el problema, y BIENVENIDO A UBUNTU!

---

### Post by soadfanatic on 2007-12-12
ya probe eso y varias otras cosas como instalar alsamixer y editar un archivo todo eso lo hize. creo que lo unico que me queda es esperar a que alguien tenga la solucion. muchas gracias por su ayuda.

---

### Post by Hei Ku on 2007-12-12
Mira que el sonido no te va a salir por los 5 parlantes excepto que sea realmente 5.1. O sea, con dvds y cosas deberia andar bien, pero con un mp3 ni noticia, excepto que actives esta emulacion. Otra cosa, es que a veces el sonido de los parlantes traseros esta puesto en mute, y solo tenes que subirle el volumen. Eso es mas facil de ver desde el alsa-mixer, en la terminal.

Que es lo que te sucede a vos? Activas "duplicar frente" y asi y todo no te sale el sonido por los otros parlantes? No termino de entender el problema especifico que tenes.

---

### Post by soadfanatic on 2007-12-13
estemm. mira yo en win podia usar los parlates delanteros, traseros y el subwoofer. osea 5 parlantes. Ya que el subwoofer era un solo parlante. pero en la configuracion de audio tenia una opcion para cambiar los canales del central y el subwoofer, ya que este va por el canal secundario. Entonces sonaba perfecto. En linux no puedo hacerlo probe configurar hasta donde sabia. Pero sigue sin sonar. 
                                                                   soadfanatic
pd:Se puedo quitar el inicio de sesion en red. O sea iniciar directamente a gnone?.

---

### Post by alfredo_cba on 2007-12-13
en gusty, yo tengo activado duplicate front, es más, si no lo activás no sale ningun sonido. Entiendo que solo funcionen en 5.1 solo si la fuente es de 6 canales... pero debería emular los otros. yo prefiero por lejos el rhythmbox al WMP, pero uno reproduce música en los 6 parlantes , con graves y un buen sonido y en gusty suena a lata y solo los frontales. En cambio en Feisty me andaba barbaro.

---

### Post by margori on 2007-12-13
En windows, cuando a DirectSound de DirectX 9 se lo alimenta con canales estereo y se tiene salida 5.1, automaticamente lo descompone en 5.1 canales para aprevechar todos los parlantes, aunque en realidad no duplica realmente la señal de los delanteros a los traseros, solo reproduce entre un 10% y 30% de los primeros.

Muchas cosas en el mundo de windows se hacen automaticamente y quedan justos para el usuario comun. Pero en Linux podes ir un poco mas alla, pero sin contar con tanta automatizacion. Yo no tuve mucho exito con el sonido surround pero se que la punta del hilo esta en el archivo ~/.asoundrc que configura ALSA.

---

### Post by Hei Ku on 2007-12-13
desde la terminal:
alsa-mixer

ahi estan casi todas las configuraciones de sonido.

---

### Post by MeduZa on 2007-12-13
> **soadfanatic said:**
> hola a todos me presento soy elias de argentina. Hoy instale  ubuntu por primera vez, despues de renegar años con ventanas. Me parecio exlente, es mejor el ambiente que se siente ahora cuando estoy frente a la pc. Con las ventanas estaba acostumbraso un muy buen sonido. Algo con lo que linux nose quedo atras. Pero de todas formas no pude hacer funcionar el sonido 5.1, nisiquiera el subwofer. Solo los 2 parlantes frontales. Revise por internet hasta el cansancio. pero no encontre solucion a mi problema. Tengo una placa madre Chipset modelo M909G V5. Quisiera saber si me pueden ayudar con mi problema. Ya que trabajo con sonido. Y linux me parecio la mejor alternativa para SO. Muchas gracias por su atencion. soadfanatic


ya se a que te refeis
dependiendo de la aplicacion que uses para escuchar musica tenes que activar la salida en 5.1, eso nada tiene que ver con el alsa, supongamos que vas a el movie player, tenes que decirle (no me acordo donde y ahora no estoy en mi pc) que use la conf 4.1 o 5.1, eso genera la duplicacion de canales y el uso de subwofer.
Yo uso el audacious con el plugin extend stereo y me sale por todos lados en la audigy 2

suerte, cuando este en mi pc te digo si tengo algo mas o como hacerlo

---

### Post by Hei Ku on 2007-12-13
el alsamixer tiene la opcion channel, donde le decis cuantos parlantes tenes. Yo lo tengo en 6.

---

