---
title: "Modificar particion swap"
date: 2007-09-18
forum: Argentina Team
---

### Post by niko_3100 on 2007-09-18
Bueno gente en realidad no es un problema ni na' raro, cuando instale ubuntu en mi maquina la persona que me inicio en el codigo abierto me dijo que siempre es recomendable hacer una particion swap que sea el doble de espacio de lo que tens de memoria ram. Esto me parecia logico si tenes 256 de ram o 512 de ram hacer una particion swap el doble de la ram osea 512 o 1 gb de swapeo entonces siguiendo ese concepto hice una particion swap del doble de mi ram o sea 3gb :guitar: es decir que tengo 1,5 gb de ram y la verdad que la particion swap esta mas al **** qe bocina en avion siempre esta en 0% y la ram como una barbaridad me llega a consumir 600 mb cuando trabajo con cosas pesadas. Entonces mi pregunta es la siguiente hay alguna forma de achicar esa particion swap y hacerla mas chica? asi puedo ganar 1,5 gb mas en mi disco rigido para aprovechar y guardar cosas mias? Si la respuesta es NO, TENES QUE INSTALAR UBUNTU DE CERO, entonces obviamente que no da. Muchas gracias.

---

### Post by Montsegur87 on 2007-09-18
Bootea con el live cd , abri el gparted , resize.

---

### Post by por100pre1 on 2007-09-18
Si, haz como te indicó Montsegur87. Lo maximo para tu configuración es 2.5G de los cuales quizas solo se use el 1%. Solo usaría mucha swap en caso de hibernación (si es que la logras poner tu PC a hibernar). Puede que requieras usar el comando swapon al reiniciar tu PC:

```
sudo swapon /dev/hdx
```

sustituyendo /dev/hdx con lo que corresponda a la particion de swap segun el resultado provisto por este commando:

```
sudo fdisk -l
```

---

