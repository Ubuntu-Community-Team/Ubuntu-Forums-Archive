---
title: "Problema con particiones y permisos"
date: 2007-08-23
forum: Argentina Team
---

### Post by LaHire on 2007-08-23
Saludos a todos!
Primero q todo, este es mi primer post en los foros de ubuntu, y estoy muy emocionado :).-

Hace 2 o 3 anios (N de R: no me anda bien el teclado ni la cabeza, perdon los horrores ortograficos) que uso Ubuntu, y el dia de hoy se me presenta el primer problema "grave".-

Mientras trabajaba sobre el IDLE (un interprete de Python), quise abrir un reproductor de musica....y no se abrio. Aparecio, en la barra de tareas, el "abriendo reproductor de musica XMMS"...pero luego se "cerro".

Luego, probe abrir otras cosas, gedit, gnome-terminal....y lo mismo. Solo me abrio el Xterm.-
Pense "bueno, se trabo x...pruebo cambiar de usuario y si no anda asi...reinicio X"....y la verdad que exploto todo :P

Resulta que la (unica) particion que tiene el disco (en la cual trabajo, o trabajaba) es /dev/hdc1...y cuando intento cambiar algo...o hacer N tipo de cosa que requiera de archivos temporales... me tira un error de que la particion esta en Read Only Mode.
Lo raro es que, cuando pongo mount sin modificadores ni nada...me aparece como que esta en "RW" (Read-Write Mode) :confused::confused:

Leyendo por ahi (en este mismo foro), encontre algo similar...y recomendaban hacer un e2fsck sobre la particion (desmontada).

Cosa que hice...y me tira una cantidad increible de errores de I/O...

Ahora mismo estoy sobre un Live CD...y pensaba formatear y reinstalar Ubuntu (por suerte mis back-ups no son tan pesados)...pero...existe alguna forma de arreglar esto sin tener que recurrir al format?

Lo mas raro de todo es que paso de un momento a otro....automagicamente :P

en fin, gracias desde ya...y..aunq mi primer post sea un pedido de ayuda...espero yo poder colaborar en lo que pueda :)

un saludo grande a todos!

Salud!

---

### Post by marianom on 2007-08-23
Si tenes bloques defectuosos podes correr un badblocks (usa man para enterarte más al respecto) para confirmarlo y llegado el momento de formatear la partición (si no existe otra solución antes), usarlo para que elimine esos bloques y no los utilice (ahi lo haces con  e2fsck o mke2fs)
Es un proceso que lleva bastante tiempo así que te lo recomiendo como casi último recurso.

---

### Post by LaHire on 2007-08-23
Probé hacer lo que recomendaste...pero nada (o si?)

Situación:

inicio Ubuntu normalmente (es un 7.04, por cierto)...y en un momento dice que hdc1 tiene errores y fuerza un fcsk...y en el %38.9, comienza a tirar errores de I/O

Luego de un rato de tirar errores, me pide la contraseña de root, o que presione ctrl+D para reiniciar la máquina.

cuando ingreso como root (y acá es -otra- cosa rara. pongo la contraseña de root de mi sistema E ingresa correctamente....pero no encuentra ningún comando bash (por ej: clear!!!)...pero por lo menos si encuentra e2fsck y otros similares) y me propongo a hacer badblocks....
no pasa nada

root@nostromo#: badblocks /dev/hdc1

y en la linea siguiente está en blanco.-
Sólo se que el led que indica que el disco está trabajando está encendido...
pero...hay otra forma de saber si -realmente- está trabajando?

es normal?, no imprime nada en la pantalla como por ej: "Running BadBlocks" o algo así?

tengo que empezar a usar mejor consola....

en fin
por cierto, sería algo similar hacer
e2fsck -c /dev/hdc1?
porq lo hice...y mismo resultado (no pasa nada...solo...se prende esa luz)

capaz que -SI- esté haciendo algo y yo no me doy cuenta...pero bueno
perdon mi ignorancia :)

---

