---
title: "Ubuntu 12.04 - Swapfile"
date: 2014-12-17
forum: Argentina Team
---

### Post by Vero1 on 2014-12-17
Buenas tardes,

Tengo un disco de 500 Gib, todo particionado. 

Al haber "muerto" un disco en el que tenía instalado Windows, reparticioné el otro de 500 Gib, pero para poder darle espacio a Windows tuve que eliminar la Partición Swap, con la intención de crear mas tarde un Swapfile, según me recomendó un amigo informático.

Yo tengo 2 Gib de RAM y quiero tener 4Gib de swapfile, primero porque en Raíz tenía suficiente lugar(ahora explico porque digo tenía). Este amigo me envió un comando para crear dicho archivo pero cuando hice la pregunta de swapon -s me mostró nada mas que 2 Gib de swapfile. No pude comunicarme más con mi amigo que vive en España así que quise arreglar la cantidad de Gib, pero no eliminé el archivo que se había creado. Hice varias pruebas, sacando información de Internet pero no dí en el clavo. Al querer hacer una nueva prueba, me salió una advertencia que el Archivo / no tenía más lugar. Antes de todo ésto yo tenía alrededor del 44% de lugar libre en el Archivo Raíz, por lo tanto empecé a sospechar que se debía a no haber eliminado los archivos que pueden haber quedado. Pero al correr swapon -s me sale que no hay nada allí.

De qué manera puedo saber dónde están esos archivos y cómo hago para eliminarlos y recuperar el espacio.

Posteriormente les voy a preguntar los valores que debo poner para tener los 4 Gib de swapfile.

Les agradeceré una pronta respuesta, dado que trabajo con fotografías, videos, etc. y la máquina está muy lenta.

Desde ya muchas gracias y cualquier aclaración no tienen mas que pedírmela.

Saludos

p.d.

Encontré dos archivos en Raíz: Swap y Swapfile.swap que, evidentemente no han sido eliminados, así que por favor díganme qué orden debo poner en Terminal para eliminarlos y recuperar espacio. Gracias

---

### Post by Vero1 on 2014-12-18
Les envío una salida para que vean dónde están estos dos archivos.

[IMG][img]http://i.imgur.com/AxuGLD0.png?1[/img][/IMG]

---

### Post by enriquek2 on 2014-12-19
En primer lugar no es recomendable tener una swatfile por que puede ser causa de fragmentación
Para saber o recordar los comandos que usaste para crear el swtfile entra a un terminal y pulsa la flecha arriba hasta dar con los comandos , siempre queno hayas borrado el historial de bash, si usaste una termial de root primenro ejecuta
sudo su y luego de poner tu contraseña pulsa la tecla arriba , los comandos que seguramente usaste se inician con 
dd if=/dev/zero of=ruta/swapfile bs=1M count=2000
 mkswap ruta/swapfile

en definitiva podrás averiguar la ruta del swatfile  y una vez la averiguas ejecuta
sudo swapoff -a
sudo rm ruta swatfile
además debes borrar la entrada en  el fstab que seguramente debiste introducir para que el swatfile arranque al inicio

---

### Post by papibe on 2014-12-19
Hola Vero1.

Es muy fácil reducir de tamaño una de las particiones que ya existen. Si reduces una de ellas exactamente 4Gb, te quedará libre el espacio necesario para crear una partición de swap.

Usa el CD/USB de instalación como un "Live CD". Selecciona 'Probar Ubuntu' en vez de instalar. Una vez que el entres en el escritorio, puedes usar 'gparted' para hacer lo anterior.

Una vez que termines, puedes acceder al disco local (no el de la versión que está corriendo Live) y modificar el /etc/fstab para montar la nueva partición de swap.

Ojala te sirva. Dinos si necesitas mas detalles.
Saludos.

---

### Post by Vero1 on 2014-12-20
> **enriquek2 said:**
> En primer lugar no es recomendable tener una swatfile por que puede ser causa de fragmentación
Para saber o recordar los comandos que usaste para crear el swtfile entra a un terminal y pulsa la flecha arriba hasta dar con los comandos , siempre queno hayas borrado el historial de bash, si usaste una termial de root primenro ejecuta
sudo su y luego de poner tu contraseña pulsa la tecla arriba , los comandos que seguramente usaste se inician con 
dd if=/dev/zero of=ruta/swapfile bs=1M count=2000
 mkswap ruta/swapfile

en definitiva podrás averiguar la ruta del swatfile  y una vez la averiguas ejecuta
sudo swapoff -a
sudo rm ruta swatfile
además debes borrar la entrada en  el fstab que seguramente debiste introducir para que el swatfile arranque al inicio

Gracias EnriqueK, ya está solucionado. Usé el comando rm /swapfile.swap. Tambien borré la entrada en fstab.
Saludos

---

### Post by Vero1 on 2014-12-20
> **papibe said:**
> Hola Vero1.

