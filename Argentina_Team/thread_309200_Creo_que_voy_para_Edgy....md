---
title: "Creo que voy para Edgy..."
date: 2006-11-29
forum: Argentina Team
---

### Post by marianom on 2006-11-29
Muchachos,
 tiré la pregunta en otro foro pero la repito aca a ver si alguien tiene consejos extras:

estando en dapper la verdad es que tengo varios problemas con Alsa, por trabajo necesito tener Skype funcionando y no dura ni 5 minutos abierto que me da error de segmentacion y se cierra. 
Investigué y me dijeron que la solución es upgradear alsa (en dapper es 0.10 cuando la versión estable actual es 0.13).
Intenté hacerlo desde la fuente pero sin éxito (toca demasiados lugares sensibles y nunca lo pude terminar bien).
Además de eso, de vez en cuando mi sonido desaparece completamente y tengo que reinstalar millones de paquetes para que funcione nuevamente (la última vez lo arreglé así pero ahora ni eso).

Desahogado vamos al tema: pienso que quizás en edgy las cosas funcionen un poco mejor así que estoy dispuesto a actualizar mi máquina pero antes necesito evaluar que podría perder en el viaje.
1- si bien tengo un backup de los archivos más importantes de mi /home, se perderá todo lo que allí haya cuando migre?
2- tengo varios programas que compilé desde la fuente, se perderán cuando haga el upgrade?
3- tengo varios programas en /opt (cliente de oracle, java, otros), se perderán cuando haga el upgrade?

Cualquier comentario que puedan hacerme (incluso como arreglar skype en dapper) será agradecido.

Un abrazo.

---

### Post by jpmorelli on 2006-11-29
> 
1- si bien tengo un backup de los archivos más importantes de mi /home, se perderá todo lo que allí haya cuando migre?
2- tengo varios programas que compilé desde la fuente, se perderán cuando haga el upgrade?
3- tengo varios programas en /opt (cliente de oracle, java, otros), se perderán cuando haga el upgrade?

Cualquier comentario que puedan hacerme (incluso como arreglar skype en dapper) será agradecido.

Un abrazo.

Si bien no tengo mucha experiencia sobre skype puedo asegurarte que la estabilidad en edgy es muy buena, por si te deja mas tranquilo. En cuanto a las preguntas:

1- si tu /home se encuentra en otra particion bastara con no formatearla cuando instales edgy y cuando crees el usuario principal le pongas el mismo nombre que el que usabas y todo levanta sin problemas.
2- Esos fuentes los vas a perder ya que no sirven para edgy.
3- igual a punto 1... si /opt esta en otra particion, no vas a perder nada.

Solo hay que ser cuidadoso en el momento en que uno va a armar la nueva instalacion a los discos y formatear solo las particiones swap y /

---

### Post by marianom on 2006-11-29
Gracias por los comentarios.
Veo que voy a tener que hacer todo de cero pero soy optimista, capaz que me divierto y todo haciendo todo de nuevo.

cuatro preguntas cuatro:
1- aquellos que tengan edgy, podrían chequear que versión de alsa tienen instalada?
2- firefox: supongo que en mi home estan guardadas mis preferencias (marcadores y páginas favoritas y esas cosas). Si guardo copia de ese/esos archivos, alguien sabe como se hace el update de firefox 2 para que las tenga en cuenta?
3- aquellos que tengan edgy, podrían chequear que versión de liferea tienen en los repos?
4- si alguno tiene experiencia en liferea (idealmente si lo usaron ates y después del upgrade) saben como hacer para migrar los rss que tienen? (no es tan grave, de ultima los copio en un txt y los pego de vuelta cuando esté todo instalado)

Gracias y saludos.

---

### Post by Nemesis Teufel on 2006-11-29
Es solo con skype o el sonido en general?

si es solo con skype quiza sea el programa. Probá con el wengo; es un programa GPL que tiene las mismas funciones, incluso videoconferencia que el skype para linux no tiene. Tengo que probarlo de todos modos para ver si bueno como asi parece ser.