### Post by marianom on 2007-08-23
Si, es lo mismo. Yo cuando lo he corrido me mostraba que bloque estaba analizando (llevaba 2 días haciendolo y alguien pateó el enchufe por error, nunca más...)
Una cosa que me extraña es que el fsck no te pregunte si queres corregir los errores. En mi experiencia cuando lo ejecuto me va preguntando error por error si quiero o no arreglarlo (como te explico que es un Y de cajón)
Tratá de iniciar la máquina en modo rescate (no se como será en Ubuntu porque por suerte nunca me pasó pero en otras distros es: 1-boot desde el CD, 2- F5 una vez iniciado y 3- linux rescue) y corre el fsck vos directamente a ver si te pregunta para arreglar los errores (que es el comportamiento por defecto).

Soy medio pesimista porque en mi experiencia ese error es problema de hard y si bien lo vas sobreviviendo día a día eventualmente es para desastre. Pero bueno, que mi mala onda no te prive de internarlo!

Suerte

---

### Post by LaHire on 2007-08-24
> **marianom said:**
> Si, es lo mismo. Yo cuando lo he corrido me mostraba que bloque estaba analizando (llevaba 2 días haciendolo y alguien pateó el enchufe por error, nunca más...)
Una cosa que me extraña es que el fsck no te pregunte si queres corregir los errores. En mi experiencia cuando lo ejecuto me va preguntando error por error si quiero o no arreglarlo (como te explico que es un Y de cajón)
Tratá de iniciar la máquina en modo rescate (no se como será en Ubuntu porque por suerte nunca me pasó pero en otras distros es: 1-boot desde el CD, 2- F5 una vez iniciado y 3- linux rescue) y corre el fsck vos directamente a ver si te pregunta para arreglar los errores (que es el comportamiento por defecto).

Soy medio pesimista porque en mi experiencia ese error es problema de hard y si bien lo vas sobreviviendo día a día eventualmente es para desastre. Pero bueno, que mi mala onda no te prive de internarlo!

Suerte

Sin el Live-CD, probé hacer lo que dijiste
primero, con el parámetro "-p" (que hace "automágico" la reparación...y no pregunta nada) y, claro, detectaba errores y me pedía un fsck manual.
Cosa que hice, con el parámetro "-y" (asume yes para todo)
y, luego de fixear una gran cantidad de errores, pidió reboot...y funcionó!

Ahora solo me queda la pregunta "¿por qué?"
y esto

kane@Nostromo:~$ mount
/dev/hdc1 on / type ext3** (rw,errors=remount-ro)**
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

probé hacer lecto escritura y todo 10 puntos...por ahora
gracias por la ayuda!

---

### Post by faktorqm on 2007-08-24
hola, a mi paso algo parecido una vez, fue todo muy raro.
una vuelta, prendo mi pc, arranca ubuntu, y me decia como que habia hecho no se que cosa como 30 veces que tenia que pasarle el fschk obligatoriamente digamos. Ahi me empezo a decir que el i-nodo no se que bola, y asi tenia muchos, asi que me empece a poner nervioso. (se acuerdan de los viejos viejos tiempos de scandisk con dos 6.22, que te recuperaba los archivos como back001.chk, back002.chk, y vos no sabias cual era cual despues? bueno senti lo mismo que aquellas veces :S)
Entonces llegue a la parte que decia CTRL+D, pero soy tan tonto que no leia, y apretaba CTRL+D y lo único que hacia era reiniciar, tirar los mismos errores y mostrarme el mismo cartel. 
Hasta que al final puse la contraseña xDxDxD y me recomendaba que use un comando re loco, tipo "fschk -d -y" por decirte algo, (ni idea en realidad). 
Ahi me empezo a hacer algo con los i-nodos, me dijo que el indice estaba ok y ke tenia que reiniciar. Reinicie y nunca jamas volvi a tener un problema de ese estilo ni con los i-nodos. :confused::confused::confused::confused::confused:
Suerte! salu2!!

---

