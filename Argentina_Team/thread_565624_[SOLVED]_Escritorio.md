---
title: "[SOLVED] Escritorio"
date: 2007-10-02
forum: Argentina Team
---

### Post by Vero1 on 2007-10-02
Hola,

Debido a que formateé y reinstalé Ubuntu, ahora me resulta imposible conectarme a Internet, haga lo que haga.

La pregunta es: Se puede instalar kde en lugar de gnome(que tengo ahora). Lo pregunto porque en kde se puede configurar mas fácilmente Internet.

El problema está en que en los repositorios no está y al no poder conectarme no puedo actualizar...

Bueno pero antes que nada hay que saber si se puede o no:)

Espero que alguien me oriente.

Gracias.

---

### Post by santiagoward2000 on 2007-10-02
Hola Vero,
Se puede si instalás el paquete kubuntu-desktop. Lo que no sé es cómo vas a hacerlo si no tenes internet...:confused:

---

### Post by Vero1 on 2007-10-02
Hola,

Justamente ése es mi problema. Si tuviera Internet no necesito descargar kde pero no hay manera.

Gracias por tu información:)

---

### Post by santiagoward2000 on 2007-10-02
Hola,
Una pregunta Vero, ¿cómo es la conexión? Tal vez te pueda ayudar a configurarla.

---

### Post by Pse on 2007-10-02
¿Configurar más fácilmente Inet? Uhm...qué problema tenés? Ta todo manejado por el networkmanager, y en kubuntu ocurre lo mismo. Si querés hacer una configuración manual no soportada por el networkmanager (raro) te recomiendo que te fijes en el wiki.

---

### Post by Vero1 on 2007-10-02
> **santiagoward2000 said:**
> Hola,
Una pregunta Vero, ¿cómo es la conexión? Tal vez te pueda ayudar a configurarla.

santiagoward2000,

Tengo conexión DSL por Speedy.
Cuando corro pppoeconf me dice que no encuentra el concentrador de acceso del proveedor.
En Win no tengo ningun problema.

Ya me pasó ésto la primera vez que instalé Ubuntu pero despues borré un host que estaba de más y funcionó. Ahora no hay modo.

Gracias.

---

### Post by Vero1 on 2007-10-02
> **Pse said:**
> ¿Configurar más fácilmente Inet? Uhm...qué problema tenés? Ta todo manejado por el networkmanager, y en kubuntu ocurre lo mismo. Si querés hacer una configuración manual no soportada por el networkmanager (raro) te recomiendo que te fijes en el wiki.


Hola Pse,

Sé que hay algun problema de configuración pero no logro encontrar cuál es. Ya usé el network manager tambien. No hay modo.

gracias

---

### Post by santiagoward2000 on 2007-10-02
Ahh, disculpá Vero1, pero yo no sé cuál será el problema :( . Ojalá alguien pueda explicartelo...

---

### Post by Vero1 on 2007-10-02
> **santiagoward2000 said:**
> Ahh, disculpá Vero1, pero yo no sé cuál será el problema :( . Ojalá alguien pueda explicartelo...


No te preocupes y gracias igual. Vale la intención.

saludos

---

### Post by marianom on 2007-10-02
Vero1: por favor, intentá responder a todos en un solo post. Facilita mucho la lectura de quienes están siguiendo tu problema y te pueden ayudar.

Gracias.

---

### Post by JoACoV on 2007-10-02
seguro que activaste bien el firmware del modem?

a lo mejor es eso... que tengas el driver pero te hayas olvidado de activarlo, fijate

---

### Post by LaHire on 2007-10-02
Ahhh...Speedy y los modems malditos....


Bueno, podés conseguirte un cd de Kubuntu (podes bajarlo de [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php))

O realmente te convendría volver a renegar con Gnome

que macana que comiences así...no te debe gustar para nada :(

Fijate si esto te puede servir...

[http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810](http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810)

o

[http://ubuntu-ar.org/soporte/comos/modemzyxel](http://ubuntu-ar.org/soporte/comos/modemzyxel)

Espero que se solucione....espero ayudar en lo que pueda :)


No te enojes con Ubuntu!, enojate con Speedy :P

un saludo!

---

### Post by Vero1 on 2007-10-03
Hola LaHire y a todos los amigos que me han contestado.

Les escribo desde Ubuntu, SIIIIIIIIIIIIIIIIIIIIIIIIIIIIIII:)

Todo el sufrimiento se debió a que no reconocía el dominio. Al cambiarlo y configurar la conexión tal como está en Win, lo solucioné.

Muchas gracias a todos:popcorn:

saludos

---

### Post by nest on 2007-10-03
¿Por qué no explicás cómo lo solucionaste para que quede acentado y asi otras personas con este problema puedan también arreglarlo simplemente buscando en el foro? ;)

---

### Post by Vero1 on 2007-10-03
Bueno, probé de todas las maneras posibles que te puedas imaginar.

Al final fuí a Windows, me fijé en la Configuracion LAN y lo repetí en la configuración de Red de Ubuntu.

Aparte, como lo dije antes, estaba mal el nombre del equipo en Configuración de Anfitriones en Red de Ubuntu.  Tambien  lo cambié por lo que corresponde.

Ésto es todo lo que recuerdo, porque ya te digo, estuve muchas horas tratando una cosa y otra, yendo de Ubuntu a Win y viceversa...

En resumen: la configuración de Red de Ubuntu debe coincidir con el LAN de Windows y el Servidor tambien debe coincidir con Windows.

Una vez que coincide todo, corro pppoeconf para que haga los cambios necesarios.

Espero no haber olvidado nada:)

