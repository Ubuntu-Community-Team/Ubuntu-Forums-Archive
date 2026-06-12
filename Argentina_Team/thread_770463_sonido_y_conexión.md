---
title: "sonido y conexión"
date: 2008-04-27
forum: Argentina Team
---

### Post by AndreaSant on 2008-04-27
*Problema con los parlantes ,no los reconoce el sistema.
*Hay determinadas páginas de internet,que cuando las quiero abrir aparece un cuadro diciendo que no son soportadas por el sistema

---

### Post by clasificado on 2008-04-27
> **AndreaSant said:**
> *Problema con los parlantes ,no los reconoce el sistema.
*Hay determinadas páginas de internet,que cuando las quiero abrir aparece un cuadro diciendo que no son soportadas por el sistema

aaaaaaaaaaaaaAAAAAAAAAaaaaaaaahhhhhhh...

¿Viene de otro lado esto y yo no me enteré?

Bueno, no sé. yo me tiro a la pileta lo mismo:

1) ¿Probaste con otros parlantes? ¿Que parlantes son? ¿Que placa de sonido tenés? ¿Alguna vez te habian funcionado?

2) ¿Que páginas de internet? pasanos algun ejemplo, asi vemos si tenemos el mismo problema todos.

3) ¿Que versión de ubuntu tenes? ¿Es ubuntu o kubuntu? ¿Le hiciste algo raro o es asi salido del cd?

clasificado

---

### Post by AndreaSant on 2008-04-27
1)El mensaje es "No se han encontrado complementos o dispositivos control de volumen de Gstreamer.Y si funcionaban bien.
2)Página cua "Centro Universitario de Aviación".
3)Ubuntu 8.04-desktop

---

### Post by oktubrer on 2008-04-27
> **AndreaSant said:**
> 
2)Página cua "Centro Universitario de Aviación".


