---
title: "problema, x fa ayudenme"
date: 2007-08-12
forum: Argentina Team
---

### Post by danukmen on 2007-08-12
bueno yege a esta comunidad por que tengo un problema con mi ubuntu feity 
y al parecer no me deja entrar como root siendo q yo soy
y me tira el siguiente eror :

danukmen@danukmen-desktop:~$ apt-get install gnokii
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13 Permiso denegado)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
danukmen@danukmen-desktop:~$ 


y para usar el snaptyc algo parecido miren :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


bueno ese es mi problema.. si alguien me puduera dar una mano estaria muy agradecido...

salu2    danuKmen

---

### Post by marianom on 2007-08-12
Cerrá Synaptic y corre la instrucción que recibís en el mensaje en una terminal:

```
sudo dpkg --configure -a
```

Eso que decís que vos sos root no entiendo bien a que hacés referencia. Si querés aclara y lo vemos.

---

### Post by Hei Ku on 2007-08-12
Pueden ser dos problemas:

El primero es que el usuario que crea Feisty por defecto es un sudoer, no un root. Lo que quiere decir es que, para la mayoria de los casos, puede impersonar al root usando el comando sudo. Pero no es root. O sea, tendrias que correr el comando con sudo adelante:

sudo apt-get install gnokii

Lo siguiente que puede ocurrir, es que realmente seas el root (si es asi, no te lo recomiendo para nada, es una invitacion para problemas y desde ya va contra todas las recomendaciones de uso de Linux o de cualquier sistema operativo que aprecie la seguridad de sus usuarios) y que tengas otro programa que está abriendo la base de administracion de paquetes. En ese caso, tendrias que fijarte antes de ejecutar el comando que hayas cerrado Synaptic, Adept, etc. Aunque me parece que tu problema va por el lado de la opcion #1

---

### Post by danukmen on 2007-08-12
si muchachos muchas gracias...
en realidad era bastante siemple la solucion.. osea la tenia adelante..
gracias por tomarce las moletia y para la proxima me fijare mejor..

   ( problema resuelto )

pd: tambien habia provado con sudo pero me avia tirado el mismo error

---

