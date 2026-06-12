---
title: "[SOLVED] Me cambio al kernel 2.6.24 y paquetes de Hardy?"
date: 2007-12-13
forum: Argentina Team
---

### Post by margori on 2007-12-13
Estimados amigos:

Les cuento que hace un tiempo publique un bug de Feisty y Gutsy en launchpad [https://bugs.launchpad.net/ubuntu/+bug/158555](https://bugs.launchpad.net/ubuntu/+bug/158555).

Una de las personas que está con ese tema me pidio que probara el nuevo kernel 2.6.24 que esta disponible en los repositorios de Hardy Heron (proximo Ubuntu 8.04).

La cosa que lo instale, parece a simple viste que el problema se soluciona con ese upgrade, pero como no todo el software que tengo instalado en compatible con este kernel, muchas cosas no andan.

Ahora la pregunta: Mi equipo es compartido asi que es primordial que se mantenga usable y estable. Si quiero probar el nuevo kernel, prácticamente tendría que utilizar los paquetes que estan en los repositorios de Hardy. Esos paquetes son estables o estan en desarrollo? Me quedo con el kernel y paquetes "viejos" y veo lo del bug luego o me puedo poner tranquilo a hacer prueba que la compu va a funcionar?

---

### Post by marianom on 2007-12-13
Con Hardy vas a tener muchas actualizaciones y algunas cosas con seguridad van a dejar de funcionar (y van a volver a funcionar y luego van a dejar de funcionar...) y hasta abril es un largo trecho si necesitas un sistema estable.
También va a ser complicado que tengas un sistema muy estable usando programas que fueron probados con un kernel anterior. Entiendo que la mayoría de las cosas van a funcionar pero es posible que tengas problemas en aplicaciones críticas como ser las que se relacionan con los perifericos o la red. Sigue siendo una excelente oportunidad para aprender a configurar cosas pero no se si esa es tu intención.

Mi sugerencia es que virtualices Hardy dentro de tu máquina y la pruebes en ese entorno donde no vas a tener problemas (y si las cosas se ponen muy feas borras la imagen y listo) para hacer las pruebas tranquilo.

---

### Post by Hei Ku on 2007-12-13
Tene en cuenta que ni siquiera el kernel es estable. El 2.6.24 esta en rc5, y no se espera que salga la final hasta fin de año o un poco mas. Asi que salvo que el bug sea muy complicado, mejor que te quedes en Gutsy.

---

### Post by margori on 2007-12-14
Gracias por lo datos.

Me quedaré en el kernel 2.6.22 hasta nuevo aviso. Al bug no lo pude solucionar en si, pero lo pude bypassear (evitar) El modo en que lo hice lo comento en [http://ubuntuforums.org/showthread.php?t=576188](http://ubuntuforums.org/showthread.php?t=576188)

Nos vemos.

---