[http://www.wengo.es/](http://www.wengo.es/)

esta en las repos de synaptic y hay instalacion en la pagina para windows y macos.

Espero que eso te lo solucione

---

### Post by spg76 on 2006-11-29
> **marianom said:**
> Gracias por los comentarios.
Veo que voy a tener que hacer todo de cero pero soy optimista, capaz que me divierto y todo haciendo todo de nuevo.

cuatro preguntas cuatro:
1- aquellos que tengan edgy, podrían chequear que versión de alsa tienen instalada?
2- firefox: supongo que en mi home estan guardadas mis preferencias (marcadores y páginas favoritas y esas cosas). Si guardo copia de ese/esos archivos, alguien sabe como se hace el update de firefox 2 para que las tenga en cuenta?
3- aquellos que tengan edgy, podrían chequear que versión de liferea tienen en los repos?
4- si alguno tiene experiencia en liferea (idealmente si lo usaron ates y después del upgrade) saben como hacer para migrar los rss que tienen? (no es tan grave, de ultima los copio en un txt y los pego de vuelta cuando esté todo instalado)

Gracias y saludos.

1- En Edgy la versión de alsa es 1.0.11 (Dapper 1.0.10).
2- Si haces upgrade a Edgy, Firefox 2 viene por default y debería guardarte sin problemas tus configuraciones y extensiones.
3- La versión de Liferea en Edgy es 1.0.23 (Dapper 1.0.12).
4- Yo no tuve que migrar nada, me guardo todo perfecto.

Espero que te sirva.
Saludos.

---

### Post by marianom on 2006-11-29
Gracias a todos por sus comentarios.

Nemesis: necesito tener skype o en su defecto algo que me permita chat con usuarios de skype. Me gustó lo que vi de wengo y además parece que tiene soporte para otros protocolos lo que me encantó (usó gaim pero el lento ciclo de desarrollo que tiene me pone nervioso) así que capaz que lo incorpore para ver que tal y si tengo suerte skype está o estará entre los protocolos soportados.

---

### Post by Nemesis Teufel on 2006-11-29
O hace una tendencia revolucionaria: decile a todos tus contactos que pongan wengo en vez de skype o las pagaran. :P

---

### Post by beuno on 2006-11-29
Deberias conservar todas tus preferencias, programas y archivos.
Problemas que pueden surgir:

- Se rompan las X (esto es casi cantado en los upgrades). Esto se arregla facil
- Java se niegue a funcionar bien, hay que reinstalarlo. Nada mas.

Yo uso el skype sobre edgy a diario y funciona muy bien.
Edgy tiene mas soporte para hardware, pero anda sabiendo que va a tener algun bug "molesto" que dapper no tenia.
Igual finalmente para todas las cosas nuevas que te da vale la pena aguantar algun que otro problema generalmente de interfaz.

Cualquier problema que te surja tene una PC a mano y anda pegandonos logs asi te ayudamos.

---

### Post by spg76 on 2006-11-29
> **marianom said:**
> si tengo suerte skype está o estará entre los protocolos soportados.

No creo porque Skype tiene un protocolo cerrado.
También podés probar Ekiga que viene instalado en Ubuntu.

---

### Post by marianom on 2006-11-29
Nemesis, si les llego a decir eso, el que no me pagará más es mi jefe (no está muy convencido que yo haya decidido cambiar a linux pero no me dice nada en la medida que -según él- no afecte mi laburo). Obvio que Ubuntu no solo no afecta sino que ayuda pero el tema del skype lamentablemente me pone bajo presión.

spg76, gracias. odio skype....

beuno, gracias por los datos. tengo varias máquinas así que cualquier problema de algún lado saldré a seguir molestando.
Si todo está bien mañana los veo en el irc desde edgy. Pregunta: a qué se quedó al final?

---

### Post by beuno on 2006-11-29
> **marianom said:**
> 
beuno, gracias por los datos. tengo varias máquinas así que cualquier problema de algún lado saldré a seguir molestando.
Si todo está bien mañana los veo en el irc desde edgy. Pregunta: a qué se quedó al final?

Reciencito postee: [http://ubuntuforums.org/showthread.php?p=1823284](http://ubuntuforums.org/showthread.php?p=1823284)

---

### Post by ari.maidana on 2006-11-29
> **marianom said:**
> Muchachos,
1- si bien tengo un backup de los archivos más importantes de mi /home, se perderá todo lo que allí haya cuando migre?
2- tengo varios programas que compilé desde la fuente, se perderán cuando haga el upgrade?
3- tengo varios programas en /opt (cliente de oracle, java, otros), se perderán cuando haga el upgrade?

Cualquier comentario que puedan hacerme (incluso como arreglar skype en dapper) será agradecido.

Un abrazo.

Por tus preguntas me parece que estás pensando en cambiar de versión instalando Edgy desde cero, o reformateando la partición raíz. Eso no es realmente necesario. En realidad, lo que te conviene hacer es actualizar mediante un dist-upgrade. Desde Ubuntu (GNOME) el notificador de actualizaciones te debe haber avisado cuando Edgy salió que hay una versión nueva. Tenés que entrar ahí y decirle que querés cambiar de versión. Si no pudieras hacerlo desde ahí, siempre podés editar en /etc/apt/sources.list  la palabra "dapper" por "edgy" en todos los lugares donde aparezca y borrar  o comentar cualquier entrada de un CDROM. Si tenés el CD de Edgy grabado podés agregarlo como fuente mediante "sudo apt-cdrom add". Eso te va a ahorar unos cuantos megas de descargas cuando actualices. Con "apt-get dist-upgrade" desde consola o diciendo que sí a la opción de hacer un dist-upgrade desde el menú gráfico.

1) Si actualizás mediante apt, tus datos en /home no se tocan para nada, aunque estén en la misma partición. Igual los backups nunca están de mas :)

2) En realidad lo de esos programas depende de cada uno, y de en qué medida dependan de las versiones específicas de sus dependencias. Pero lo peor que te puede pasar es tener que recompilar.

