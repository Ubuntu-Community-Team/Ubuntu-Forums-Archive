---
title: "[SOLVED] Problema con Azureus"
date: 2007-10-02
forum: Argentina Team
---

### Post by Oktubre on 2007-10-02
Hola Gente,

ayer abri el Azureus, puse a bajar un archivo y al rato se me cerro. 

Luego de esto cada vez que lo intento abrir, cuando termina de abrir, se me cierra.

Practicamente no lo utilizo nunca, y habra durado abierto no mas de 20 minutos. 

Alguna idea? Gracias.

Saludos.

---

### Post by nest on 2007-10-02
abrilo desde la consola y pastea el error que te tira.

---

### Post by marianom on 2007-10-02
Si es Edgy tener en cuenta [este bug]("https://launchpad.net/ubuntu/+source/azureus/+bug/57875").

Si es Feisty debería andar. Por las dudas pegale una leída a [este wiki]("https://help.ubuntu.com/community/AzureusHowTo").

---

### Post by Oktubre on 2007-10-03
Gracias por las respuestas.

Segui los pasos que están [acá]("http://ubuntuparanovatos.wordpress.com/2007/06/06/problemas-con-azureus/"), porque ya tenia instalado el Azureus, por ahora funciona sin problemas.

Saludos,

---

### Post by LaHire on 2007-10-03
> **Oktubre said:**
> Gracias por las respuestas.

Segui los pasos que están [acá]("http://ubuntuparanovatos.wordpress.com/2007/06/06/problemas-con-azureus/"), porque ya tenia instalado el Azureus, por ahora funciona sin problemas.

Saludos,

Esperemos que siga así =)

Si no te es molestia (y apenas "sientas" que el error se fué :)), editá el nombre del Thread y ponele un [SOLVED] antes del nombre, así personas con el mismo problema pueden ver el thread Y/O la gente que quiere ayudar va directo a los hilos sin resolver :)

espero que te siga funcionando!

---

### Post by Oktubre on 2007-10-04
Bueno, ayer cuando lo volvi a abrir nuevamente se me cerraba. 

Entonces ejecuto lo siguiente: 

sudo update-alternatives –config java

selecciono que corra con la siguiente opcion de java: 

/usr/bin/gij-wrapper-4.1

luego lo cierro y le vuelvo a poner que corra con la opcion default de java (que tenia anteriormente).

Asi me funciona sin problemas, ya van dos dias que lo vengo utilizando.

Saludos,

---

### Post by WanderingKnight on 2007-10-07
Solo queria agregar que, habiendome encontrado con este mismo problema, simplemente opte por bajar el binario precompilado de la pagina oficial de Azureus, que funciona a la perfeccion.

---

