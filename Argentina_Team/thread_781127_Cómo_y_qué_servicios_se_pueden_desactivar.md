---
title: "Cómo y qué servicios se pueden desactivar?"
date: 2008-05-04
forum: Argentina Team
---

### Post by smrdelj on 2008-05-04
Hola que tal.

Quisiera optimizar el rendimiento de mi Ubuntu 8.04 Hardy aligerandole todo lo q pueda.
Seguramente haya algun servicio para desactivar, o cualquier cosa que no haga falta que se cargue al iniciar Ubuntu.

Qué me recomiendan? Cómo lo hago?

Gracias, saludos

---

### Post by gsiliceo on 2008-05-04
Hola, puedes quitar servicios en dos lugares: 
sistema / preferencias / sessiones
y
systema / administracion / servicios
Yo quite todo lo que logea(registra) eventos, lo que permite programar eventos, los servicios de bluetooth, los de tracker(no me gusta), escritorio remoto y los de manejo de energia(si usas laptop deja estos) no me acuerdo de los nombres exactamente, pero traen una explicación pequeña que para mi fue suficiente para saber si los debería dejar.

---

### Post by Hei Ku on 2008-05-04
ojo con los de manejo de energia, que despues la pc no se apaga bien. No se usan solo para laptops, aunque dan esa impresion.

---

### Post by MeduZa on 2008-05-04
hola, yo para optimizar mi sistema agarre e hice una lista del hardware que tengo y de los modulos que necesito para que este hard ande, entonces me baje en kernel de linux mas nuevo que habia y quite todo lo que nunca en mi vida voy a tener, despues de eso desactive todo lo que no era compatible para mi hard ej: todo lo de intel ya que tengo AMD. hice que muchas cosas se compilen directamente en el kernel como los alsa, solo eleji alsa, alsa-oss y el driver de la audigy2.
con el tiempo fui quitando mas cosas que encotraba inutiles y leyendo aca y alla logre un boteo super rapido, por ultimo, me base en un par de guias para quitar cosas que no uso, aca te dejo dos links que me sirvieron mucho
(si no sos siquigo quita si o si el sistema para gente ciega)

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

y

[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

estan en ingles asi que ojo xD, por otro lado no todo lo que dice ahi tenes que quitarlo, es en base a tus necesidades y tu sistema. yo como crom y anacrom no lo quite pero si quite el avahi y otros mas, haciendo que mi boteo sea de solo unos segundos

ojo tambien con el recorte no te pase como a mi que no se que quite y ahora no tengo usplash jajajaja

suerte

---

### Post by gsiliceo on 2008-05-04
Meduza y en cuanto tiempo inicia tu compu yo quitando servicios y usand bootchart para ver que me detiene ando en 32 segundos de un inicio en frio.
Espero que optimizando el kernel como tu consiga unos 5 6 segundos menos :P

---

### Post by MeduZa on 2008-05-04
> **gsiliceo said:**
> Meduza y en cuanto tiempo inicia tu compu yo quitando servicios y usand bootchart para ver que me detiene ando en 32 segundos de un inicio en frio.
Espero que optimizando el kernel como tu consiga unos 5 6 segundos menos :P

la mia con todo lo minimo llego a 16 segundos pero despues le empece a meter mano para el otro lado (activar cosas) y me quedo en 26 a 30 -.- fluctua
ahora estoy compilando el kernel para que me ande el usplash (ya lo hice nadar pero anda raro y no me gusta)

asi que sigo probando, cuando todo ande de nuevo procedo a romper cosas de nuevo ajjajaja para bajar otra vez la velocidad de arracaque y quitar cosas innecesarias.

---

