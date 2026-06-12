---
title: "Arranque demasiado lento en Gutsy"
date: 2008-03-09
forum: Argentina Team
---

### Post by jdcane on 2008-03-09
Hola! tengo un problema extraño en gutsy.
Al momento de arrancar, apenas prendo la pc, todo va rápido, carga enseguida. Cuando aparece la pantalla de login, y después de poner nombre y contraseña, pasan 6 minutos (contados por reloj) hasta que carga el escritorio. A partir de ahi toda va perfecto, rápido, sin problemas, uso todo normalmente. 
La verdad que busque información o si a alguien le pasa algo parecido, pero no encontré. Y no tengo idea de lo que puede ser.

Lo que se es que si desconecto el cable de conexión a internet, antes de prender la pc, en lugar de 6, son 2 o 3 minutos de carga entre el login y el escritorio. Y después, una vez prendida, si vuelvo a conectar la pc al modem, no lo reconoce, y no se conecta. 

También me parece que esto empezó a pasar después de configurar un archivo (/etc/init.d/rc) y cambiar “CONCURRENCY=none”por “CONCURRENCY=shell” al iniciar me daba un error de hal, errores con dbus y la conexion ethernet, (al parecer a causa de un bug: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881") ) y despues de tocar e intentar varias cosas, se soluciono con esto
    $ sudo mv /etc/rc2.d/S12hal /etc/rc2.d/S13hal
    $ sudo mv /etc/rc3.d/S12hal /etc/rc3.d/S13hal
    $ sudo mv /etc/rc4.d/S12hal /etc/rc4.d/S13hal
    $ sudo mv /etc/rc5.d/S12hal /etc/rc5.d/S13hal

no hubo mas errores, pero el arranque quedo demasiado lento.


Cualquier ayuda es bienvenida
Desde ya gracias.

---

### Post by Mauro22 on 2008-03-09
Es normal que tarde en aparecer el escritorio.

A mi me tarda unos 2 minutos, mas o menos.
Pero vale la pena :D


Saludos!

---

### Post by facundocorradini on 2008-03-09
No, no es para nada normal. A mí no me tarda más de cinco segundos entre el login y el sistema "100 usable".

Que compu tenés? cuanto hace que instalaste Ubuntu? Siempre te andubo así?

---

### Post by jdcane on 2008-03-09
tengo:
amd 1100 a 1.9 Ghz
1gb de Ram
nvidia geforce 6100
disco 80 gb

instale ubuntu 7.10 en diciembre del año pasado, y este problema lo tengo desde hace un mes, despues de haber cambiado cosas en ese archivo (/etc/init.d/rc)

todo lo demas funciona sin problemas

---

### Post by facundocorradini on 2008-03-09
Por seguir el primer tutorial que uno se cruza por la red....

El AMD 1100 es un procesador de un solo nucleo, y la opción de Concurrency es para aprovechar los procesadores multinucleo en el arranque. 
Decirle al sistema que aproveche varios nucleos teniendo uno solo, únicamente puede generar errores...

Fijate si cambiando el concurrency a "none" se arregla, sino por ahí te sirve una copia de mi archivo... después te la adjunto

saludos y suerte

---

### Post by pol666 on 2008-03-09
uh y yo me quejo que tarda 15 seg :S

---

### Post by jdcane on 2008-03-09
Cambie a concurrency=none, reinicié, pero sigue igual.

---

