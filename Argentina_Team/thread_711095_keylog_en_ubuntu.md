---
title: "keylog en ubuntu?"
date: 2008-02-29
forum: Argentina Team
---

### Post by fedematic on 2008-02-29
Hola a todos. Me llamo Federico, soy de Buenos Aires y hace poco que me meti en el mundo linux.

Queria preguntar si me pueden recomendar algun keylog para ubuntu que funcione con teclados USB en lo posible.

Estoy casi seguro que me estan espiando la computadora en la oficina y quiero saber quien es. Me han desaparecido documentos importantes tanto del rigido como de gmail y misteriosamente me aparece el historial de firefox borrado.

Por favor si me pueden dar una mano con esto estaria muy agradecido.

Fede.

---

### Post by faktorqm on 2008-02-29
Hola! No entiendo exactamente cual es el problema, saben tus contraseñas? Te logueas a un dominio compartido? usas samba? 
Si cambias la contraseña de root y la de tu usuario, pones los documentos en el grupo de usuario root como propietario, sin permisos de lecturas para el resto de los usuarios y listo! _Aunque ahora que lo pienso un segundo, si es una empresa seguro no tenes la pass de root. D todas maneras la podrias "resetear" a una tuya y listo. Explayate mas sobre la situacion. Salu2!

---

### Post by User21 on 2008-02-29
No es mi intención ser un [trol]("http://es.wikipedia.org/wiki/Troll_%28Internet%29") ... lejos de todo eso, creo que este tipo de prácticas no son a las que apuntamos por aquí, en un foro de software libre, y mucho menos en uno donde respetamos tanto las libertades, como en Ubuntu. 
Mas allá de todo, lamentamos que hayas sido víctima de este tipo de acciones que violan la intimidad y privacidad, objetos tan preciados hoy en día, en un mundo lleno de tecnologías invasivas y siniestros personajes que abusan de la buena voluntad de los usuarios.

Quien tenga algo mas que agregar, por favor, no recurra al flamewar y PIENSE SERIAMENTE lo que tiene que decir. 
NO APOYAMOS ningún método de violación a la confidencialidad en Internet y en la informática en general...

SI: hay todo un mundo de discusiones acerca de esto, y cada quien tiene su postura. En resumen: no creo que este sea el lugar adecuado para solicitar este tipo de software.

**POR OTRO LADO: **lamento tener que recibirte de esta manera; no intento ni desalentarte ni nada por el estilo. Por el contrario, te doy la bienvenida al software libre y a su filosofía. Espero que esta comunidad supere tus espectativas y encuentres toda la ayuda necesaria. 
Una vez mas, disculpas a quienes vean esta respuesta y la consideren inadecuada.

---

### Post by odiseo77 on 2008-02-29
Lo que yo te sugeriría es que cambies la contraseña de usuario de ser posible (en caso de que no seas el administrador y no tengas la de root), y bloquees la sesión cada vez que te ausentes del ordenador (de esta manera, cuando alguien quiera usar la computadora, se le preguntará tu contraseña y no podrá usarla).

---

### Post by fedematic on 2008-02-29
Mi pc la usan varias personas, no solo yo. Tengo configurado ubuntu para que me logee automaticamente asi no tienen que andar poniendo el user y pass cuando la quieran usar.

El password de root lo se solo yo y en firefox no guardo ninguna contrasenia. La idea es que si precisan la pc para algo la puedan usar, pero no para revisarme las cosas! Siempre confie en la buena fe de la gente, pero ahora me han *****...

Tengo montadas 3 particiones con datos, dos ntfs que quedaron de viejos windows y una ext3.

Una solucion (que no se como hacer) seria que ubuntu no monte todas las particiones y que solo yo pueda dar la orden de hacerlo. O sea, tomarme el trabajo de cuando uso la pc, ejecutar algun script para montar en modo RW esas particiones.

Aun asi, precisaria algun soft que monitoree que hacen con mi pc cuando no estoy porque la unica manera de sacar datos es via internet. Tengo deshabilitados los puertos USB desde el setup y la pc no tiene grabadora de CD ni DVD. Seguramente habran reenviado mails y archivos a cuentas de mail o algo parecido.

Como accedieron a mi gmail no se, ya cambie la contrasenia... y quiero saber quien fue.

---

### Post by odiseo77 on 2008-02-29
Para lo de la configuración de las particiones, si puedes poner aquí el contenido del archivo /etc/fstab, te podríamos decir como hacer para que no se monten automáticamente (si no me equivoco, lo que tienes que hacer básicamente es agregar ***noauto*** a las opciones de montaje de estas particiones y no serán montadas durante el arranque).
Respecto a lo del software para monitorear la PC, la verdad no sé, porque nunca he tenido que usar uno (si buscas en synaptic quizás tengas un poco de suerte).

Saludos.

---

### Post by fedematic on 2008-02-29
Hola User21, entiendo tu punto.

Mi intencion no es espiar, aca me han jodido borrandome muchos dias de trabajo y si llegan a usar los documentos para pasarlos a la competencia, no solo perjudicaria a mi empleador sino que yo quedaria bastante mal.

Por lo menos quiero INTENTAR recuperarlo y saber quien esta usando mi pc malintencionadamente.

