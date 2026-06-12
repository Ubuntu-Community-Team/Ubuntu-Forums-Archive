---
title: "Mantenimiento de Pc en Ubuntu Hardy?"
date: 2008-05-14
forum: Argentina Team
---

### Post by smrdelj on 2008-05-14
Hola buenos dias.

Desde que instalé Ubuntu me pregunto si, como sucede en Windows, hay programas de mantenimiento (limpieza de disco y de registro; limpieza de spyware; defragmentacion de disco y registro; scandisk; etc). 

Hay algo?

Por otro lado, ¿Es necesario hacer mantenimiento en Ubuntu? O es tan estable que no lo necesita?

Sinceramente, soy muy obsesivo de tener el OS siempre como nuevo y andando de 10; es por esto que me gustaría que me recomendaran algun programa de mantenimiento copado (tipo TuneUp Utilities).

Gracias, saludos.

---

### Post by Applelnx on 2008-05-14
Mira, de esto se muy poco, pero lo que me habian comentado es que en linux no era necesario desfragmentar el disco duro por mucho tiempo.

Pero no se bien, espera la respuesta de alguien mas ducho en linux ;)

---

### Post by faktorqm on 2008-05-14
Hola, segun tengo entendido no existen muchas cosas de las que vos nombras y por lo tanto no existen herramientas para eso.

Fragmentacion: Los sistemas de archivos EXT3 no fragmentan. En realidad es mentira que no fragmenta, el truco esta en que esa fragmentacion es tan tan chica, que bajo ningun punto de vista afecta al rendimiento. Pensa que esta tabulado el valor en un 0,001%. (que alguien me corrija si esta mal ese valor)
resumen: No existe defragmentador por que no fragmenta.

spyware/virus/adware/malware: no existen, asi ke nada. (existen antivirus para windows que corren en linux, pero eso es otra cosa)

registro tampoco existe, por suerte. cada configuracion de los programas se guarda en un archivo de texto y no depende de una base de datos en memoria.... :D

limpieza de disco tampoco hace falta, por que linux utiliza una particion aparte para swapear, por lo tanto podes estar con 1 mb libre y el sistema te anda igual. (en realidad no es tan asi, por el tema de los logs, pero bueno)

lo mas parecido a scandisk es fsck. peeeeero ubuntu automaticamente te lo pasa cada 30 montadas de una particion, o cuando se te corto la luz y no pudiste apagar la pc, por lo tanto tampoco hace falta que vos lo pases a mano.

Salu2!! :KS

---

### Post by Thalskarth on 2008-05-14
> **faktorqm said:**
> Hola, segun tengo entendido no existen muchas cosas de las que vos nombras y por lo tanto no existen herramientas para eso.

Fragmentacion: Los sistemas de archivos EXT3 no fragmentan. En realidad es mentira que no fragmenta, el truco esta en que esa fragmentacion es tan tan chica, que bajo ningun punto de vista afecta al rendimiento. Pensa que esta tabulado el valor en un 0,001%. (que alguien me corrija si esta mal ese valor)
resumen: No existe defragmentador por que no fragmenta.

spyware/virus/adware/malware: no existen, asi ke nada. (existen antivirus para windows que corren en windows, pero eso es otra cosa)

registro tampoco existe, por suerte. cada configuracion de los programas se guarda en un archivo de texto y no depende de una base de datos en memoria.... :D

limpieza de disco tampoco hace falta, por que linux utiliza una particion aparte para swapear, por lo tanto podes estar con 1 mb libre y el sistema te anda igual. (en realidad no es tan asi, por el tema de los logs, pero bueno)

lo mas parecido a scandisk es fsck. peeeeero ubuntu automaticamente te lo pasa cada 30 montadas de una particion, o cuando se te corto la luz y no pudiste apagar la pc, por lo tanto tampoco hace falta que vos lo pases a mano.

Salu2!! :KS

En resumen:

Olvidate y disfrutá :)

---

### Post by smrdelj on 2008-05-14
Barbaro! Todo tal cual suponía (pero preferí preguntar por si acaso :$)

Muchas gracias, saludos!

---

### Post by niko_3100 on 2008-05-14
Te diste cuenta porque linux es mejor?

---

### Post by Hei Ku on 2008-05-14
Y ahora que vas a hacer con tanto tiempo libre?


Relajate y gozá! :lolflag:

---

### Post by Mauro22 on 2008-05-14
El tema de la defragmentacion es asi:

La diferencia entre windows y gnu/linux es que usan un sistema completamente diferente.

Windows, al querer escribir datos en el disco, busca lugares vacios y escribe. Es decir, un mismo archivo puede estar en pedazos a lo largo del disco.

**Esto hace mas rapida la escritura y mas lenta la lectura**