¿Esta? [http://www.cua-argentina.com/](http://www.cua-argentina.com/)
Ingresé sin problemas, ¿que navegador usas? mejor posteá el error, y por las dudas si tenés windows probá entrar desde ahí.
Hay veces que determinados isp tienen problemillas de ruteo, y no sería tema de Ubuntu.  También puede ser que el sitio estuviera caído momentáneamente.

---

### Post by AndreaSant on 2008-04-27
> **oktubrer said:**
> ¿Esta? [http://www.cua-argentina.com/](http://www.cua-argentina.com/)
Ingresé sin problemas, ¿que navegador usas? mejor posteá el error, y por las dudas si tenés windows probá entrar desde ahí.
Hay veces que determinados isp tienen problemillas de ruteo, y no sería tema de Ubuntu.  También puede ser que el sitio estuviera caído momentáneamente.

Si es esa la página y el mensaje que aparece es "La página no puede ser mostrada porque usa una forma de compresión no válida o no soportada,el navegador que uso "Navegador web Firefox" creo que 3 ,desde windows siempre pude entrar

---

### Post by faktorqm on 2008-04-27
Mi opera la abre perfecta, mi firefox tb. Trabajaste durante 20 años en una oficina de telegramas? Salu2!!

---

### Post by AndreaSant on 2008-04-27
> **faktorqm said:**
> Mi opera la abre perfecta, mi firefox tb. Trabajaste durante 20 años en una oficina de telegramas? Salu2!!

Conmigo la página se niega a cooperar.
 Nunca trabajé en una oficina de telegramas,hago algo peor descifro lo que quieren escribir mis alumnos cuando escriben tipo mensaje de texto a media palabra y yo soy la "profe" de matemática.Espero sepan disculpar mi insistencia en el uso de la palabra completa para entendernos mejor,como siempre muchas gracias por responder y asistir a mis dudas,Andrea.

---

### Post by faktorqm on 2008-04-27
¿Andrea no tendra el problema del tcp_window_scaling?

Por las dudas, leete esto: [http://ubuntuforums.org/showthread.php?t=737133](http://ubuntuforums.org/showthread.php?t=737133)
No tengas miedo en hacer el cambio, no te va a afectar en nada si lo haces y el problema continua. Salu2!

---

### Post by clasificado on 2008-04-28
Yo también pude entrar sin problemas

Y al no poder reproducirlo, va a ser un poco mas trabajoso, pero vamos a intentar lo mismo:

1) Podria ser incompatibilidad de hardware: La prueba para esto es sencilla. Abrí una Terminal y tecleá esto:

```
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

Y dale [ENTER]. Es una prueba nomás. Si podés navegar la página, habrá que hacer un pequeño cambio para que quede arreglado.

2) Podria ser tu navegador de internet: Probá bajarte uno diferente para reemplazar al firefox. Te recomiendo el [Opera]("http://www.opera.com"), al menos por un rato, como para ver si es eso.

en cuanto se me ocurra algo más lo agrego

clasificado

---

### Post by AndreaSant on 2008-04-28
> **clasificado said:**
> Yo también pude entrar sin problemas

Y al no poder reproducirlo, va a ser un poco mas trabajoso, pero vamos a intentar lo mismo:

1) Podria ser incompatibilidad de hardware: La prueba para esto es sencilla. Abrí una Terminal y tecleá esto:

```
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

Y dale [ENTER]. Es una prueba nomás. Si podés navegar la página, habrá que hacer un pequeño cambio para que quede arreglado.

2) Podria ser tu navegador de internet: Probá bajarte uno diferente para reemplazar al firefox. Te recomiendo el [Opera]("http://www.opera.com"), al menos por un rato, como para ver si es eso.

en cuanto se me ocurra algo más lo agrego

clasificado

Cuando ingresé a la terminal para hacer la prueba luego del enter me apareció "Permiso denegado",sigo intentando con las otras propuestas,desde ya muy agradecida por tu ayuda,Andrea.

---

### Post by clasificado on 2008-04-29
> **AndreaSant said:**
> Cuando ingresé a la terminal para hacer la prueba luego del enter me apareció "Permiso denegado",

es cierto!! necesita permisos de superusuario. Usualmente te diria que antepongas SUDO, pero no funciona en los comandos que usan ">".

Probá así:

```
echo 0 | sudo tee -a /proc/sys/net/ipv4/tcp_window_scaling
```

Es lo mismo, pero diferente :D

clasificado

---

### Post by AndreaSant on 2008-04-30
> **clasificado said:**
> es cierto!! necesita permisos de superusuario. Usualmente te diria que antepongas SUDO, pero no funciona en los comandos que usan ">".

Probá así:

[CODE] 0 | sudo tee -a /proc/sys/net/ipv4/tcp_window_scaling

Es lo mismo, pero diferente :D

clasificado

Probé tu propuesta y me pide una orden,¿podés decirme que orden debo ingresar? Desde ya muchas gracias,Andrea.

---

### Post by margori on 2008-04-30
> **AndreaSant said:**
> Probé tu propuesta y me pide una orden,¿podés decirme que orden debo ingresar?

No te pide una orden, te esta pidiendo la contraseña con la que ingresas al sistema. Es una cuestion de seguridad. Poniendo tu contraseña, el comando ```
sudo
``` verifica que sos vos, es decir autentifica el usuario.

Lo unico es que no va mostrarte ningún caracter al ingresar la contraseña, así que deberás teclearla bien y de memoria. Si te equivocas, no pasa nada, solo no va a ejecutar el comando.

---

### Post by AndreaSant on 2008-05-02
> **margori said:**
> No te pide una orden, te esta pidiendo la contraseña con la que ingresas al sistema. Es una cuestion de seguridad. Poniendo tu contraseña, el comando ```
sudo
``` verifica que sos vos, es decir autentifica el usuario.

Lo unico es que no va mostrarte ningún caracter al ingresar la contraseña, así que deberás teclearla bien y de memoria. Si te equivocas, no pasa nada, solo no va a ejecutar el comando.

Desde ya agradecida por tus consejos,pero no funcionaron si se te ocurre otra cosa,me podrás mandar un mensaje? y si sabes como hacer para que reconozca los parlantes también.
Desde ya muchas  gracias,Andrea.

---

