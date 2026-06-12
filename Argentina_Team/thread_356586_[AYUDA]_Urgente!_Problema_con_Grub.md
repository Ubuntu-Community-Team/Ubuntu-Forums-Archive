---
title: "[AYUDA] Urgente! Problema con Grub"
date: 2007-02-08
forum: Argentina Team
---

### Post by Biasoli on 2007-02-08
Aca estoy por 3ra vez, pero esta es la peor de todas.
Resulta que en otro thread habia pedido ayuda acerca de como desinstalar Linux.
Bueno, la particion de Linux la borre.
El problema es el siguiente:
Al instalar Linux, antes de arrancar ningun SO, me aparecia un tal Grub que me permitia elegir entre Linux y Windows para arrancar.
Al borrar la particion de Liunx, supuse que este programa tambien iba a borrarse. Y digamos que me equivoque.
Ahora, el unico SO en mi maquina es Windows, pero al prender la PC me aparece este tal Grub tirandome el error 22 y quedandose ahi.
Lo unico que puedo hacer es apagar la maquina.
¿Alguna idea de como solucionar esto?

Gracias!

PD: no quiero sonar pretencioso, pero en lo posible no mencionen formatear, ya que eso lo haria como ultimo recurso unicamente.

---

### Post by screening on 2007-02-08
Pones el cd de Windows XP, arrancas la pc desde él, cargas a la consola de recuperacion y pones "fixmbr" (sin las tildes), contesta que YES a la pregunta y listo...

---

### Post by Biasoli on 2007-02-08
> Pones el cd de Windows XP, arrancas la pc desde él, cargas a la consola de recuperacion y pones "fixmbr" (sin las tildes), contesta que YES a la pregunta y listo...


Excelente!
Funciono!!!
Muchas, muchas gracias!!!


Saludos!!

---

### Post by quaid on 2007-02-08
o tb con un disoc de arranque pones fsdisk /mbr y listo. 

Ahora ya sabes, fdisk mbr antes q todo

---

### Post by Biasoli on 2007-02-09
Perfecto, gracias, eso tambien me viene bien.


Saludos!

---

