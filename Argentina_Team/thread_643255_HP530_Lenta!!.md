---
title: "HP530 Lenta!!"
date: 2007-12-17
forum: Argentina Team
---

### Post by sharkg on 2007-12-17
Hola a todos. bueno les comento q me compre una HP 530, pero ademas la lleve a 2Gb de ram, en teoria me tiene que andar como un avion, pero no es asi.. :( no se q tiene pero como que no anda bien, lo primero q pense es en la memoria, pero le hice varios test de mas de 1 hora c/u y no paso nada!! ningun error. pense en drivers, pero lei que el gusty reconoce completamente a esta HP.. asi q no se que puede ser..
les comento que demora mas de 1 min en cargar el escritorio, pongo q inicie y demora mucho... la verdad no se que puede ser!! alguno le paso lo mismo o tiene alguna idea para ayudar.. gracias y saludos

---

### Post by Mister X on 2007-12-17
Fijate si tenes algun proceso que te coma la cpu. En la consola pone:
```
top
```

Que micro tiene, yo con un core 2 duo + placa intel tube un problema con un proceso, creo que era el kacpid, se disparaba el % de uso de la cpu.

---

### Post by sharkg on 2007-12-17
el micro es un T5300 e
no tiene nada de uso el micro.. nada de nada...
para mi la mano viene por algo mal configurado o q no encuentra y por eso demora en cargar...
hay alguna forma de ver eso? yo hasta donde busque esta todo bien.. no me aparece nada raro..
en la parte de servicios. el ajuste de disco puede q me haga lenta la cosa??

---

### Post by Mister X on 2007-12-17
Solamente notas lentitud en el booteo? fijate con el comando 
```
dmesg
```
los mensajes que tira al bootear, por si hay algo sospechoso, tambien podes sacarle el parametro de inicio "splash", asi te muestra el progreso del booteo para ir viendo donde esta la demora.
Tambien debés tener en cuenta que los discos de las notebooks son lentos (normalmente 5400 rpm), por lo que recien vas a notar la ventaja de tener 2GB de RAM despues de un rato de uso y cuando tenga los programas que estas usando en memoria

---

### Post by sharkg on 2007-12-17
si es verdad... debe de ser el disco tonces! es lento, es verdad! pero bueno veremos q pasa si pongo el servidio de optimizado de disco.. sirve o solo come recursos??

---

### Post by niko_3100 on 2007-12-18
anda a una terminal y hace:

sudo gedit /boot/grub/menu.lst
...y la contraseña jejej

se abrira un archivo de texto, desplazate hasta el final donde dice:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet **splash**

... o similar. Solo ttenes  que cambiar 'splash' por **'nosplash'**. Reinicia y celébralo!


Algo offtopic, me podrias decir cual es la temperatura mas o menos del core duo? Gracias.

Con esto lo que haces es que en ves de bootear y te aparesca el logo de ubuntu con la barrita naranja cargandose te va a tirar todos los servicios o procesos que va a levantar mientras bootea, supongo que con el que mas va a tardar se va a quedar y vas a poder ver que es y despues desabhilitarlo.

---

### Post by sharkg on 2007-12-18
bueno ahora como q me anda bien! no se q le pasa! esta loca!
pero el drama lo tengo despues del boot, es decir, q carga lento la pantalla despues de poner el usuario y contraseña! seguro q por el disco q tarda!

decime si tenes algun programa para ver la temperatura del micro y demas asi lo veo.. la verdad q busque y no encontre nada q me tire esa info! jeje

---

### Post by Hei Ku on 2007-12-18
instala lm-sensors

despues a veces tenes que hacer sensors-detect para que detecte los sensores de temperatura. Otras veces lo hace automatico.

y despues con el conky, o algun otro programa podes ver los datos de los sensores.

---

### Post by sharkg on 2007-12-18
bueno voy a ver q onda eso!!! cualquier cosa pregunto jeje gracias.

---

### Post by sharkg on 2007-12-18
bueno dure poco!! jejeje
instale con conky, pero no me sale la temp del cpu!! jeje.. me fije y me sale de todo un poco de info del cpu, pero nada de temp!!!
como hago pa poder ver eso? 
gracias y saludos

---

### Post by sajnox on 2007-12-19
Si bien algo indague tampoco me volvi loco, pero no pude ver la temperatura con conky y me termine resignando a un applet de gnome, lo podes agregar haciendo click derecho en cualquiera de las barras de tareas (obvio que aplica si usas ubuntu y no cualquier otro *buntu)

---

### Post by rojojuan on 2007-12-20
> **sharkg said:**
> Hola a todos. bueno les comento q me compre una HP 530, pero ademas la lleve a 2Gb de ram, en teoria me tiene que andar como un avion, pero no es asi.. :( no se q tiene pero como que no anda bien, lo primero q pense es en la memoria, pero le hice varios test de mas de 1 hora c/u y no paso nada!! ningun error. pense en drivers, pero lei que el gusty reconoce completamente a esta HP.. asi q no se que puede ser..
les comento que demora mas de 1 min en cargar el escritorio, pongo q inicie y demora mucho... la verdad no se que puede ser!! alguno le paso lo mismo o tiene alguna idea para ayudar.. gracias y saludos

Si tenés un procesador AMD probá eliminando desde Sinaptic powernowd; a mi me funcionó. Si no es eso, volvés a instalarlo y listo.

---

### Post by sharkg on 2007-12-20
bueno les comento que hice....
instale Win Xp y no me reconocia el disco... foreando encontre q hay q desabilitar el disco en sata... raro, pero si es asi la cosa.
Instale Win y vuela la maquina... me dio bronca e instale ubuntu con la misma config de disco y aparentemente anda bien ahora, carga rapido, no le instale nada, esta base, pero almenos al abrir la terminal me la abre al toque y no demora en cargar la sesion...
espero q el problema fuera eso solo.... pero me parece raro, no?

---

