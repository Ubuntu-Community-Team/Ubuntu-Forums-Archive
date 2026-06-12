---
title: "Problema con Hojas de calculo"
date: 2008-05-08
forum: Argentina Team
---

### Post by kdk on 2008-05-08
Hola, mi nombre es juan y tengo el siguiente problema, tengo un archivo xls que contiene macros, y el openoffice no me lo abre y el gnumeric lo abre pero no puedo utilizar los macros, alguien me puede ayudar¿¿¿¿¿



Gracias!

---

### Post by clasificado on 2008-05-08
> **kdk said:**
> Hola, mi nombre es juan 
Bienvenido Juan! :KS

> y tengo el siguiente problema, tengo un archivo xls que contiene macros, y el openoffice no me lo abre

¿Te dice algo cuando no te lo abre? ¿Te tira algun cartel?

Sino probá abrirlo desde la consola (No recuerdo ahora el comando), pero asi te deja en la consola mucho mensaje adicional que suele servir en situaciones como esta

En definitiva, **en algun lugar te tiene que decir porqué no lo abre**

clasificado

---

### Post by kdk on 2008-05-09
Gracias por la respuesta, cuando lo abro via GNOME no me tira ningun error, no responde directamente, por la terminal no se abrirlo, pero ayer instale el gnumeric y lo abre, pero no me reconoce los macroe y no encontre ningun plugin k los acepte., y la verdad k no se k hacer



Gracias por la pronta respuesta

---

### Post by brunovecchi on 2008-05-10
Para abrir una planilla con Open Office Hoja de cálculos, tenés que ejecutar:

```
oocalc nombre-de-archivo
```

Asegurate de estar posicionado en el directorio en el que se encuentra el archivo que querés abrir (accedés mediante cd /ruta/del/archivo) o de ingresar como argumento la ruta completa:

```
oocalc /ruta/del/archivo/nombre-de-archivo
```

Espero te ayude a identificar el error!

---

### Post by kdk on 2008-05-13
Gracias por la respuesta!!

aparentemente ya se cual es el problema y se los paso a detallar:
estamos haciendo, en el trabajo, el transpaso a el sistema ubuntu desde Windows, y mi pc fue la primera, el problema de incompatibilidad con openoffice se debe a que queria acceder a archivos que estan en la red, pero si ese mismo archivo lo paso a mi pc lo puedo abrir sin problemas con openoffice, alguien sabe si esto podra ser asi, o sera otra cosa???

Otro problema con que me tope es que cuando genero un archivo en Gnumeric y lo guardo con formato Excel , desde Windows no lo puedo abrir.


Saludos y gracias!

---

### Post by euzkoarima on 2008-05-13
Yo uso muy poco el openoffice, sin embargo puedo abrir con doble click una planilla excel que este en un disco al que accedo por red (smb para ser más específico) sin problemas. La diferencia es que son todas planillas simples, sin macros, no se si esto influirá.

Dicho sea de paso, aca también estamos migrando, tranqui, pero avanzamos. Dentro de lo que es la migración a las pc con winbugs se les puso openoffice y de a poco todo esta en ods. Lo único en formato xls es lo que nos mandan otros por mail. Te lo comento porque me parece una buena práctica.

Saludos

---

### Post by kdk on 2008-05-19
En la terminal me pone el siguiente mensaje cuando lo trato de abrir:

 ** (soffice:5785): WARNING **: El backend no soporta la operación
(Ubicación del error desconocida)Invalid byte 2 of 2-byte UTF-8 sequence.

---