3) Los programas de /opt no se tocan, aunque estén en la misma partición, siempre que hagas el upgrade desde apt. Sólo se podrían ver afectados si alguno estuviera instalado desde un paquete deb que se llame exactamente igual a uno de la distribución, pero eso no es muy probable.
En relación con lo de java, si es la versión de Sun la que estás usando, podés instalarla desde apt (tenés que habilitar los repositorios universe y multiverse). Buscá los paquetes sun-java5-* (sun-java5-bin, sun-java5-jre, etc).

Saludos,
Ariel

---

### Post by Nemesis Teufel on 2006-11-29
> Nemesis, si les llego a decir eso, el que no me pagará más es mi jefe (no está muy convencido que yo haya decidido cambiar a linux pero no me dice nada en la medida que -según él- no afecte mi laburo). Obvio que Ubuntu no solo no afecta sino que ayuda pero el tema del skype lamentablemente me pone bajo presión.

Entiendo lo que me decis.. yo tan solo con decir Linux adelante de algunos amigos me miran con cara de freak que me la paso el dia programando y compilando (-1 de idea tengo). 
Quiza, lo que podes hacer para probar el wengo y dejar a todos contentos es instalarlo tambien y probarlo. Si va mal seguis usando elskype.. 
De ultima.. ni idea como sera tu jefe.. quiza funcione..le comentas la onda, de lo que tenes planeado hacer, que estas probando algo que se puede volver a  poner como antes sin perjudicar algo. Quiza lo ve como una preocupacion que vos tenes en el laburo y estas enganchado.. ahi no se que decirte.. habria que crear un subforo de psicopedagogia..no? :p

---

### Post by marianom on 2006-11-29
Mi jefe AMA windows, de todos modos es un buen tipo: nos deja tener todos los servidores en linux así que mejor me dejo de quejar (a ver si llega a leer esto)

Como verán por mi banner ya estoy en 6.10 (llevo como una hora con skype abierto sin "segmentation fault"!!!) y todas mis cosas están ok, no falta nada. 
A aquellos que vayan a hacer el update les recomiendo que tengan cuidado con el nessusd, se pone medio loco.

Un "esito" total diría un vecino mío. Nos vemos mañana.

---

### Post by marianom on 2006-11-30
No, se me sigue cerrando con el mismo error que en Dapper... no lo puedo creer... una autentica porquería este skype.

---

### Post by beuno on 2006-11-30
¿Que error te esta tirando?
¿Que chipset de audio tenes?

---

### Post by marianom on 2006-11-30
Segmentation fault, same old...

Como veo el chipset?

---

### Post by marianom on 2006-11-30
Puede ser VIA8237? Esa es la que tenía cuando intentaba instalar una nueva versión de alsa.

---

### Post by beuno on 2006-11-30
Proba abrir el skype desde la consola asi cuando vuelca ves el error.
Copiame y pegame eso.

El chipset lo podes ver en System > Administration > Device Manager
ahi tenes todos los chipsets de todo.

---

### Post by beuno on 2006-11-30
Probaste esto:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx)

---

### Post by marianom on 2006-11-30
Subí un error al Launchpad con el detalle del trace que te da Edgy.
Aca está el detalle completo del trace: [https://launchpad.net/distros/ubuntu/+bug/73929](https://launchpad.net/distros/ubuntu/+bug/73929)

Voy a chequear la página que me recomendas a ver que puedo hacer.

---

### Post by beuno on 2006-11-30
Proba lo de abrirlo desde la consola para ver que te dice ahi.

---

### Post by marianom on 2006-11-30
Creo que dice solo 
*Segmentation fault (core dumped)*
ya lo estoy corriendo desde la terminal, apenas pase lo pego aca para confirmar.

---

### Post by marianom on 2006-11-30
Confirmado:

mariano@mishima:~$ skype
Fallo de segmentación (core dumped)

---

### Post by jpmorelli on 2006-11-30
Buenísimo, y te lo confirmaron y todo ... un espectaculo.
A propósito como hiciste para subir el bug, algo en especial o solo lo mandas ?

---

### Post by marianom on 2006-11-30
Es fácil, un poco desorientador para llegar pero esencialmente te comento los pasos que sigo:
(desde el inicio y logueado con tu usuario).

1- Ingresá a: [https://launchpad.net/](https://launchpad.net/)
2- click en bugs
3- click en "bugs in Ubuntu"
4- en el search pones el paquete o texto afín que te está dando problemas (para evitar duplicados) y si no hay nada relacionado, click en "Report a bug" (arriba a la izquierda).
5- llenas con toda la información que más puedas. Los adjuntos solo se pueden agregar una vez el bug está creado y no hay que olvidarse de poner una descripción del adjunto, si no da error.

Se supone que edgy tenemos algo llamado bug buddy que se encarga del envío de bugs cuando hay un crash pero como skype no es realmente un paquete de ubuntu, no lo hizo. De todos modos me generó un lindo log en /var/crash que fue el que subí.

---

### Post by jpmorelli on 2006-11-30
Copy roger !

---

### Post by pakux on 2006-12-02
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

no debería perder ningún dato, ni los programas ya instalados. A mí incluso me funcionó la configuración de la resolución de la pantalla y de la tarjeta de sonido (que en su momento fueron todo un dolor de cabeza cuando instalé Dapper).

ojalá no sea demasiado tarde...

---