saludos

---

### Post by LaHire on 2007-10-03
> **Vero1 said:**
> Bueno, probé de todas las maneras posibles que te puedas imaginar.

Al final fuí a Windows, me fijé en la Configuracion LAN y lo repetí en la configuración de Red de Ubuntu.

Aparte, como lo dije antes, estaba mal el nombre del equipo en Configuración de Anfitriones en Red de Ubuntu.  Tambien  lo cambié por lo que corresponde.

Ésto es todo lo que recuerdo, porque ya te digo, estuve muchas horas tratando una cosa y otra, yendo de Ubuntu a Win y viceversa...

En resumen: la configuración de Red de Ubuntu debe coincidir con el LAN de Windows y el Servidor tambien debe coincidir con Windows.

Una vez que coincide todo, corro pppoeconf para que haga los cambios necesarios.

Espero no haber olvidado nada:)

saludos


¿Puede ser que tengas un modem ethernet? 

Los modems ethernet son los que se conectan por RED (con una ficha RJ45, como las del teléfono pero más gordita)

si fuera por eso...bueno, por si las dudas te digo que esos modems no tiene (casi :lolflag:)ningún problema  con Linux (generalmente todas las últimas distribuciónes) vienen con soporte para ellos...y lo único que hay que configurar en sí es...bueno, justamente la configuración de la red Y la configuración del router (que generalmente se hace vía web ingresando la dirección IP en el Firefox o algún explorador afín)

y Si no es un modem por red (o sea, usa una conección usb....te envidio, nunca lo vi solucionado tan fácil :P

---

### Post by Vero1 on 2007-10-03
LaHire, tengo Ethernet o sea no es USB, por lo tanto no tenés nada que envidiar eh:lolflag:

De todas formas me ha costado un perú, pero ya está.

La otra vez me fue imposible ingresar al módem, pero por suerte no hace falta.

Ahora, ya que estamos, trato de enviar un e-mail con un adjunto (es un especie de clip) pero no hay manera de que lo envíe. Si mando texto envía sin problemas.

Tenés idea del por qué?

---

### Post by LaHire on 2007-10-03
> **Vero1 said:**
> LaHire, tengo Ethernet o sea no es USB, por lo tanto no tenés nada que envidiar eh:lolflag:

De todas formas me ha costado un perú, pero ya está.

La otra vez me fue imposible ingresar al módem, pero por suerte no hace falta.

Ahora, ya que estamos, trato de enviar un e-mail con un adjunto (es un especie de clip) pero no hay manera de que lo envíe. Si mando texto envía sin problemas.

Tenés idea del por qué?

Bueno, puede ser por muchas cosas...

Que usas para mandar los mails? evolution? thunderbird?

El archivo adjunto es *mandable*? (o sea, si es una imagen debería mandarlo, si es un ejecutable no)

pasa con todos los remitentes? o solo con uno?

---

### Post by Vero1 on 2007-10-03
Disculpá no aclaré que es Evolution.
No es un exe, es un videoclip o película.

Ubuntu lo uso yo sola.

---

### Post by LaHire on 2007-10-03
> **Vero1 said:**
> Disculpá no aclaré que es Evolution.
No es un exe, es un videoclip o película.

Ubuntu lo uso yo sola.

No será que es demasiado grande para tu casilla?
Por ejemplo, si bien Gmail tiene....casi 3Gb de almacenamiento, tiene un máximo de ~10mb en archivos adjuntos por mail.... Hotmail tiene menos, creo

Son números fríos, claro, pero ese también puede ser un factor :)

Y perdón, no fuí claro con mi pregunta :), me refería que si el mail fallaba solamente cuando lo enviabas a N cuenta, o si el mai falla con cualquier destinatario.

Te preguntaba eso porq puede ser que el/los propietario/s de esa cuenta tengan:

[LIST]
[*]Su Casilla llena y no te deja enviar archivos más grandes de x MB
[*]Algún tipo de firewall/iptables activado que rebote toda esa clase de cosas
[*]o que Vos tengas un firewall/iptables activado y programado para rebotar mensajes con archivos adjuntos, lo cual es extraño, porque nada de eso se activa sin que vos lo especifiques explícitamente...y (Ubuntu al menos) no tiende a molestarte en esos asuntos.[/LIST]Provaste mandar otra cosa como archivo adjunto? (alguna imagen o algo?): si probás hacer eso, y funciona, quiere decir que es un problema del archivo (porq es muy grande) o de tu proveedor de correo o del proveeedor de correo de el destinatario
¿Comprimiendo el archivo?(me refiero, comprimirlo en un .rar, por ejemplo): con esto podés "zafar" de que el archivo sea demasiado grande..


espero que se solucione! y espero ayudar, por cierto  :)

---

### Post by Vero1 on 2007-10-04
Hola LaHire,

Es muy posible que sea por el tamaño del archivo que Evolution no quiere enviarlo. Es una lastima porque es muy cómica la película.

El mail falla si lo mando a cualquiera.

Bueno, no sé si vale la pena comprimirla porque algunos destinatarios ni saben lo que es compresión y tal vez ni tengan programas para descomprimir. 

No importa, solamente me llamó la atención.

LaHire por qué no visitas ubuntu-es?  Digo, si te interesa. Hay muchos argentinos allí.

Gracias por tu atención a mis problemas:)

saludos

---

