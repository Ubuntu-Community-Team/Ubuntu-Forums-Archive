---
title: "Desorden en el panel y ..."
date: 2007-03-20
forum: Argentina Team
---

### Post by valucha on 2007-03-20
[COLOR="DarkOrchid"]Antes que nada, hola, saludos a todos soy nueva acá y con Ubuntu.

El tema es así, tengo Ubuntu Edgy  (con una mother soyo y la compu comprada en compumundo :p) con varios síntomas:

1) Me pasa que cuando entro en mi cuenta, ingreso la clave, se abre la pantalla y cuando se está cargando todo se tilda, se pone todo negro y me vuelve a pedir la clave, así mil veces. Cuando entro en modo a prueba de fallas me dice que hay un problema con la personalización y bla bla bla... Pero eso lo solucioné ya que me dijeron que capaz era porque yo "personalizaba" mientras  bajaba las actualizaciones...  Y dejó de pasarme, igualmente ahora, a pesar de haberlo instalado cmo me indicaron, me pasó una vez.

2) Cada vez que inicio el panel de "aplicacones, lugares, sistemas, etc"... donde además tengo el firefox, thunderbird, gaim y mi carpeta personal, me aparece desordenado... los iconos en cualquier lado, la hora y la fecha aveces me aparece en el medio, y encima aveces hay íconos que ni aparecen.

3)Aveces está funcionando todo perfecto, y cuando quiero apagar la compu y aprieto el ícono de salida no me da bola... Por más que clikee no me aparece nada.

Eso es todo... busqué en google y no encontré nada. 

[/COLOR]

---

### Post by DuckMan on 2007-03-20
1) sudo dpkg-reconfiguire xserver-xorg, quizás te ayude!
2) fijate si no se estan moviendo los plugins de lugar, clic derecho mover para ponerlos en su lugar, tambien podes "trabarlos" en el lugar con clic derecho // bloquear
3) eso a veces pasa xD muuy de vez en cuando creo, proba apretando ctrl + alt + backspace (tecla para borrar) , se va a reiniciar el gestor grafico en unos segundos y vas a poder apagar desde la pantalla de login

4) ya por ser mujer y tener ubuntu, tenes a cualquier pibe de este foro a tus pies, usalo con responsabilidad


bienvenida!

---

### Post by beuno on 2007-03-20
Me suena a problemas de permisos...

Te diria que pruebes crearte un usuario nuevo, y entres con ese.

---

### Post by valucha on 2007-03-20
[COLOR="DarkOrchid"]el 2) no los tenía bloqueados al panel, me había olvidado de volverlos a bloquear cuando los reorganicé :) jajaja... capas es eso...

Sobre el 1) :
en la 1era pantalla aparece un selector de "x server driver" y mirá que es de muy ignorante lo que te voy a decir, seguro me mando cualquiera. Pero en Windows recuerdo que mi placa usaba uno llamado "proSavageDDR" o algo así, y leyendo vi que hay uno que se llama "savage" puede ser ese?... 
Jajaja realmete no sé que elegir en lo que me mandaste a abrir, recién empiezo con esto :$.. 

bueno, espero la respuest,a y gracias por la bienvenida :)[/COLOR]

---

### Post by valucha on 2007-03-20
> **beuno said:**
> Me suena a problemas de permisos...

Te diria que pruebes crearte un usuario nuevo, y entres con ese.

[COLOR="DarkOrchid"]Ahi entra perfectamente...[/COLOR]

---

### Post by beuno on 2007-03-20
> **valucha said:**
> [COLOR="DarkOrchid"]Ahi entra perfectamente...[/COLOR]

Me alegro.
Ahora lo unico que te quedaria es copiar lo que quieras del otro usuario, y borrarlo (si queres, por una cuestion de orden nada mas).

---

