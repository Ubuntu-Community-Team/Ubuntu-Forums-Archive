---
title: "Ayuda !! Requerimientos Ubuntu 7.10"
date: 2007-11-04
forum: Argentina Team
---

### Post by leonardo83 on 2007-11-04
Que tal gente! tengo una consulta.
Hace pocos dias me llego el cd de ubuntu 7.04 y lo probe en live cd: de mas esta decir que me atrapo por completo y estuve a punto de instalarlo, pero en el tiempo que esperaba me llegue el cd salio el 7.10 (que tambien pedi). :)
Probe el live cd de 7.04 y funciona ok, se ve bien y a pesar de que no lo instale todavia es un caño. Pero un amigo me grabo el cd del 7.10 y el problema es que NO se ve bien, la pantalla me aparece como doblada y no se ve la barra superior del menu, cosa que no pasaba con feisty fawn. Verifique si el cd tenia errores y me dio negativo.Mi consulta es si el problema es mi pc que no es adecuada para el nuevo ubuntu.
Paso a comentar, mi pc es algo viejita, pentium 3 con 640 de ram, disco de 60gb, 750 mhz , donde ahora funciona el win ME (si ya se, no pienso pasar a xp !!).
Por favor diganme donde podria estar el inconveniente, aunque en todo caso deberia probarlo con el cd original del 7.10, que llegara con suerte dentro de 3 semanas... :confused:
Saludos!!

---

### Post by The_NewBye on 2007-11-04
Requerimientos del Sistema

Ubuntu está disponible para arquitecturas PC, 64-Bit y Mac. El CD requiere por lo memos 256 MB of RAM. La instalación requiere por lo menos 2 GB de espacio en disco.

Fuente: [http://ubuntu-ar.org/ubuntu/queesubuntu/edicionescritorio]("http://ubuntu-ar.org/ubuntu/queesubuntu/edicionescritorio")

---

### Post by margori on 2007-11-04
Leonardo:

Por los requerimientos de sistema, la verdad estas sobrado de cariñio. Estoy seguro que el problema va por el asunto de controladores o configuración.

Ubuntu 7.10 viene por defecto con Compiz-Fusion habilitado. Compiz es una paquete que usa OpenGL para darles efecto re-bonitos al escritorio. Pero claro que para que eso sea posible necesita claro esta una placa aceleradora de videa 3D y que los driver de video estan correctamente instalados.

Hasta la fecha, existe buen soporte para NVidia (Yo uso una de esas placas) y recientemente se han creado los controladores para ATI.

Por favor comentanos cual es tu placa de video, que configuracion utilizas, etc. etc. Tiranos mas datos.

---

### Post by por100pre1 on 2007-11-04
En **Sistema> Administración> Pantallas y gráficos** prueba elegir tu tarjeta gráfica manualmente. Muchos problemas han sido causados porque en Gutsy el sistema elige el controlador erroneo.

---

### Post by leonardo83 on 2007-11-04
antes que nada gracias por todos los aportes!!!
Es verdad, voy a probar viendo eso de la configuracion.
Me olvide decirles que tengo una placa 3d .....sniper2 Riva tnt2 M64 ja ja con soporte nVidia obviamente.
Configuracion ? mmmmmmh no se, en windows la detecto de una, lo puedo configurar desde el cd o tengo que poner el cd de la placa? :confused:
Voy a ver con el live cd viendo esa configuracion y les aviso que resultado tuvo, pero igualmente espero sea un problema del cd en todo caso.
Saludos! :guitar:

---

### Post by Moonlit Knight on 2007-11-05
A mi me pasó lo mismo, es una cuestión de configuración de la resolución de la pantalla, que no viene bien por defecto, fijate cuando te aparece el menú que dice "start or install ubuntu", apretá F4 y elegí la resolución que soporte tu monitor, 

Cuando inicies si el problema persiste, fijate de tirar el mouse lo más para arriba posible, cosa de que le des clicks a los menús y puedas acceder a **sistema - administración - pantallas** y gráficos y ahí configuralo para que se vea bien. 

Quedate tranquilo que no es una cuestión de requerimientos. Ojalá te sirva.

Saludos

---

