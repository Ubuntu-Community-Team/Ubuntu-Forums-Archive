---
title: "[Ayuda] Ubuntu 8.04 y Wine, combinacion explosiva :S"
date: 2008-05-01
forum: Argentina Team
---

### Post by smrdelj on 2008-05-01
Hola q tal, ya me estoy haciendo popular y pesado por aca :$..

La cuestión es que el Ubu Hardy 8.04 me ta volviendo loco a la hora de ejecutar aplicaciones via Wine.

Para empezar, aclaro que actualicé repositorios tal cual dice la web oficial de wine ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)).
Por ende, el wine q tengo instalado es la ultima version.

Lo que yo quiero jugar es Counter-Strike. Como sé que la convivencia Linux - sXe Injected es imposible (al menos por wine), me encapriché con hacer correr Steam (ya q tengo licencia oficial para jugar Cs, asi q al no necesitar ningun antichit ajeno al VAC podria jugar en servidores Steam).

Al ejecutar el instalador SteamInstall.msi, va todo bien. Logro instalarlo perfectamente. El problema está en las instancias siguientes. 
Siguiendo cualquier guia en internet, se puede apreciar que, en lenguaje burdo y poco tecnico, Steam "corre por HTML". En pocas palabras, para correr Steam necesito el Gecko.
Y aca está el problema (como planteo en mi otro thread). Llegada la hora de la verdad, cuando Wine debería proponerme instalar Gecko, se cierra. Es decir que Wine, al parecer, funciona mal o no tiene aun compatibilidad Gecko con Ubu 8.04, porq no solo no me ofrece oportunamente instalar Gecko, sino que ademas directamente se me cierra la aplicación que requiere su uso (en este caso, Steam).
Por otro lado, he leido que puede instalarse Gecko por consola tipeando "wine iexplore http://winehq.org"; pero eso tampoco me resulta. Acto seguido a ejecutar el comando, se me despliega una ventana titulada "Wine Internet Explorer" que dice "El renderizado HTML está actualmente deshabilitado" en un fondo blanco.

Cansado de este ida y vuelta, decidí probar con otra aplicacion que encontré en la web, el Wine-Doors (y fue de hecho una muy mala idea, bah al menos me dejó aun más confundido).
Al instalar este programa, le indiqué que instale Steam, Gecko, IE 6, Mozilla 2...en fin, todo lo q me parecía vinculado al problema. Los resultados fueron muy extraños:

1) Por un lado, Steam sigue desvaneciendose en la misma instancia q antes, con la diferencia que de a ratos aparece, para luego (en cuestion de segundos) volver a desaparecer. Es decir que Steam, cuando intento logearme a mi cuenta, se borra y ni pelota. Pero al ratito aparece y se despliega, y a los pocos segundos de hecharle mano para hacer cualquier cosa (como por ejemplo simplemente dirigirme a la solapa "Games"), se cierra y vuelve a desaparecer. Incluso en un tiempito vuelve a aparecer y se repite lo mismo una y otra vez.

2) Al hacerle click a cualquiera de las Aplicaciones q instalo via Wine-Doors, no sucede nada. No me refiero a accesos directos, sino a los enlaces que genera en los grupos o categorias del menu Aplicaciones de la barra GNOME. Simplemente no se inmuta ante la orden de ejecutar el programa supuestamente instalado.

3) No puedo desinstalar el Wine-Doors. Probé con "sudo apt-get remove Wine-Doors" y, tras decirme q lo desinstaló satisfactoriamente, el conchudo sigue ahi.

4) Al ejecutar "wine iexplore http://winehq.org", en vez de decirme lo q antes conté, me salta esto: ```

preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:module:import_dll Library shdocvw.dll (which is needed by L"C:\\windows\\system32\\iexplore.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\iexplore.exe" failed, status c0000135

```

Por otro lado, tambien tengo el Wine (original) instalado, coexistiendo con el Wine-Doors. A su vez, tengo Steam supuestamente instalado via ambos programas (aunque, como explico, el Steam q corresponde al Wine-Doors no responde ante la ejecucion -aunque, en realidad, no tengo idea cual de ambos Steams es el q aparece y desaparece como expliqué-). No solo eso, sino q tambien tengo otra peculiaridad q destacar: no sé porqué, aunque desinstale el Wine, su carpeta sigue apareciendo en el menu Aplicaciones. A su vez, si desinstalo el Steam de Wine, sigue apareciendo en Aplicaciones > Wine > Programas.
En cuanto al Wine-Doors y las aplicaciones q instalé via él, no tengo idea como desinstalarlas, ejecutarlas ni nada.

La verdad que es todo un quilombo, ya no sé que hacer. Me parece q es todo producto de muchas incompatibilidades juntas.
Supongo que el Wine actual (0.9.60) no está del todo preparado para correr en Ubu 8.04 (al menos el Gecko no camina); y mucho menos el Wine-Doors (aunque, curiosamente, luego de instalarlo el Steam empezó al menos a asomarse cada rato).

Alguien me puede ayudar con esto? (si es q existe ser humano q se haya tomado la molestia de leer todo y tenga ahora la paciencia suficiente como para darme una mano)

Muchas gracias, mataría que me ayuden :D

Saludos, disculpen las molestias y la falta de precision o tecnisismo a la hora de expresarme. Seguro hubiera sido todo mas corto y sencillo de explicar si no fuera por ello.

Gracias, espero con ansias alguna idea.

Saludos

---

### Post by marianom on 2008-05-01
Por las dudas no encuentres la respuesta que necesitás en este subforo (pese a que tenemos varios gamers) es conveniente saber que existe un foro de games en ubuntuforums al cual podes recurrir en caso de necesidad (aunque es preciso que escribas todo el post en inglés).

Si podes cumplir esa condición, seguro que allá tendrás respuesta. Esperemos, sin embargo, que primero llegue la respuesta por este subforo. ¡Suerte!

---

### Post by MeduZa on 2008-05-01
te esta faltando ese dll, como lo dije antes, instala el wine doors y metele todo paquete que te faltes, sobre todo IE y las runtime library.

Saludos

---

### Post by faktorqm on 2008-05-01
doble post, cierren este o fusionenlo con el anterior. 
post con lo mismo: [http://ubuntuforums.org/showthread.php?t=774224](http://ubuntuforums.org/showthread.php?t=774224)
Salu2!

---

### Post by smrdelj on 2008-05-01
Naahh, esto no es doble thread. Acá el topic central, si bien está conectado con Gecko, reposa en otra cosa. Acá planteo una situacion mucho mas compleja, que involucra, más que nada, la convivencia complicada entre Ubuntu 8.04; Wine; Wine-Doors; Gecko y los programas de windows (q ya no sé por donde encararla). También se tocan posibles problemas de configuración...en fin, lo q yo acá planteo es algo más complejo q instalar Gecko (q, por cierto, al parecer pude lograrlo -dejé en mi otro thread lo que hice-).

marianom, ya estoy tratando el tema con la gente del foro de Wine, a ver si me dan una mano con este quilombo. Vos me recomendas otro foro especifico?

Veremos si de alguno de los dos foros puedo rescatar algooo. Muchas gracias.

Saludos

---

### Post by MeduZa on 2008-05-03
segun lo que yo leo en el mensaje que error como te dije te falta una dll
shdocvw.dll which is needed by... yo que vos copio desde un box windowsxp  shdocvw.dll a la carperta ~/.wine/drive_c/windows y pruevo que pasa.

si te sigue haciendo drama ahi ya no se que hacer.

---