### Post by valucha on 2007-03-20
> **beuno said:**
> Me alegro.
Ahora lo unico que te quedaria es copiar lo que quieras del otro usuario, y borrarlo (si queres, por una cuestion de orden nada mas).
[COLOR="DarkOrchid"]
Perooo.. el tema es que necesito tener otro usuario... por mis papás... Les juro que si los meto en mi escritorio no entienden nada.. Cuál es el problema?... osea, me mandé una cagada al crear la orta cuenta o qué :S?[/COLOR]

---

### Post by beuno on 2007-03-20
> **valucha said:**
> [COLOR="DarkOrchid"]
Perooo.. el tema es que necesito tener otro usuario... por mis papás... Les juro que si los meto en mi escritorio no entienden nada.. Cuál es el problema?... osea, me mandé una cagada al crear la orta cuenta o qué :S?[/COLOR]

Para nada, crea todos los usuarios que quieras.
Yo decia que borraras el usuario que no funcionaba.

---

### Post by DuckMan on 2007-03-20
aja, como dice beuno, borra ese q seguramente salio mal del parto (?)

y despues create todos los q quieras..

de acuerdo a lo del Savage, depende q placa tengas, si nos das mas informacion podemos ayudarte

igual lo mas facil y practico es lo de beuno

espero q te sea leve el camino ubuntero!

---

### Post by jpmorelli on 2007-03-21
Cuidado con borrar el primer usuario que uno crea al instalar que despues hay que setearle todos los permisos para poder hacer sudo y demás, que por lo menos para mi no son muy fáciles, aunque bueno, a veces se cosas tan complicadas y otras parece que recién puse Linux en la máquina. :lolflag:

---

### Post by lavaramano on 2007-03-22
para crear el usuario y que no pierdas nada (eh permisos y gilada de sudo) lo haces con 'sudo adduser USUARIO admin'
el admin despues de USUARIO es el grupo donde va a ir a parar, el cual es ni mas ni menos que "admin", en ese grupo todos pueden sudear(?) (cualqueir cosa, 'sudo cat /etc/sudoers' y ahi van a ver, carajo(?)).
  
ahora si ya agregaste al usuario y queres meterlo dentro del grupo "admin", hay que hacer lo siguiente.

> 
sudo nano /etc/group


ahi te va a aparecer eh.. justamente el archivo group que contiene a los usuarios dentro de los grupos.

si leiste al archivo /etc/sudoers vas a ver que todos los usuarios del grupo "admin" pueden sudear(?), entonces, agregas al usuario nuevo al grupo admin, el cual deberia quedarte masomenos asi:
> 
admin: x :666:usuario_actual,usuario_nuevo


notas: 
* la x entre " : " es sin espacio, pero aca los tuve que poenr porque sino me clavaba un emoticon....
* el 666 es el gid del grupo "admin" y puede variar.
* lo que se hizo fue agregar al usuario nuevo, DESPUES de agregar una coma.


me explique como el orto, pero bueno.
cualquier cosa, man *problema* ...  que no hace mal (?).

---

### Post by konstantin88 on 2007-04-24
Hola! yo publiqué ayer un tema nuevo porque no puedo acceder como sudo, por lo que no puedo realizar ninguna tarea administrativa, ni actualizar, ni instalar programas. Quizá ustedes sepan que puedo hacer. 
 Jmorelli dijo "Cuidado con borrar el primer usuario que uno crea al instalar que despues hay que setearle todos los permisos para poder hacer sudo y demás, que por lo menos para mi no son muy fáciles, aunque bueno, a veces se cosas tan complicadas y otras parece que recién puse Linux en la máquina.". Creo que mi caso es parecido, saben que es lo que tengo que hacer para volver a ponerle a mi cuenta los permisos de sudo?
 Gracias

---

### Post by konstantin88 on 2007-04-24
Ah, el tema es [http://ubuntuforums.org/showthread.php?p=2527314&posted=1#post2527314](http://ubuntuforums.org/showthread.php?p=2527314&posted=1#post2527314)
Mirenlo antes de responder para descartar los consejos que ahí me dieron.

---

