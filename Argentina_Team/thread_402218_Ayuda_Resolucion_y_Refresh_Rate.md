---
title: "Ayuda: Resolucion y Refresh Rate"
date: 2007-04-05
forum: Argentina Team
---

### Post by MarcosDV on 2007-04-05
Buenas, nadie me conoce, soy nuevo por aca y tambien nuevo en esto de linux... y la verdad que me cope con ubuntu y ahora tengo un problemita, aver si me pueden dar una mano...
Tengo un monitor Samsung SyncMaster 793s que por lo que se soporta hasta 1280x1024 75hz, pero cuando pongo esa resolucion no me da para elejir el refresh rate, solamente me aparece de 60hz y la verdad que me parte la vista, me gustaria saber como poder tener esa resolucion con un refresh rate de 75hz.

Uso Ubuntu Edgy, y tengo una placa Nvidia GeForce 5500

Desde ya gracias :)

---

### Post by Nemesis Teufel on 2007-04-05
Lo cambias con el boton secundario en el escritorio o vas a Sistema/Preferencias/Resolucion de la pantalla? Hacelo con la segunda opcion que te doy.

Tenes instalados los drivers de la placa de video?

---

### Post by MarcosDV on 2007-04-05
Tal cual, para cambiarlo hago como vos dijiste, y si, tengo los drivers de la placa instalados. 
Escuche que se soluciona editando algo del xorg.conf pero no estoy seguro...

Gracias igual!

---

### Post by Federick on 2007-04-05
Hola Marcos.

A mi me pasaba lo mismo con mi SyncMaster 753s.

Lo que hice fue utilizar el GUI del editor del xorg.conf usando:
sudo dpkg-reconfigure xserver-xorg

No tenés que cambiar nada excepto en el momento que tenés que ponerle los rangos de frecuencia del monitor, te fijás en tu manual, y ponés los rangos horizontales y verticales correspondientes.

Si salió todo bien, al reiniciar las X (Alt+Ctrl+Backspace) vas a poder elegir resoluciones superiores.

Agrego que a mi hasta me da hasta la opción de 87 en 1024x768 pero no me animo a probarla.

Cualquier duda chiflá.

Saludos.

---

### Post by Federick on 2007-04-05
¡No te olvidés de hacer un backup del xorg.conf !

(sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.resguardo)

Saludos.

---

### Post by MarcosDV on 2007-04-05
Gracias Federick, voy a probar con eso y en un toque edito y digo que pasó...

Mirá, segui los pasos, toque todo ESC hasta que llegue a la parte del monitor, y puse como horizontal 30-70 y vertical 50-160 (lo saque de internet, no encuentro el manual) y haciendo esto como bien dijiste, tengo la opcion de 1024x768 a 87hz y y también 1152x864 a 75hz, que antes no tenia, pero sigo sin poder poner 1280x1024 a 75hz, me da nada mas la opción de 60.
Vos que tenes el mismo monitor, me podrías decir si los valores que puse como horizontal y vertical estan bien? Y sino, si estoy haciendo algo mal en la configuracion?

Saludos!

---

### Post by Federick on 2007-04-05
Hola Marcos.

El problema mío era peor, no podía tener en 1024x768  más de 60Hz.
En mi equipo agregué recién modos hasta 1280x1024 y me pasa lo mismo, nada más 60Hz en la máxima.
Pero 75Hz en 1152x768 no están tan mal para mi.

No sé que decirte. Pero no tenemos el mismo monitor (Aunque por lo que parece son los mismos valores).

Saludos.

---

### Post by MarcosDV on 2007-04-05
Ok, muchas gracias igual, la verdad me ayudaste mucho :) 

Saludos y gracias!

---

