---
title: "Sobre el anuncio &quot;Malicious Commands&quot;"
date: 2007-11-20
forum: Argentina Team
---

### Post by leo_rockway on 2007-11-20
Quizás hayan leído un anuncio en el foro sobre "comandos maliciosos", si no lo hicieron léanlo y vuelvan...

Mi pregunta es: ¿Qué tiene de malo el comando rm -rf? Es un comando muy útil y mucho menos riesgoso que gksudo nautilus, por ejemplo.

rm -rf sirve para borrar un directorio entero sin pedir verificación, es algo extremadamente normal querer hacer algo así. Ni siquiera tiene un sudo delante, así que no existe el riesgo de borrar archivos de sistema.

Está bien que se banee a un usuario que con toda maldad y alevosía hace que alguien borre algún directorio de sistema, pero hacer uso de ese comando de buena fe y enseñando lo que hace no me parece mal, más bien todo lo contrario.

Yo creía que ubuntuforums estaba para informar a los usuarios, no para andar escondiéndole comandos.

---

### Post by santiagoward2000 on 2007-11-20
> **leo_rockway said:**
> Quizás hayan leído un anuncio en el foro sobre "comandos maliciosos", si no lo hicieron léanlo y vuelvan...

Mi pregunta es: ¿Qué tiene de malo el comando rm -rf? Es un comando muy útil y mucho menos riesgoso que gksudo nautilus, por ejemplo.

rm -rf sirve para borrar un directorio entero sin pedir verificación, es algo extremadamente normal querer hacer algo así. Ni siquiera tiene un sudo delante, así que no existe el riesgo de borrar archivos de sistema.

Está bien que se banee a un usuario que con toda maldad y alevosía hace que alguien borre algún directorio de sistema, pero hacer uso de ese comando de buena fe y enseñando lo que hace no me parece mal, más bien todo lo contrario.

Yo creía que ubuntuforums estaba para informar a los usuarios, no para andar escondiéndole comandos.

Yo estuve siguiendo ese problema. El tema es que en el foro para principiantes, un spammer estuvo respondiendo a todos los que tenían un problema, diciéndoles que corran un comando que les borraba la carpeta /home. Como eran usuarios que recién empezaban, muchos lo hicieron sin saber qué hacían...
Sé que el comando puede ser útil, pero habría que encontrar alguna otra forma para que esto no vuelva a pasar.

---

### Post by leo_rockway on 2007-11-20
> **santiagoward2000 said:**
> Yo estuve siguiendo ese problema. El tema es que en el foro para principiantes, un spammer estuvo respondiendo a todos los que tenían un problema, diciéndoles que corran un comando que les borraba la carpeta /home.

OK, yo no seguí el problema, sólo vi el anuncio y me pareció rarísimo que quisieran prohibir el uso de ese comando.

Bueno, entonces estoy de acuerdo. Tal como dije en mi post anterior: si el que escribe ese comando lo hace de mala fe, merece que se lo banee.

---

### Post by faktorqm on 2007-11-21
hola, esta todo mas que bien, pero yo no me voy a poner script por script a ver que comando tiene, o si le doy con sudo o nada, si me borra o no me borra. por ejemplo el envy, que te instala el driver de nvidia, y lo considero un script "grande", como hago para verificar fehacientemente que el tipo no me rompe un modulo, una carpeta, que no manda un mail con mi informacion afuera, si un script como de 2000 lineas con suerte!
Leo tiene razon, es lo mismo que te digan que hagas "format c:" o "del *.*" o "deltree *", como evitas eso? 
yo diria que empiecen regalando los manuales de ubuntu................ jajajajaj vamo' muchachos! largando los manuales gratis :P :P que si no no voy a confiar mas en su sistema operativo xDXDXD
che igual me asusto te digo, yo instalo cualquier bobada que anda dando vueltas por ahi, y en la compu del trabajo ni hablar, en mi casa no. salu2!!

---

### Post by xpelaox on 2007-11-21
ese anuncio me hizo pensar... osea yo siempre que tengo un problema googeleo, generalmente hay algun post, copio los comandos en y pego en la consola .. uno se puede dar cuenta que si hay un comando que se llama "format system" es sospechoso, pero alguno de esos comandos que lei,,, yo ni sospecharia y les daria sudo y enter sin miedo.... asi que me voy a empezar a cultivar en el asunto para no caer:P

Saludoss

---

### Post by marianom on 2007-11-21
No te hagas problema: si siempre que aplicás alguna solución, vas prestando atención, los comandos se aprenden, casi diría que se incorporan por osmosis.

---

### Post by santiagoward2000 on 2007-11-21
> **marianom said:**
> No te hagas problema: si siempre que aplicás alguna solución, vas prestando atención, los comandos se aprenden, casi diría que se incorporan por osmosis.

La mayoría sí, pero en el aviso leí un tal Forkbomb, y el comando es solo una combinación de símbolos que ni idea qué quieren decir (por las dudas no voy a postear el comando acá). Pero según dice ahí, hace que el sistema empiece a hacer muchos procesos hasta que se cuelga.
> Executes a huge number of processes until system freezes, forcing you to do a hard reset which may cause corruption, data damage, or other awful fates.

---

### Post by marianom on 2007-11-21
El consejo que se da es saludable: salvo que confíes en la persona que te sugiere el código o entiendas que hace, no lo ejecutes.

---

### Post by ubuntu27 on 2007-11-21
> **faktorqm said:**
>  vamo' muchachos! largando los manuales gratis :P :P !


Esto podra ayudar a muchos. [Referencia a comandos comunes en GNU/Linux y Unix]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/").  Esta traducido en distintos idiomas, asi que hangan click en Spanish

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

---

### Post by WanderingKnight on 2007-11-21
Es sencillo: Minimizar el uso de los scripts de terceros al _minimo_. A menos que confien muchisimo en quien te lo esta dando (o que haya habido feedback positivo al respecto), _NO_ corran ningun script. Con los comandos sueltos hay menos drama, porque esta todo visible en la misma pagina del foro y es mas facil detectarlo, pero los scripts pueden tener una cantidad de comandos demasiado larga para hacer eso.

El ejemplo mas conocido es Automatix, que en muchas ocasiones genero problemas para los usuarios, a veces hasta dejando sus sistemas sin posibilidad de booteo.

---

