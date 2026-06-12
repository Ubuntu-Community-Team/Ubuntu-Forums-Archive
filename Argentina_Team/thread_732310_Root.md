---
title: "Root"
date: 2008-03-22
forum: Argentina Team
---

### Post by ghertzan on 2008-03-22
Buenas!
Tengo una Preguntonta.
Como hago para loguearme como root, quiero instalar Hamachi y me pide estar logueado como root.

Saludos!!!! Toy beri japy UBUNTU es lo mejor!!!!!!!

---

### Post by newtonfn on 2008-03-22
Por lo general no es necesario nunca loguearse como root para instalar un programa. Basta con ejecutarlo con sudo (o gksudo si es gráfico) desde una terminal o desde el dialogo de ejecutar aplicación qeu aparece cuando presionas alt-f2

Si ejecutándolo así no funciona, o igualmente quiere activar la cuenta de sudo, con el riesgo de seguridad que acarrea puedes hacerlo ejecutando en una terminal:

```
$ sudo passwd root
```

Pero nuevamente, te recomiendo ejecutar los programas con sudo. En ultimo caso puedes, siempre en una terminal ejecutar "sudo su" si son muchos los comandos que quieres ejecutar como root. (En más de 2 años que vengo usando Ubuntu, jamás necesité activar root)

---

### Post by margori on 2008-03-22
Realmente no es necesario loguearse como root para instalar un programa.

Digo esto para secundar la sugerencia de nuestro amigo newtonfn.

Te recomiendo pensar en loguearse como root como ultimo recurso.

Si no me equivoco hamachi debe compilarse. Para eso se hace, en la carpeta del código fuente:

./configure
make
sudo make install

El comando sudo es el que te da privilegios de root para instalar, sin necesidad de loguearse como root. Claro que tu cuenta de usuario tiene que tener privilegios de administración, claro está.

---

