---
title: "Problemas con el audio"
date: 2007-02-28
forum: Argentina Team
---

### Post by zspikes on 2007-02-28
Buenas gente!
no se q diablos paso q perdi el sonido :S Estaba tocando unas opciones de beryl y no se por q perdi el puntero del mouse, entonces aprete ctrl+alt+F1 para poner reboot, como no pude me desespere y aprete ctrl+alt+supr y se reinicio. La cosa es q cuando se volvio a abrir ubuntu, me encontre conq ya no tenia sonido! :(

alguien me da una manito? gracias!!!

---

### Post by beuno on 2007-03-01
A ver, primeros lugares para buscar errores:

/var/log/dmesg
/var/log/kern.log
/var/log/messages


Empeza a navegar por ahi buscando errores de sonido, y sino, postea aca los 3 y vemos que podemos hacer.

---

### Post by quaid on 2007-03-01
a mi em paso exactamente lo mismo uan vez y me volvi loco, probe todo.
Algo q me re ayudo en mi caso fue el hwinfo -sound

Me decia q sonido tengo y si los modulos estaban cargados, los cargaba con modprobey no me andubo a mi.

Reinstale ALSA y etc y no habia caso.

La unica solucion q encontre sin tener q reinstalar linux fue compilando un nuevo kernel.
Tomalo como ultima opcion

---

### Post by marianom on 2007-03-01
A mi reinstalar Alsa me funcionó así que le pedí a zspikes ayer que lo hiciera pero tampoco tuvo suerte. Esperemos que no tenga que seguir tu camino.
Vamos a ver que dicen esos logs.

---

### Post by zspikes on 2007-03-01
> **beuno said:**
> A ver, primeros lugares para buscar errores:

/var/log/dmesg
/var/log/kern.log
/var/log/messages


Empeza a navegar por ahí buscando errores de sonido, y sino, postea aca los 3 y vemos que podemos hacer.

perdona q sea tan animal, pero donde busco eso? q me tengo q fijar? :S

Ya probé revisar todo el tema de hardware, esta todo bien conectado, no falla nada. El sonido no esta en silencio ni nada de eso, asiq queda descartado. Me resulta muy raro q cueste tanto, porq apenas instalas ubuntu, te agarra todo sin problemas :S
Y la de reinstalar el sistema la tomo como uuuuuuuuultima posibilidad, ya q tengo el cd de ubuntu 6.06, y para tener edgy tuve q dejar la pc actualizando como 12 horas :S

---

### Post by marianom on 2007-03-01
Hace 

```
vim /var/log/dmesg
vim /var/log/kern.log
vim /var/log/messages

```

o 

```
gedit /var/log/dmesg
gedit /var/log/kern.log
gedit /var/log/messages

```

lo que te sea más cómodo. Con cada instrucción se abrirá el archivo de logs (algunos largos) donde podrás intentar detectar algún mensaje de error con el sonido.
Si no sale o no ves nada, tar.gz a todo y subilo al foro.

---

### Post by zspikes on 2007-03-01
ahi le heche una revisadita a los archivos, y a simple vista no hay nada q llame la atencion. De todos modos uds sabran mas q yo, aca dejo los ficheros.

bytes!

---

### Post by beuno on 2007-03-01
> **zspikes said:**
> ahi le heche una revisadita a los archivos, y a simple vista no hay nada q llame la atencion. De todos modos uds sabran mas q yo, aca dejo los ficheros.

bytes!

A simple viste no se ve ningun error grave.
Eso es bueno y malo.
Bueno porque no es algo grave, pero al no habe algo muy evidente es mas dificil puntualizar el error.
Te diria que sigas el consejo de Mariano, y reinstales alsa.

---

### Post by zspikes on 2007-03-01
si, ya reinstale alsa... ocea, lo q hice fue buscar en el synaptic todo lo q sea "sound" y reinstalar los paquetes ALSA... no se si hice bien. Si es asi, no me funciono.

No tengo problema con reinstalar el OS, el problema es q tengo en cd 6.06 y me da fiaca actualizar a 6.10... esta tarde deje bajando edgy por las dudas, y llego al 95% y se quedo ahi :@

---

### Post by zspikes on 2007-03-02
Bueno, en vista de q no podia solucionar el problema, baje ubuntu 6.10 lo copie a un cd y lo reinstale... tube q instalar todo de nuevo!!! fue una tortura... pero ahora anda el audio y estoy escuchando dream theater! :D jaja

gracias a todos! bytes!

---

### Post by godzeus on 2007-03-03
yo tengo un problema similar, tengo una placa de sonidoon board, y una soundblaster Live,.
Cuando el sistema arranca es como que detecta siempre las dos placas a psar que la onboard esta desconectada, y me reconoce como dispositivo 0 y 1, pero en algunos casos me reconoce la soundblaster como 0 y la onboard como 1, en estos casos tengo que editar a mano el asound.conf.
Alguien sabe porque sucede esto y alguna solucion.?

Gracias y saludos

---

### Post by jpmorelli on 2007-03-04
Si tu mother es de los modelos PC-Chips te aviso que no bastaba con deshabilitar el audio desde el setup sino que además tenían un jumper cerca de las salidas de audio que había que cambiar de posición para anularla completamente.
En todo caso fijate por la web del fabricante si podés conseguir el manual del modelo exacto y ahí va a mostrar exactamente como desactivar el audio on board.
Suerte !

---

