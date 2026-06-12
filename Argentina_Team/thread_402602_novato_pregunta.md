---
title: "novato pregunta"
date: 2007-04-05
forum: Argentina Team
---

### Post by yoelnacho on 2007-04-05
Hola me llamo Ignacio;  siempre me gustó el tema de explorar linux, y desde que encontré esta última versión de Ubuntu (no ta chocante, debido a su entorno gráfico), decidí intentar utilizarlo.
Puede instalarlo en un disco de 6 Gb, y ahora me encuentro con que no sé como configurarlo para poder navegar por internet. No sé si se crea un acceso a la conexión de internet como en windows, o si es distinto. 
la placa de red que uso es una Via Rhine III, conectada a un router mediante una ip fija (192.168.xxx.xxx). Y el proveedor es fibertel.
Espero que alguien me diga cómo puedo configurar la placa para poder navegar, ya que las respuestas que encontré están en ingles, o son muy complicada para mi ignorancia en cuanto a linux.-
Si dentro de éste foro hay una sesión para novatos, por favor muevan este post ahí.
Gracias por su tiempo.-

---

### Post by DuckMan on 2007-04-06
supongo q el modem es cable modem y tenes internet todo el tiempo sin necesidad de conectarte.. o tenes q marcar algun numero?

por la primera opcion, me extraña q no tengas internet automaticamente.. pero deberias ir a Sistema / Administracion / Red y configurarla como dhcp para que tome automaticamente la ip ..

si va por otro lado, deja mas informacion

PD: las tags son para describir el problema, "recien empiezo" no dice nada del problema, podrias poner algo como "problema conexion internet" o algo asi

---

### Post by yoelnacho on 2007-04-07
Si es un cable modem. Cambié la configuración de la placa de red a dhcp, reinicié, pero sigo sin conseguir conectarme. 
Abro firefox, pero no navega.
Que otra solución puedo encontrar?
Saludos.-

---

### Post by beuno on 2007-04-07
> **yoelnacho said:**
> Si es un cable modem. Cambié la configuración de la placa de red a dhcp, reinicié, pero sigo sin conseguir conectarme. 
Abro firefox, pero no navega.
Que otra solución puedo encontrar?
Saludos.-

Quizas tu router no este dandote los DNS adecuados.

Proba poner como DNS:

200.49.156.3
200.49.156.4

---

### Post by DuckMan on 2007-04-07
hace poco me paso cuando toq el cableado de mi red, fijate lo q dice beuno o entra a tu router y fijate los datos q te tira

---

### Post by yoelnacho on 2007-06-02
Gracias amigos, por las respuestas.
Logr´e ingresar a mi router desde el navegador, y todo lo solucion´e simplemente buscando los DNS correctos que delegaba,.. y listo.... funcionando internet en ubuntu!.-
Gracias por todo

---

### Post by undiaperfecto on 2007-06-03
que te dieron el modem webstar ese feo?

---

### Post by yoelnacho on 2007-06-03
La verdad que el modem no era el problema, porque cuando lo ponía directo a la placa de red y daba un DHCP, "navegaba", pero al pasar la conexión por el router, "no".
Cambié los DNS y todo ok.
Ah, aclaro que todo se me dío porque probé una versión de ubuntu que se instala desde windows, sin necesidad de hacer una partición. (para empezar está bien para mí)
dejo el enlace por si a alguien le interesa probar [clicki]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html") 
Saludos.-

---

### Post by undiaperfecto on 2007-06-03
yo tengo un problema parecido, pero tampoco es el modem, la historia la tengo con el router wifi, ya me volvi loco asi que lo sigo usando via cable. el mundo wifi es todavia muy complicado para mi

---

### Post by fetova on 2007-06-04
> **undiaperfecto said:**
> yo tengo un problema parecido, pero tampoco es el modem, la historia la tengo con el router wifi, ya me volvi loco asi que lo sigo usando via cable. el mundo wifi es todavia muy complicado para mi

Proba leer esto: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) tal vez te de algo nuevo y ya halles :), ademas, el network manager funciona muy bien para la seleccion de redes inalambricas

Saludos!

---