Es muy fácil reducir de tamaño una de las particiones que ya existen. Si reduces una de ellas exactamente 4Gb, te quedará libre el espacio necesario para crear una partición de swap.

Usa el CD/USB de instalación como un "Live CD". Selecciona 'Probar Ubuntu' en vez de instalar. Una vez que el entres en el escritorio, puedes usar 'gparted' para hacer lo anterior.

Una vez que termines, puedes acceder al disco local (no el de la versión que está corriendo Live) y modificar el /etc/fstab para montar la nueva partición de swap.

Ojala te sirva. Dinos si necesitas mas detalles.
Saludos.

Gracias por los comentarios.
En su oportunidad no pude crear una partición Swap porque tenía todas las primarias ocupadas y la única salida fue hacer un Archivo Swap. 
Mi único problema ahora es que no logro poner la cantidad en "count".
Originalmente me habían dicho poner 1048576 pero con esta cifra me daba 2 Gib, no 4.
Entonces hice la pregunta en varios Foros, nadie me contestó hasta Ask Ubuntu. De ahí me sugirieron que duplique esta cantidad. Me pareció lógico y lo hice pero ahora me sale que tengo 8 Gib, no 4.
Si yo pongo este comando:
sudo dd if=/dev/zero of=swapfile.swap bs=4096 count=                 qué cifra debe ir para que me dé 4 Gib?
Si me aclarás ésto podré dar por finalizado este problema que ya me lleva cerca de 10 días, sin poder resolver.

Muchas gracias.
Saludos.

---

### Post by enriquek2 on 2014-12-20
Pone la salida de 
df -H

---

### Post by Vero1 on 2014-12-20
veronica@veronica-System-Product-Name:~$ df -H
S.ficheros     Tamaño Usados  Disp Uso% Montado en
/dev/sda2         86G    15G   67G  18% /
udev             1,1G   4,1k  1,1G   1% /dev
tmpfs            211M   1,2M  210M   1% /run
none             5,3M      0  5,3M   0% /run/lock
none             1,1G   144k  1,1G   1% /run/shm
/dev/sda1        7,9G   160M  7,3G   3% /boot
/dev/sda3        315G    62G  238G  21% /home
/dev/sdb1        3,9G   1,1G  2,9G  27% /media/FB96-F603
veronica@veronica-System-Product-Name:~$ 

Saludos

---

### Post by enriquek2 on 2014-12-20
La idea es poner la swapfile en /home así no mermas el espacio en  / y evitas fragmerntación en este
En un terminal  pones 
sudo su
 luego de poner tu pass , pones los siguientes comando uno por vez
1.- dd if=/dev/zero of=/home/swapfile bs=1M count=4000
 2.- mkswap /home/swapfile
3.- echo -e '# Entry for swapfile : \n /home/swapfile \t swap  \t swap \t defaults \t   0   \t 0' >> /etc/fstab
4.- init 6

En tu lugar muevo el contenido de /boot en / y así te quedaría libre sda1 de 6Gb ideal para tener  la swap

---

### Post by Vero1 on 2014-12-21
Hola EnriqueK,

Me parece que estoy en otro lío. 
No puedo hacer nada. Al querer poner el comando me sale: dd: memoria agotada por buffer de entrada de 1073741824 bytes (1,0 Gib).

Tengo que eliminar lo que hay en caché y buffer?

Te pongo lo que me sale en Terminal con free:

veronica@veronica-System-Product-Name:~$ free
             total       used       free     shared    buffers     cached
Mem:       2052952    1229836     823116          0     117752     703796
-/+ buffers/cache:     408288    1644664
Swap:            0          0          0
veronica@veronica-System-Product-Name:~$ 


Si tengo que eliminar, con qué comando?

Gracias

---

### Post by enriquek2 on 2014-12-21
Es posible que por los rquerimientos de Unity te quedas con muy poca ram disponible, podrías intentar dos cosas
Primero que nada anotá en papel los comandos que te puse por que no tendrás entorno gráfico
1.- Ejecutá los comandos en Recovery Mode . espera a que termine la rutina y eliges la opción creo que se llama netroot o algo así , lo importante es que vas a tener un terminal de root  así que ya no tendrás que poner 
sudo su
2.- la otra forma sería mater las X en un tty
para esto último  ejecuta
Alt + Ctrl +F1
luego de logearte  ejecuta
sudo su
pones tu pass 
service lightdm stop
por último ejecutas los comandos
dd if=/dev/zero of=/home/swapfile bs=1M count=4000 
etc
etc

---

### Post by enriquek2 on 2014-12-21
mensaje repetido

---

### Post by Vero1 on 2014-12-22
Hola a todos los que ayudaron.

Ya solucioné el problema. Pude crear el swapfile, una vez que cerré todo y reinicié. 
El comando final que he usado es bs=1G count=4. Con ésto tengo 4 Gib de swapfile.

Muchas gracias y saludos.

---