Gnu/Linux en cambio, cuando quiere escribir, busca un lugar vacio lo suficientemente largo para que entre todo.

**Esto hace mas lenta la escritura y mas rapida la lectura, pero el disco no se fragmenta**



En resumen, cuanto mas usas Windows, peor va a andar ( + defragmentacion); cuanto mas uses linux mas rapido te va a andar ( 0 fragmentacion, los archivos "frecuentes" son indexados)

---

### Post by Hei Ku on 2008-05-14
de hecho, ext3 se fragmenta aunque en mucha menor medida que ntfs. Estamos hablando de años, en lugar de semanas o meses. Pero al ser un sistema basado en journaling, la mayoria de los problemas se resuelve mas facil, como el caso del readahead, para acelerar el booteo. Si te gusta tunear, busca en este foro por readahead y vas a encontrar un par de cosas.
Tambien podes sacarle el access time a las particiones ext3, eso evita que actualice el ultimo tiempo de acceso a los archivos y hace que la lectura sea un poco mas rapido.
Pero en resumen, la mayoria de los tuneos se hacen sobre cosas finas, y no existen "procesos de mantenimiento" como en el innombrable.

---

### Post by vk-cdg on 2008-05-15
> **smrdelj said:**
> Hola buenos dias.

Desde que instalé Ubuntu me pregunto si, como sucede en Windows, hay programas de mantenimiento (limpieza de disco y de registro; limpieza de spyware; defragmentacion de disco y registro; scandisk; etc). 

Hay algo?



Existen antivirus de distintos fabricantes, por ejemplo Avast, AVG, etc, pero es mas marketing que otra cosa. Yo no tengo instalado nada y hasta ahora no tengo ningún problema.
Puedo sugerirte que le pegues una mirada a la configuración de tu firewall (sobre todo si dejás la PC encendida siempre y conectada a internet) no se que tan configurado viene por default, pero mas que eso no tenés que hacerle.

---

### Post by User21 on 2008-05-15
Si no querés aburrirte, ahora que no tenes nada que "mantener" podes borrar tus fotos, o archivos de música.. moverlos a otra carpeta... Desinstalar e instalar aplicaciones... Todo eso para recordar viejos malos tiempos. 
Por otro lado, si querés invertir aún mejor tu tiempo, podes leer y releer tutoriales, ayudar en traducir porciones de software via Launchpad, podés colaborar dando soporte o ayuda en los chats a la gente que pregunta cosas que vos ya dominas, podes probar instalar Ubuntu en otras maquinas, promover el soft libre, o incluso, quedarte sin HACER NADA de NADA. Solo disfrutar de tu fabuloso sistema operativo. 
Damos este post como **SOLVED** ? (Busca en Thread Tools, de esta pagina).

---

### Post by margori on 2008-05-15
> **vk-cdg said:**
> ...Puedo sugerirte que le pegues una mirada a la configuración de tu firewall ... no se que tan configurado viene por default, pero mas que eso no tenés que hacerle.

Por defecto el firewall está desactivado, todos los puertos salientes abiertos y entrantes tambien. Si un programa quiere mandar algo a la red, no tiene ningun problema para hacerlo. Si algun paquete entrante es enviado a un puerto que ningun programa esta escuchando, "cae al vacio" y es descartado.

Los programas que vienen para Ubuntu, la mayoria tienen muy alta confibialidad (ningun programa esta libre de errores, vulnerabilidades, pero exiten sin mala intencion de los programadores) asi que no es necesario estar paranoico viendo que entra a o que sale, solo busca una solucion cuando haya un problema, ocupate, no te pre-ocupes.

Ubuntu no solo es libertad, es paz.

---

### Post by vk-cdg on 2008-05-15
Mejor entonces. 
Dedico mi tiempo a tunera mi desktop. Jajajajaja

---

### Post by sergiom99 on 2008-05-15
hay algo equivalente al chkdsk para saber si un disco esta muriendo?

---

### Post by faktorqm on 2008-05-16
para ext3 ó 2 esta fsck. para otros tipos de particiones hay otras cosas. Salu2!

---

### Post by sergiom99 on 2008-05-16
gracias faktorqm.
cuando lo quiero correr me dice que no puedo hacerlo en un fs montado.
el problema es que lo estoy haciendo en un server remoto y sin posibilidad de rebootearlo.

como puedo checar el disco?

---

### Post by Hei Ku on 2008-05-16
> **sergiom99 said:**
> gracias faktorqm.
cuando lo quiero correr me dice que no puedo hacerlo en un fs montado.
el problema es que lo estoy haciendo en un server remoto y sin posibilidad de rebootearlo.

como puedo checar el disco?

podes tratar de desmontar solo esa particion. salvo que sea el / :lolflag:

---

