---
title: "[SOLVED] Migración total - Particiones"
date: 2007-11-30
forum: Argentina Team
---

### Post by Radikal on 2007-11-30
Bueno, la cuestion es que ya me decidi a sacar el xp (al cual no entro desde que instale el ubuntu).
Mi duda es con respecto a las particiones,ya que en win, solo usaba NTFS, para instalar el ubuntu cree una particion en ext3 de 20 gb y una swap de 2 gb (la verdad, sobre la swap no tengo mucha idea como es, pero como lei que a uno le habian recomendado 1 gb, dije, "entonces con 2 gb voy mejor"), pero sinceramente no tengo mucha idea, y no creo que necesite tanto, ya que tengo 1 gb de ram proximo a actualizarlo a 2.

Les comento como tengo las particiones de win:

**C:** win y todos los programas (57 gb aprox.)

**D:** Música, peliculas, series, etc. (220 gb aprox)

Música y videos no estan en C, por el motivo de que en win 2x3 formateaba...

Lo que no se, es si ahora hago todas las particiones ext3 ó ¿como las hago?
Si me quieren aconsejar como distribuirlas tambien se los agradezco, el disco es de 320 gb, osea que en limpio tengo unos 290 mas ó menos.

Desde ya muchas gracias, es que quiero migrar definitivamente de una vez por todas :D

---

### Post by Mafber on 2007-11-30
Hola Radikal!!! Lo de los tamaños de las particiones, es una cuestión de gustos y de que a vos te sirva.
Lo que corregiría seria:
la unidad de swap... por lo que tengo entendido, no se necesita más de 512 mb.
y las que son ntfs las convertiría a ext3
Suerte!!! :)

---

### Post by Radikal on 2007-11-30
Muchas gracias por la respuesta!, sobre lo del tamaño era lo de menos, pero por ahi, como no pienso andar formateando tanto, capaz que la haga mas grande la de ubuntu.
Pero mi duda era esa, si las hacia ext3, ó si las dejaba en NTFS, y tanbien voy a cambiar la swap entonces, muchas gracias nuevamente ;)

---

### Post by ma_chro on 2007-12-01
Tengo algo que agregar por el tamaño de SWAP. A mi me instalaron Ubuntu en un festival de instalación de la UTN. Ahí me dijo un flaco que el tamaño del swap debía ser mínimamente el de la RAM, para cuando suspendes a disco (hibernás), toda la RAM se pasa al disco.
Espero te sirva.
Saludos

---

### Post by Radikal on 2007-12-01
Muchas gracias por la info, ya particione, deje unos 80 gb para ubuntu, la particion swap la hice de 1 gb y despues dividi el resto en 2 de unos 100 gb mas o menos.

Bye bye wind0w$ ):P

---

### Post by facundocorradini on 2007-12-01
Pues felicitaciones por el gran paso!!!!

pregunto: las otras dos particiones como las dejaste? como las montas?

---

### Post by Radikal on 2007-12-01
No entendi bien tu pregunta, pero asi es como me quedo ahora:

Swap: 1 gb
Sistema de archivos: 78.7 gb
sda6: 106.3 gb
sda5: 110.8 gb

Todas en formato ext3
Lo que no entiendo es porque me quedaron con esos numeros y no como sda1 y sda2 o como sda2 y sda3, en fin, no creo que afecte, pero es la costumbre que en win siempre me quedaban consecutivas, tipo C, D, E, etc.

---

