---
title: "Pantalla de inicio y tamaño de letra"
date: 2007-11-18
forum: Argentina Team
---

### Post by arielboss on 2007-11-18
Hola gente, como les va, posteo esto porque no he encontrado solucion a mi problema, y espero que ustedes sepan como hacerlo.
Tengo Ubuntu 7.10 en una dual core 2.8 con placa asus nvidia 7300 GT, y la cuestion es la siguiente:
Instale Ubuntu, todo de 10, instalo drivers restringidos, de 10, pongo resolucion en 1024 x 768, de 10, reinicio, y las letras de la pantalla de inicio estan recontra chiquitas, con una resolucion de 800 x 600 creo. Aparte, algunos dialogos del sistema se muestran con el mismo tamaño de letra, pero cuando entro en mi sesion las letras se ven perfecto.
Creyendo que podia llegar a mejorar algo, le instale el Kde, pero nada, es mas, como no tengo la sesion iniciada y personalizada, TODO esta con la letra chica, y no puedo hacer nada.

Les pido ayuda porque hace mas de 20 dias que estoy peleando con esto, y creo que en cualquier momento reinstalo de la bronca que tengo.

Gracias adelantadas
Arielboss

---

### Post by Mauro22 on 2007-11-18
En la pantalla de inicio anda probando las resoluciones con:

Control + Alt + +

---

### Post by arielboss on 2007-11-18
Gracias por la ayuda, pero hay un tema que lo que vos me decis funciona solo en exploradores, y yo tengo un problema de configuracion, que no sabia como solucionarlo, de todas formas, busque  hasta que encontre la solucion en otro foro de un problema totalmente distinto que me dio la idea.
El tema de la resolucion de mi pantalla y todo lo demas, lo tuve desde que instale los Drivers NVidia, entonces, me acorde que mi monitor no estaba listado en los modelos y tuve que elegir a 1 como el mas parecido. tengo un monitor SyncMaster 794v, entonces lo que hize fue ir a la pagina, bajarme el instalador, descomprimirlo, llevar el archivo .inf a la carpeta /root/Desktop y de ahi lo agregue a las posibles opciones para hacer correr el sistema, y LISTO!, problema solucionado.
Asi que gue, si a alguno le ocurre algo similar, pueden probar a como hize.

Gracias de todas formas

---

### Post by rojojuan on 2007-11-19
> **arielboss said:**
> Hola gente, como les va, posteo esto porque no he encontrado solucion a mi problema, y espero que ustedes sepan como hacerlo.
Tengo Ubuntu 7.10 en una dual core 2.8 con placa asus nvidia 7300 GT, y la cuestion es la siguiente:
Instale Ubuntu, todo de 10, instalo drivers restringidos, de 10, pongo resolucion en 1024 x 768, de 10, reinicio, y las letras de la pantalla de inicio estan recontra chiquitas, con una resolucion de 800 x 600 creo. Aparte, algunos dialogos del sistema se muestran con el mismo tamaño de letra, pero cuando entro en mi sesion las letras se ven perfecto.
Creyendo que podia llegar a mejorar algo, le instale el Kde, pero nada, es mas, como no tengo la sesion iniciada y personalizada, TODO esta con la letra chica, y no puedo hacer nada.

Les pido ayuda porque hace mas de 20 dias que estoy peleando con esto, y creo que en cualquier momento reinstalo de la bronca que tengo.

Gracias adelantadas
Arielboss

Anda a Sistema - Preferencias - Apariencia - Tipografías - Detalle - Resolución - aquí podés poner el tamaño que quieras. El más usado es 96. ( o 97 si querés más grande).
Fijate si te funciona, sino te doy otra solución.

---

### Post by clasificado on 2007-11-19
> **Carlitus said:**
> http://ubuntuforums.org/newreply.php?do=newreply&p=1844437][/url]
I got the same problem. Solved changing the xorg initialization (sorry if the translation is incorrect:

- Gnome menu System/Administration/Login Window (gdmsetup, the last one option).

- Tab "Security", button "Configure X Server"

- On "Command" field, add " -dpi 96" (no quotes) at the end of the command.

In my case, it solved the problem. Try it.


Yo tambien tenia el mismo problema, pero me daba fiaca arreglarlo

clasificado

---

