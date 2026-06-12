---
title: "Gusty y Compiz: Resolución y Refresco del Video"
date: 2007-11-11
forum: Argentina Team
---

### Post by acabrera22 on 2007-11-11
Hola nuevamente, simplemente otro reporte de problemas con Gutsy Gibbon...
En una instalación limpia de Ubuntu 7.10, instalo los controladores restringidos de mi placa Nvidia GeForce MX 4000 y activo y personalizo correctamente Compiz con plugins a mi gusto. Todo correcto.
Luego de trabajar un rato veo que mi monitor (Samsung 591s, 15") estaba trabajando a una tasa de refresco vertical a 50hz... con lo cual me dispongo a cambiar esto desde "Sistema>Administración>Pantallas y Graficos", y observo que mi monitor fue detectado como "Monitor Plug & Play" y las configuraciones posibles de resolución y refresco:
640x480... ?hz
800x600... ?hz
1024x768... 50hz ó 51hz...
cuando mi monitor debería soportar los 1024x768 a 70 ó 72hz.
Entonces me propongo configurar mi monitor, viendo que no esta listado entre los modelos disponibles, si bien la configuración autodetectada es correcta en cuanto a los rangos soportados...
Leyendo un blog veo que esta la posibilidad de importar el .inf de controlador (que descargo desde la pagina de samsung).
Esto me agrega el modelo correctamente (con los mismos rangos que autodetectaba ubuntu en la config. anterior, que vuelvo a aclarar son correctos... (30-55; 50-120) ).
Ahora las configuraciones posibles son tanto más acertadas... aunque la configuracion del refresco en 1024x768 no me permite más que unos 60 miseros hz...
Cierro Sesion como me advierte la aplicación, y me dispongo a chequear como resulto el cambio.
Las configuraciones no fueron aplicadas como correspondian, automaticamente volvió todo como estaba antes en cuanto a resoluciones y refrescos permitidos, solo que mi monitor ahora se lista como Samsung 591s.
Se agregan también los problemas comunes de la carga del decorador de ventanas emerald, (ventanas sin bordes, gnome-terminal en blanco) teniendo que o volver a la autodetección del monitor, para que se liste como "Monitor Plug & Play" ó bien usar metacity como decorador de ventanas.
A este punto no queda más que probar un dpkg-reconfigure xserver-xorg a ver si puedo trabajar a una tasa de refresco aceptable en mi monitor (mis ojos no dan más...).
Lo cual resulta bastante inutil porque mi ubuntu se empeña aparentemente en modificarme las configuraciones del video.
Con lo cual ahora sigo trabajando en 50hz y con compiz-fusion (lamentablemente) desactivado.
Me resulta bastante tonto pasarles mi xorg.conf luego de la reconfiguración y ciertos pruebas a mano que hice.
Si alguno de ustedes podría informarme acerca de la detección de video de ubuntu y de la manera de ayudar reportando los incovenientes a desarrolladores (para alguien que solamente habla español obvio), creo que haríamos un bien a todos los que tengamos problemas semejantes para la proxima release de ubuntu, que debemos ser muchos calculo....
Así y todo estoy muy contento con esta distro.
Pido disculpas por lo extenso de este posteo.
Gracias por la paciencia y saludos!.

---

### Post by Mauro22 on 2007-11-11
Tenes que agregar los modos que queres en el xorg.conf e ir probando, desctivar los que no andan y asi...

---

### Post by acabrera22 on 2007-11-11
Si si, algo anduve probando como decía... pero sin resultados, en cuanto le encuentre la vuelta posteo. 
De todos modos realmente estaría bueno saber que se esta haciendo  respecto a la detección del video y como se puede ayudar. Por allá en el año 1999 estaban los mismos problemas de detección en otras distros... :(
Gracias de todos modos! :)

---

### Post by niko_3100 on 2007-11-11
En mi notebook tambien me pone ua resolucion de 1280x800 y 50 hz pero la verdad no noto diferencia con 60 o 65 hz... asi que no le di bola.. :P

---

### Post by rojojuan on 2007-11-12
[QUOTE=acabrera22;3752547]Hola nuevamente, simplemente otro reporte de problemas con Gutsy Gibbon...
En una instalación limpia de Ubuntu 7.10, instalo los controladores restringidos de mi placa Nvidia GeForce MX 4000 y activo y personalizo correctamente Compiz con plugins a mi gusto. Todo correcto.
Luego de trabajar un rato veo que mi monitor (Samsung 591s, 15") estaba trabajando a una tasa de refresco vertical a 50hz... con lo cual me dispongo a cambiar esto desde "Sistema>Administración>Pantallas y Graficos", y observo que mi monitor fue detectado como "Monitor Plug & Play" y las configuraciones posibles de resolución y refresco:
640x480... ?hz
800x600... ?hz
1024x768... 50hz ó 51hz...
cuando mi monitor debería soportar los 1024x768 a 70 ó 72hz.



Te cuento lo que me pasa a mi y tal vez puedas encontrar alguna solución o bien aclararme algo a mi.
Instalé los drivers propietarios de nvidia con Envy. Entré a nvidia-settings y configuré la resolución de 800 x 600 a 75. Grabé en las X.
Fui a Sistema - Pnatallas - y elegí mi monitor. Acepté.
(Te reconoce bien aquí el monitor?)
Al arrancar nuevamente me reconoce bien la nueva configuración. A veces al arrancar aparece la configuración de 50; rearranco las X (Ctl + Alt + Retroc) y vuelve a colocarme la resolución a 74 (en lugar de 75, pero anda bien).
Algunas veces cuando ingreso a alguna página de Internet se cuelga (vaya a saber porqué), rearranco y la configuración vuelve a 50.
En síntesis, si no se cuelga, anda a 74 según Preferencias -Resolución de Pantallas -, pese a que esa velicudad de refresco con existe en el xorg.conf.
Siempre tengo activado el Compiz sin problemas.
Parece que todavía existe alguna incompatibilidad con los drivers de nvidia?

---

### Post by User21 on 2007-11-12
Tuve un problema similar al empezar a usar Gutsy: una vez instalados los drivers de Nvidia, instale el paquete nvidia-settings. Lo ejecute con sudo y lo setie manualmente al modo que mi monitor indicaba como soportado. Guarde los cambios en xorg.conf desde el mismo asistente de Nvidia, y SAN SE ACABO! Intentalo!

---

### Post by elaleph on 2007-11-12
Les comento cómo resolví en mi caso, no solo el problema de la detección del monitor (Samsung SyncMaster 793v) y la taza de refresco, sino también el del reconocimiento de mi tarjeta gráfica, una Nvidia GeForce 7200GS. 
Simplemente reinstalé Gutsy pero, antes de particionar y proceder a la carga de archivos, configuré en Sistema>Administración>Pantallas y gráficos esos dos parámetros, el modelo de la tarjeta y el monitor. Y así fue que funcionaron luego ambos a la perfección. Antes, cuando instalaba el sistema y luego intentaba configurar, las cosas se complicaban.
No puedo asegurar que esto sea una solución universal, incluso cabe la posibilidad de que todo haya sido una gran casualidad, pero si quieren probar...

Saludos y mucha suerte.

---

### Post by clasificado on 2007-11-12
[quote]Simplemente reinstalé Gutsy pero[quote]

Tramposo!!

Que bueno que pudiste solucionarlo!

Clasificado

---

### Post by elaleph on 2007-11-12
Ja, ja, ja !!! 
Sí, pero juro que antes intenté de todo y no hubo caso. Y así la cosa marchó. Obviamente, no lo hagan a menos que no encuentren otra opción o que, como a mí, reinstalar el sistema les proporcione un cierto placer oculto.
Será porque soy novato en Linux y cada instalación va marcando un hito en mi aprendizaje.

Saludos.

---