### Post by marianom on 2007-08-24
> **LaHire said:**
> Ahora solo me queda la pregunta "¿por qué?"

Tantas cosas pueden pasar... un shutdown forzado en un momento inconveniente, problemas de recuperación del journal de ext3, problemas del hardware. Hay que replicar, rastrear, cotejar, agarrarlo de la pestaña y solucionarlo.

> **LaHire said:**
> 
y esto

kane@Nostromo:~$ mount
/dev/hdc1 on / type ext3** (rw,errors=remount-ro)**

Es una opción de comportamiento al montar ese disco. Si hay errores que lo monte solo lectura. Pegale una leída al man de mount para más datos.

---

### Post by LaHire on 2007-08-28
> **marianom said:**
> (...) Hay que replicar, rastrear, cotejar, agarrarlo de la pestaña y solucionarlo.


Badblocks?

> **marianom said:**
> 
Es una opción de comportamiento al montar ese disco. Si hay errores que lo monte solo lectura. Pegale una leída al man de mount para más datos.

hay errores:
"""
Error reading block 10879253 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error? 
"""

de esos, hay...bastantes

si le pongo el parametro "-y", lo ignora Y luego lo reescribe (porq luego pregunta si se desea sobreescribir...y como esta el yes por default...)

Entonces... voy a tener que quedarme enfrente de la pc un buen dia, con mucho cafe, y valium, para poner que no ignore el error?
y luego, badblocks? :P

---

### Post by marianom on 2007-08-28
El problema es que Badblocks no te va a ayudar en todos los casos. Hay a veces problemas electronicos en el disco y los sectores defectuosos van a crecer más allá de lo que hayas rastreado con badblocks y van a saltar en otro momento.

(Esperemos que alguien con más onda que yo se sume a este thread. Las dos veces que a mi me pasó tuve que tirar el disco a la basura, por eso estoy medio como abogado del diablo :))

---

### Post by clasificado on 2007-08-28
Pasaba, vi luz y entré: Lo que tenés es un disco rígido que se va a morir en un corto - mediano tiempo.

Es como si tuvieras un auto, un dia agarras un pozo y una rueda nunca va a volver a ser la misma. 

Tarde o temprano vas a tener que hacer el cambio, y si es muy tarde te va a abandonar y vas a tener que contar cuánto perdés en el accidente.

Todo el resto (badblocks, e2fsck) es para tratar de rapiñar ese disco: Si el problema es físico, descarta los bloques dañados; Si el problema es electrónico, se te van a morir bloques alternadamente y te van a dar muchos dolores de cabeza

Ése no es un disco al que a mi me gustaría tener mi laburo, mis fotos familiares ni mis documentos personales. Mañana puede que despierte y ya no estén mas ahi.

Por el resto, el amigo ya dijo todo lo que yo podía aportar (Badblocks + e2fsck)

Clasificado

---

### Post by ecodina22 on 2007-08-28
La logica algebraica de un usuario novato:
si uno puede invertir en un segundo disco rigido?
Asi en caso de problemas se monta el disco alternativo.
El problema es que hay que hacer algo antes que el desastre ocurra.
No creen?

---

### Post by LaHire on 2007-08-29
> **ecodina22 said:**
> La logica algebraica de un usuario novato:
si uno puede invertir en un segundo disco rigido?
Asi en caso de problemas se monta el disco alternativo.
El problema es que hay que hacer algo antes que el desastre ocurra.
No creen?

Así es :)

problema: mi lógica monetaria entra en conflicto con tu tésis, la cual es viable, si comprobamos que las funciones de ahorro estén en crecimiento exponencial (a infinito positivo)

problema 2: no lo están :P

---

### Post by msangil on 2007-08-30
> **LaHire said:**
> Así es :)

problema: mi lógica monetaria entra en conflicto con tu tésis, la cual es viable, si comprobamos que las funciones de ahorro estén en crecimiento exponencial (a infinito positivo)

problema 2: no lo están :P


:lolflag:   :lol:

---

