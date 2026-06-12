---
title: "Agregar temas a un reprod. mp3"
date: 2006-12-21
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-12-21
Tengo un mp3 SanDisk Sansa de 1gb. Y si bien lo tengo en fat.. cuando lo conecto a ubuntu.. me lee las carpetas.. pero me lee OTRAS! no son las que estan x ej en windows.. no estan los temas.. ni ocultos y a la vista.. no lo puedo hacer conectar con amarok para aunque sea reproducir los temas. Cuando voy a propiedades.. me dice que esta solo en lectura.. y si quiero ponerlo en lectura  y escritura me tira error. Y si enchufo temas no los lee.
El problema es de Ubuntu, de MI Ubuntu, del mp3 o de MI mp3?

---

### Post by spg76 on 2006-12-21
Yo tengo un MP3 Sandisk Sansa de 512MB y Ubuntu lo reconoce perfectamente, asi que puedo agregar temas (o datos) desde Nautilus. Fijate en si podes cambiar el modo de conexión en el reproductor (en el mío no se puede pero según lei en otros Sansa si) en Settings > USB > MSC. Tenes que ponerlo en MSC.
Lamentablemente, Amarok no me lo reconoce automaticamente, aunque creo que tocando algún archivo de configuración debería funcionar.
Saludos.

---

### Post by Nemesis Teufel on 2006-12-21
mm.. resulta que en windows tmb me pasa.. es aca en la pc.. en la otra funciono..
lo raro es que una vez en pude hacerlo correr en windows en esta misma pc..
me aparecen los mismos archivos tanto en ubuntu como en windows.. y esta en MSC.

Es un problema de la pc supongo.
en google no hay nada :(

---

### Post by jpmorelli on 2006-12-21
Excuse me ! Pero yo tambien tengo un Sandisk Sansa E140 y Ubuntu y amarok me lo reconocen perfecto !!! no tuve más que conectarlo para que lo reconozca y hasta amarok me dijo que habia un dispositivo nuevo si queria agregarlo, transfiero desde ahi o lo uso tipo USB disk.
Asi que debe ser algo que no esta del todo original o que la maquina tenga USB 1.1 porque como te digo, la mia lo reconocio perfecto. Aclaro mis USB son 2.0.
Ya que estamos les comento, tengan cuidado con la pantalla ! es super sensible, a mi se me rompio el display por darle un poquito mas fuerte al boton de Play y me queria matar, eso si, mande un mail a Sandisk para ver si podían arreglarlo y no solo me lo contestaron muy amablemente sino que aparte me dijeron que se los mande que me lo cambiaban por otro nuevo !!!! En este momento lo estoy extrañando porque lo tuve que mandar hasta EEUU ( un kilombo ) pero ayer me avisaron que llegó y que ahora ellos me estarían mandando el nuevo, unos grosos !
Otro Tip, fijense la version del firmware, la mia si mal no recuerdo era la 2.01 y para los que tienen una version más viejita esta el upgrade en la pagina de Sandisk. ( lástima que solo se puede hacer desde Win.
[http://www.sandisk.com/Retail/Default.aspx?CatID=1295]("http://www.sandisk.com/Retail/Default.aspx?CatID=1295")

---

### Post by spg76 on 2006-12-21
> **jmorelli said:**
> hasta amarok me dijo que habia un dispositivo nuevo si queria agregarlo, transfiero desde ahi o lo uso tipo USB disk.

Entonces voy a probar a ver si Amarok me lo reconoce. Cuando intente antes no me funciono (ojo, tampoco me mate). Quizas tenga que actualizar Amarok. 
Yo tengo un E130, aunque calculo que será lo mismo.

---

### Post by jpmorelli on 2006-12-21
Deberia ser igual ! Te lo va a tomar como un Reproductor USB generico, pero funciona OK !

---

### Post by Nemesis Teufel on 2006-12-22
Si.. me lo detecta perfectamente al mp3.. pero el problema es que no lee como deberia..
lee otras carpetas, no lee la musica que hay, y si agrego musica no la toma dps el reproductor.

---

### Post by jpmorelli on 2006-12-22
> **Nemesis Teufel said:**
> Si.. me lo detecta perfectamente al mp3.. pero el problema es que no lee como deberia..
lee otras carpetas, no lee la musica que hay, y si agrego musica no la toma dps el reproductor.

La verdad que ese problema no lo tenía y use el reprodcutor tal cual vino de fábrica, probé hasta si leía ogg pero no :( , pero los formatos wma y mp3 que le pasaba ningun drama y lo que tenía lo bajaba a mi compu y todo bien tambien, buscale la vuelta porque algo te está faltando.

---

### Post by randu on 2007-08-12
hola a todos 
se que esta algo desactualizado el tema, pero hace poco compre un sansa y pues queria preguntarles que si lo han podido enlazar con ubuntu, ya que pues en modo usb me lo reconoce pero el banshee no me lo reconce, voy a intentar con amarok a ver que tal me va

---

### Post by faktorqm on 2007-08-13
Yo me fijaria como lo estas montando al usb. Capaz lo estas montando en solo lectura. Fijate de hacerlo por consola, desmontando primero, y luego montando como root. (usá sudo)
A mi me pasa lo mismo pero con un disco extraible que tengo, si lo monto con la interfaz grafica, no puedo borrar archivos, ni escribir sobre el disco. Me voy a una consola, lo monto como root y listo.
Lo de que no te muestra todos los archivos y carpetas, prestá atención a los acentos. Yo tengo compartido en el laburo una particion ntfs con mp3 (mis compañeros usan windows, yo linux en el extraible) y todos los mp3 con acentos directamente no me aparecen, ocasionando perdida de temas xD) pero cuando arranco con el windows "aparecen". Salu2!

---