Pregunte por un keylog porque es lo unico que se me ocurre, pero si hay otro tipo de herramienta que haga algo parecido bienvenido sea. Ni siquiera me interesa saber contrasenias, solo ver la seguidilla de pasos y nombres de usuario a ver si puedo descubrir quien es.

Bloquear mi computadora a los demas NO es una opcion.

///

gracias odiseo, lo voy a probar cuando llegue.

---

### Post by faktorqm on 2008-02-29
yo creo que lo mas mas rapido que podes hacer asi mientras encontramos otra solucion es que veas esto:

[http://ubuntulife.wordpress.com/2007/05/28/truecrypt-proteger-carpetas-encriptando-el-contenido-en-linux/](http://ubuntulife.wordpress.com/2007/05/28/truecrypt-proteger-carpetas-encriptando-el-contenido-en-linux/)

esto a su vez tiene 2 grandes inconvenientes: !) si te olvidas la contraseña perdes todo 2) si borras los archivos de configuracion perdes todo. te lo aviso por las dudas.


aca usan los permisos para que nadie vea tus carpetas

[http://www.forosdelweb.com/f41/como-proteger-carpetas-debian-ubuntu-499445/](http://www.forosdelweb.com/f41/como-proteger-carpetas-debian-ubuntu-499445/)

(asegurate de hacer eso pero con el usuario root, para ver los archivos, sudo nautilus)

Espero que te haya servido. Salu2!

---

### Post by vk-cdg on 2008-02-29
> **fedematic said:**
> Hola User21, entiendo tu punto.

Mi intencion no es espiar, aca me han jodido borrandome muchos dias de trabajo y si llegan a usar los documentos para pasarlos a la competencia, no solo perjudicaria a mi empleador sino que yo quedaria bastante mal.

Por lo menos quiero INTENTAR recuperarlo y saber quien esta usando mi pc malintencionadamente.

Pregunte por un keylog porque es lo unico que se me ocurre, pero si hay otro tipo de herramienta que haga algo parecido bienvenido sea. Ni siquiera me interesa saber contrasenias, solo ver la seguidilla de pasos y nombres de usuario a ver si puedo descubrir quien es.

Bloquear mi computadora a los demas NO es una opcion.

///

gracias odiseo, lo voy a probar cuando llegue.

Creo que nadie dice que debas bloquear tu equipo, pero si aprovechar la posibilidad que te da Ubuntu de hacer mas de un perfil de usuario. Cada usuario se loguea al equipo con un perfil diferente y no tiene por que saber las contraseñas de los demás. 
En mi casa lo tengo así, un perfil para cada usuario. 
Los documentos están alojados dentro del perfil de cada usuario y con los correspondientes permisos, cada uno solo puede ver lo suyo, sin poder hacer nada con lo de los demás.

---

### Post by Tosh78 on 2008-02-29
Hola! La verdad es que te entiendo perfectamente porque tambien en el trabajo me pasaron cosas similares y es muy frustrante sentir la impotencia que eso te genera.
User-21 estoy completamente de acuerdo con vos y quedate tranquilo que tu mensaje no sono para nada mal. Por suerte te expresaste muy bien y no hay dudas de tu buena intencion.
Con respecto al problema de seguridad...quizas podes pensar en alguna solucion alternativa, como por ejemplo que el amsn o el pidgin guarden el ultimo usuario que se loggeo. Otra que podes hacer es llamar por telefono a la oficina cuando no estas, o volver antes de lo que dijiste, o dejar un documento falso en el escitorio...
Espero que puedas resolver esto de alguna forma.

---

### Post by AnRa on 2008-02-29
Creo que lo mejor sería crear un usuario "invitado" que tenga privilegios reducidos y listo.

---

### Post by Thalskarth on 2008-02-29
> **vk-cdg said:**
> Creo que nadie dice que debas bloquear tu equipo, pero si aprovechar la posibilidad que te da Ubuntu de hacer mas de un perfil de usuario. Cada usuario se loguea al equipo con un perfil diferente y no tiene por que saber las contraseñas de los demás. 
En mi casa lo tengo así, un perfil para cada usuario. 
Los documentos están alojados dentro del perfil de cada usuario y con los correspondientes permisos, cada uno solo puede ver lo suyo, sin poder hacer nada con lo de los demás.

me parece que esta puede ser una de las soluciones mas sencillas para tu caso...

o sea, create un nuevo usuario digamosle "Pepe". y que cuando la maquina enciende, carge directamente al usuario "pepe" que es el perfil publico que cualquiera puede tocar en tu PC. (Hay no pones nada importante)... y a tu user actual (o uno nuevo), le cambias la contraseña...

Y configuras que "Pepe" no tenga accseso a tu home por ejemplo (es decir, donde estan tus documentos y etc.). Entonces, a lo sumo, cada vez que vos uses la maquina, tenes que cerrar session "pepe" y logearte con tu usuario. Y al termianr, volver a pepe... asi cualquiera puede usar la PC... pero tus cosas no son accsesibles

incluso, jugando con los permisos... poder prohibirle a "pepe" hacer varias cosas, o ejecutar algunos programas... setearle carpetas no lejibles o no escribibles... etc etc etc

---

### Post by leo_rockway on 2008-02-29
Ni siquiera tendria que desloguear a pepe, solo loguear su usuario y bloquearlo cuando se va... eso es lo que hago yo con kde al menos.

---

