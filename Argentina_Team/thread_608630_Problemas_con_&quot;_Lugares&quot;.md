---
title: "Problemas con &quot; Lugares&quot;"
date: 2007-11-10
forum: Argentina Team
---

### Post by marcesneibrun on 2007-11-10
Hola, tengo instalado ubuntu 7.10, necesito ayuda porque no se que debo haber tocado ya que cuando ingreso  a "Lugares" y trato de abrir cualquier programa que esta dentro de esta carpeta sea carpeta personal, fotos familia, etc ; no me abre nada, no se que es lo que pasa, agradecería si alguien puede ayudarme.
Antes no tenia este problema.
Gracias.
Marcelo

---

### Post by sajnox on 2007-11-10
¿como es nada?

Que usuario estas usando??

si no tenes permisos para ver los archivos no te deja verlos

proba lo siguiente: abri el nautilus con permisos de root y fijate si asi te deja

alt + f2 y escribis gksudo nautilus /home

te pide la contraseña y abre nautilus, si asi lo podes ver es que tenes que modificar los dueños de los archivos

Si esto es el problema, despues te explicamos como modificarlo

Saludos

---

### Post by marcesneibrun on 2007-11-10
Gracias sajnox por contestarme, te cuento q con aplicaciones y sistema no tengo el problema, solo con la carpeta lugares; no se si tendra algo que ver pero el procesador me aparece 100% en uso y no baja de ahi.
Ya la reinicie y no cambio.
No se que puedo hacer.
Gracias por tu respuesta.
MArcelo

---

### Post by sajnox on 2007-11-10
Procesador en uso al 100%!!!!

Que proceso es el que te lo come??

Para poder verlo:

Sistema/Administracion/Monitor del Sistema

---

### Post by marcesneibrun on 2007-11-12
el proceso que esta casi al 80 y 90 % es " nautilus"
Gracias por contestar.
Marcelo.

---

### Post by sajnox on 2007-11-12
Hace muy poco nautilus me hizo algo parecido (habia reorganizado la carpeta de fotos), simplemente mate el proceso y cuando volvi a abrir la carpeta no tuve mas problemas y anda todo bien.

Al proceso lo podes matar desde

Sistema/Administracion/Monitor del Sistema

click derecho en el proceso / matar proceso

---

