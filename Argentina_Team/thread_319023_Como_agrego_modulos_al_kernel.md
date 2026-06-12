---
title: "Como agrego modulos al kernel?"
date: 2006-12-14
forum: Argentina Team
---

### Post by quaid on 2006-12-14
Tube un problema con el sonido q no andaba, probando con modprobe en cargar los modulos de sonido me encuentro con q estos no estan.

En el kernel me falto todo el directorio sound/pci.

Queria saber com ose hace para agregar todo estos modulos, el kernel lo baje, perfecto. y ahora?

Uso edgy

---

### Post by lavaramano on 2006-12-17
fijate por ahi que yo hace poco puse un howto compilar kernel, por ahi eso te ayude un poco.

---

### Post by quaid on 2006-12-18
> **lavaramano said:**
> fijate por ahi que yo hace poco puse un howto compilar kernel, por ahi eso te ayude un poco.

Exactamente agarre ese howto, muy bueno, ya lo compile anda el sonido y todo.

Asi q x eso deduzco q no hay forma de agregar modulos excepto recompilando el kernel no?

---

### Post by jpmorelli on 2006-12-18
Si que hay forma, hay unos comandos para correr los modulos sin compilarlos en el kernel, si no me equivoco y que alguno me corrija si no es asi.

lsmod: lista los modulos cargados
modprobe: carga o descarga modulos en el kernel( durante la sesion )
insmod: inserta modulos en el kernel ( cual es la dife con el anterior ??? )

pero bueno, lo que quiero decir es que si hay maneras de decirle al kernel, cargalo vos compilalo dentro del kernel o carga el modulo por separado.
Alguien que sepa un poco más y nos explique a ambos ? jajaja

---

### Post by lavaramano on 2006-12-18
metiendo archivos en /lib/firmware? :-k 
perdon si nada que ver, pero al menos los modems usb los hice funcionar asi.


> **jmorelli said:**
> Si que hay forma, hay unos comandos para correr los modulos sin compilarlos en el kernel, si no me equivoco y que alguno me corrija si no es asi.

lsmod: lista los modulos cargados
modprobe: carga o descarga modulos en el kernel( durante la sesion )
insmod: inserta modulos en el kernel ( cual es la dife con el anterior ??? )

pero bueno, lo que quiero decir es que si hay maneras de decirle al kernel, cargalo vos compilalo dentro del kernel o carga el modulo por separado.
Alguien que sepa un poco más y nos explique a ambos ? jajaja

---

### Post by quaid on 2006-12-19
Buena pregunta, tb esta el confmod.

Segun me parece (me parece) el modprobe lo carga solo para la sesion actual. el confmod lo activa y queda asi.
insmod me pedia un archivo q no se de donde sacarlo, lo mas seguro q se instalen con esto pero no se de donde sacar el modulo. 

Seria bueno q alguien eche un poco d eluz al tema

---

