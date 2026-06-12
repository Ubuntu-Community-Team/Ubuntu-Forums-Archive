---
title: "[SOLVED] Falta de espacio en disco"
date: 2007-09-12
forum: Argentina Team
---

### Post by Vero1 on 2007-09-12
Hola,

Ubuntu está montado en un disco con una capacidad de 40 Gb.

Actualmente hay libres poco mas de 1 Gb... 

Quisiera saber qué es lo que puedo eliminar y cómo saberlo.

Corrí baobab y me dice que en Trash, por ejemplo, hay mas de 300 Mb.

Trash es basura o me equivoco? Si es basura, cómo lo elimino?

gracias

---

### Post by Mister X on 2007-09-12
las carpetas .Trash tienen el contenido de la papelera de cada usuario, tambien podes limpiar el cache de descarga de paquetes con el comando
```
# apt-get clean
```

---

### Post by Vero1 on 2007-09-12
Gracias Mister X:)

---

### Post by Vero1 on 2007-09-12
> **Vero1 said:**
> Gracias Mister X:)

Si se hace desde Terminal, no pasa nada con este comando:confused:

---

### Post by Mister X on 2007-09-12
tenes que hacerlo como root (por eso puse el simbolo # yo estoy acostumbrado a tener el usuario root habilitado :) ) o sino con sudo:
```
sudo apt-get clean
```

lo que hace es borrar el contenido de /var/cache/apt/archives/ (fijate con baobab cuanto te ocupa antes de ejecutar la limpieza)

---

### Post by Vero1 on 2007-09-12
:) Estuve a punto de poner sudo, pero no me atreví...(soy nueva con Ubuntu y estoy aprendiendo).

Ya me fijé en baobab y pesa mas de 300 Mb

gracias

---

### Post by Vero1 on 2007-09-12
> **Vero1 said:**
> :) Estuve a punto de poner sudo, pero no me atreví...(soy nueva con Ubuntu y estoy aprendiendo).

Ya me fijé en baobab y pesa mas de 300 Mb

gracias

Tampoco reacciona con sudo apt-get clean:confused:

---

### Post by slira on 2007-09-12
Olá

desculpa o portugues mas não escrevo castellano...

estas usando Gnome ou KDE? se usas KDE, do lado direito, em baixo, tens o símbolo de papelera... basta apontar aí, clicar com o botão esquerdo e "empty trash bin"- tudo irá fora :)

se queres verificar primeiro, escolhe "open in a new window"...

(funciona exactamente como no Windows XP)

slira

---

### Post by Vero1 on 2007-09-12
> **Vero1 said:**
> Tampoco reacciona con sudo apt-get clean:confused:

Pasa una cosa rara. Veo mi carpeta personal y la papelera no tiene nada, está en 0. Cómo se explica?

Perdoná tanto lío.

---

### Post by Vero1 on 2007-09-12
> **slira said:**
> Olá

desculpa o portugues mas não escrevo castellano...

estas usando Gnome ou KDE? se usas KDE, do lado direito, em baixo, tens o símbolo de papelera... basta apontar aí, clicar com o botão esquerdo e "empty trash bin"- tudo irá fora :)

se queres verificar primeiro, escolhe "open in a new window"...

(funciona exactamente como no Windows XP)

slira

Hola y gracias por contestar. Entiendo igual lo que escribiste:)
Tengo Gnome, así que lamentablemente la papelera no está en el escritorio.

gracias igual:)

---

### Post by Mister X on 2007-09-12
> **Vero1 said:**
> Tampoco reacciona con sudo apt-get clean:confused:

Te da un error o que?


> **Vero1 said:**
> Pasa una cosa rara. Veo mi carpeta personal y la papelera no tiene nada, está en 0. Cómo se explica? 

Como ves que esta en cero?

Para ver el tamaño de una carpeta desde la linea de comando:
```

  du -sh  /var/cache/apt/archives/

  du -sh  /home/tu_usuario/

```

Otra cosa, en Gnome si se puede ver la papelera en el escritorio, abri el programa Editor de configuracion, en la derecha tenes un arbol, anda hasta /apps/nautilus/desktop y tilda trash_icon_visible.

Saludos

---

### Post by Mafber on 2007-09-12
Hola Vero1!!!
si queres ver la papelera en el escritorio podes hacer esto:
en una terminal poné: "gconf-editor" (sin la comillas)
buscá "apps" .... despues "nautilus" ... "desktop"
y dentro de esta última carpeta buscá:
"trash_icon_visible" activalo (Activado)
Suerte!!!

---

### Post by Vero1 on 2007-09-12
> **Mister X said:**
> Te da un error o que?




Como ves que esta en cero?

Para ver el tamaño de una carpeta desde la linea de comando:
```

  du -sh  /var/cache/apt/archives/

  du -sh  /home/tu_usuario/

```

Otra cosa, en Gnome si se puede ver la papelera en el escritorio, abri el programa Editor de configuracion, en la derecha tenes un arbol, anda hasta /apps/nautilus/desktop y tilda trash_icon_visible.

Saludos

Veo el cero en mi carpeta personal.

Perdoná pero cómo abro el Editor de Configuración?

---

### Post by Vero1 on 2007-09-12
> **Mafber said:**
> Hola Vero1!!!
si queres ver la papelera en el escritorio podes hacer esto:
en una terminal poné: "gconf-editor" (sin la comillas)
buscá "apps" .... despues "nautilus" ... "desktop"
y dentro de esta última carpeta buscá:
"trash_icon_visible" activalo (Activado)
Suerte!!!

Hola y muchas gracias. Ya está la papelera en el escritorio:)

---

### Post by Montsegur87 on 2007-09-12
```

$sudo apt-get install deborphan
$sudo deborphan
a
b
c
$sudo apt-get --purge remove a b c
```

deborphan finds "orphaned" packages on your system. It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections. 

saludos

---

### Post by Vero1 on 2007-09-13
Hola Montsegur87,

Hasta sudo deborphan todo bien, me refiero que saca un informe.
Ahora, las letras a b y c qué significan?
Intento ponerlas pero dice que orden no encontrada.
Cómo es?
Qué sigue despues de sudo deborphan y antes de sudo apt-get, etc?
Gracias

---

### Post by marianom on 2007-09-13
Son un ejemplo. Reemplazá esas letras con los paquetes que tengas que purgar.

---

### Post by Vero1 on 2007-09-13
> **marianom said:**
> Son un ejemplo. Reemplazá esas letras con los paquetes que tengas que purgar.

marianom, no me dió oportunidad de poner nada, pero luego me pone ésto:
Los siguientes paquetes fueron instalados automáticamente y ya no son necesarios:
  beryl-core beryl-settings-bindings libberylsettings0 beryl-plugins
  beryl-plugins-data libberyldecoration0
Use «apt-get autoremove» para desinstalarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
veronica@veradri-desktop:~$ apt-get autoremove
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13 Permiso denegado)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Qué significa? Qué es ser root? Administrador?
Si es así, creo que lo soy...

---

### Post by marianom on 2007-09-13
Sos la administradora pero en Linux hay que acreditarse como tal (es una medida de seguridad). [Aca]("https://help.ubuntu.com/community/RootSudo") tenés una buena explicación al respecto.

> **Vero1 said:**
> no me dió oportunidad de poner nada

No entendí esa parte. ¿Qué no te dió oportunidad de poner nada?

---

### Post by LaHire on 2007-09-13
> **Vero1 said:**
> (...)
veronica@veradri-desktop:~$ apt-get autoremove
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13 Permiso denegado)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Qué significa? Qué es ser root? Administrador?

Si es así, creo que lo soy...

Si sos vos la que instalaste el sistema operativo, por defecto, sos la administradora del sistema (root), pero no te va a dejar "tocar nada" (me refiero a modificar archivos de sistema, y demas cosas importantes) sin que antes "corrobores" que estas en la lista de sudoers
para eso, se usa el comando sudo

sudo te deja ejecutar comandos como si fueras otro usuario, o un SuperUsuario

supongamos que , cuando instalaste Ubuntu, pusiste "veronica" como nombre de usuario (eso aparece en la linea de comando:  
veronica **(usuario con el que estas conectada)**@veradri-desktop **(nombre de la maquina en la que estas trabajando)**:~$)

Sin bien tengo entendido, Ubuntu va a tomar que el usuario "veronica" es el administrador de sistema,

EDIT: no se si eso es cierto, pero lo que estoy casi seguro es que mete al usuario a la lista de sudoers...o sea, los usuarios que pueden modificar el sistema

cuando quieras trabajar sobre la configuracion de sistema, te va a pedir Tu contrasenia 

asi que, por ejemplo

```
apt-get autoremove
``` va a tirar error, porq no especificaste que estas en la lista de sudoers

para evitar eso, y para poder trabajar sobre el sistema

le pones el comando "sudo" antes

```
 sudo apt-get autoremove 
```ahi te pide una contrasenia...ingresa la tuya y listo, espero

asi que bueno, siempre que quieras hacer algo "de administrador" como trabajar con apt, synaptic, modificar usuarios y demas cosas...vas a necesitar usar el comando sudo

perdon por mi horrible forma de explicar las cosas :)

espero ayudar!

EDIT:

man sudo en cosola es mucho MUCHO mas explicativo que yo, sorry :)

---

### Post by Vero1 on 2007-09-13
> **LaHire said:**
> Si sos vos la que instalaste el sistema operativo, por defecto, sos la administradora del sistema (root), pero no te va a dejar "tocar nada" (me refiero a modificar archivos de sistema, y demas cosas importantes) sin que antes "corrobores" que sos root
para eso, se usa el comando sudo

sudo te deja ejecutar comandos como si fueras otro usuario, o un SuperUsuario

supongamos que , cuando instalaste Ubuntu, pusiste "veronica" como nombre de usuario (eso aparece en la linea de comando:  
veronica **(usuario con el que estas conectada)**@veradri-desktop **(nombre de la maquina en la que estas trabajando)**:~$)

Sin bien tengo entendido, Ubuntu va a tomar que el usuario "veronica" es el administrador de sistema,

pero, por alguna razon que escapapa mi entendimiento (supongo que para evitar problemas en una cuenta compartida), siempre te va a pedir la contrasenia de administrador para hacer "operaciones administrativas"

esto es

cuando quieras trabajar sobre la configuracion de sistema, te va a pedir la contrasenia del root
(que no te asustes, es la contrasenia tuya, siempre y cuando vos hayas instalado el sistema operativo)

asi que, por ejemplo

```
 apt-get autoremove 
```
te va a denegar el acceso, porq no "apareces" como root

para evitar eso, y para poder trabajar sobre el sistema

le pones el comando "sudo" antes

```
 sudo apt-get autoremove 
```

ahi te pide una contrasenia...ingresa la tuya y listo, espero

asi que bueno, siempre que quieras hacer algo "de administrador" como trabajar con apt, synaptic, modificar usuarios y demas cosas...vas a necesitar usar el comando sudo

perdon por mi horrible forma de explicar las cosas :)

espero ayudar!

Sí mariano yo he instalado el sistema. Queda entendido lo de sudo.
intentaré nuevamente el autoremove con sudo.
Despues te digo.
Gracias y no es horrible tu explicación:)

---

### Post by Vero1 on 2007-09-13
> **Vero1 said:**
> Sí mariano yo he instalado el sistema. Queda entendido lo de sudo.
intentaré nuevamente el autoremove con sudo.
Despues te digo.
Gracias y no es horrible tu explicación:)

Resultó marianom y lo tendré en cuenta para el futuro.

Gracias.:)

---

### Post by LaHire on 2007-09-13
> **Vero1 said:**
> Resultó marianom y lo tendré en cuenta para el futuro.

Gracias.:)
Yo no soy marianom!, aunq si queres darme un @ubuntu yo no tengo problema, no?

y siempre, aunq no soy vocero ni nada por el estilo, la comunidad esta para ayudar siempre :), un placer ayudarte! xD

Marian...no, LaHire :P

---

### Post by Vero1 on 2007-09-13
uy, perdón, no se por que puse marianom. Será porque él me contestó primero.
Muchas gracias a vos entonces, es que ya estoy muy mareada con todo ésto tan nuevo y desconocido para mi:(

y acostumbrada a Windows pues me cuesta bastante enterarme de todo el funcionamiento de Ubuntu. Pero de a poco, no?

saludos:popcorn:

---

### Post by niko_3100 on 2007-09-14
Mira yo tengo 20 años y descubri ubuntu hace 4 meses y ya le agarre la mano. Para borrar cosas tenes apt-get remove archivoABorrar o sino a mano borrando las carpetas, desconosco si hay otra manera de quitar software tipo el xp en panel de control. tambien en el "inicio" tenes un ADD/REMOVE pero me parece que son programas propios de gnome o kde.

---

### Post by Vero1 on 2007-09-14
Hola nico,

Bueno yo tengo un "poco" mas de 20 años jeje.

Mi problema es que no sé qué es lo que puedo borrar y que no, hablando de lo que NO son programas.

Los Tutoriales son bastante complicados y la mayoría en inglés(porque viene mezclado y no sé por qué)

Justamente voy a enviar un post sobre este punto.

De todos modos, a vos gracias.

saludos

---

### Post by Vero1 on 2007-09-15
> **LaHire said:**
> Yo no soy marianom!, aunq si queres darme un @ubuntu yo no tengo problema, no?

y siempre, aunq no soy vocero ni nada por el estilo, la comunidad esta para ayudar siempre :), un placer ayudarte! xD

Marian...no, LaHire :P

Hola La Hire:)

Te molesto nuevamente.
Despues de haber corrido el autoclean y autoremove, veo que me ha borrado escasos Kb...

Ahora me pregunto.
Cuando busco en Art por elemplo Backgrounds o cualquier otra cosa, sale una ventana diciendo download y baja todo lo que hay.
Yo elijo lo que quiero y lo bajo, pero todo el resto que se descargó aunque no se instaló, dónde va a parar? Hay algun chaché? Si es así, desde donde se borra, porque pienso que allí debe haber unos cuantos megas o gigas.
Qué opinás?

Gracias y saludos

---

### Post by Montsegur87 on 2007-09-15
> **Vero1 said:**
> Hola Montsegur87,

Hasta sudo deborphan todo bien, me refiero que saca un informe.
Ahora, las letras a b y c qué significan?
Intento ponerlas pero dice que orden no encontrada.
Cómo es?
Qué sigue despues de sudo deborphan y antes de sudo apt-get, etc?
Gracias

Fue un ejemplo , copiame lo que te muestra el comando deborphan.

---

### Post by Vero1 on 2007-09-16
Hola Montesegur 87,

Ya se descubrió por qué me falta espacio. Tengo 32 Gib sin asignar...
Éso pasó porque seguramente hice algo mal en la instalación.

En el chat me sugirieron reinstalar Ubuntu, con la ayuda en línea de la persona que descubrió la falla, así que te agradezco tu interés pero voy a reinstalar.

saludos:)

---

### Post by Montsegur87 on 2007-09-16
me parece medio al **** reinstalar, podes bootear con el Live CD , redimensionar tu particion donde tenes Ubuntu (supono que el espacio no asignado es contiguo a tu particion) y voila.

---

### Post by Vero1 on 2007-09-16
Hola de nuevo,

Voy a tratar de que veas las particiones a ver qué opinás.
ImageShack me lo rechaza porque dice que no es soportado.
Veo como hago.
No puedo, bueno la información aparece así:

sin asignar                                     32,59 Gib
/dev/hda2/Linux Swap                 957 Mib
/dev/hda1/ ext3                             4.66 Gib

en éste orden.

Datos sacados de gparted.

---

### Post by Montsegur87 on 2007-09-16
por lo que veo ahi tenes 1 solo disco rigido , con 2 particiones y espacio sin asignar , correcto?

Lo que podes hacer es bootear con el livecd y abrir el gparted. Desmontas las particiones hda1 y hda2 , haces un resize de la particion hda1 hasta el espacion deseado.

Que puede pasar? Supongamos que las particiones hda1 y hda2 son contiguas , lo que vas a tener que hacer es mover la particion de swap (hda2) al final del rigido ( graficamente , tirar la particion para la derecha en la opcion move , creo que se llama asi).
Siguiente paso , haces el resize de la particion hda1 y listo.

Suerte

---

### Post by Vero1 on 2007-09-16
Gracias Montsegur87,

Espero que me salga bien y no se presenten problemas.

Cuando lo haya hecho, te aviso.

saludos:)

---

### Post by Vero1 on 2007-09-17
Hola Montsegur87,

Bueno, no pude hacer nada.

El único que se puede mover y resize es ext3(hda1) el resto está deshabilitado.

No sé si tiene importancia pero gparted informa que

libparted: 1.7.l
automounting disabled...

Por otro lado en el chat me han sugerido mover al lugar que está vacío el swap pero no se puede.

Qué hago?

gracias

---

### Post by Montsegur87 on 2007-09-17
No me queda claro las particiones del disco

postea que tira el comando 

```
sudo fdisk -l
```

el mio es asi
```

andres@andres-desktop:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9824    78911248+  83  Linux
/dev/sda2            9825       10011     1502077+   5  Extended
/dev/sda5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+  83  Linux
/dev/sdb2           13055       26108   104856255   83  Linux
/dev/sdb3           26109       30401    34483522+  83  Linux
```

Igual , si estas apurada reinstala todo y listo.

---

### Post by LaHire on 2007-09-18
Perdon mi ignorancia, pero el que esté desabilitado esa opción en el gparted...es porq no se inició como SuperUsuario?

---

### Post by Montsegur87 on 2007-09-18
el gParted levanta aunque no seas root? no deberia.

---

### Post by Vero1 on 2007-09-18
> **Montsegur87 said:**
> No me queda claro las particiones del disco

postea que tira el comando 

```
sudo fdisk -l
```

el mio es asi
```

andres@andres-desktop:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9824    78911248+  83  Linux
/dev/sda2            9825       10011     1502077+   5  Extended
/dev/sda5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+  83  Linux
/dev/sdb2           13055       26108   104856255   83  Linux
/dev/sdb3           26109       30401    34483522+  83  Linux
```

Igual , si estas apurada reinstala todo y listo.

Montesegur87 me tira ésto:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9728    47423880    f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   7  HPFS/NTFS
/dev/sda6            7649        9688    16386268+   7  HPFS/NTFS

Disco /dev/hda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1            4391        4998     4883760   83  Linux
/dev/hda2            4269        4390      979965   82  Linux swap / Solaris
/dev/hda3             128        4268    33262582+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Claro porque hice mal la partición...

No, no estoy apurada y quiero hacerlo bien.

Pasa que la nueva partición está donde Windows...

El disco de Ubuntu tiene 40 Gb y el de Win 80.

Se puede hacer particionar de nuevo?

gracias

---

### Post by Vero1 on 2007-09-18
> **Montsegur87 said:**
> el gParted levanta aunque no seas root? no deberia.

Yo usé sudo gparted.

---

### Post by Vero1 on 2007-09-18
> **Vero1 said:**
> Montesegur87 me tira ésto:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9728    47423880    f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   7  HPFS/NTFS
/dev/sda6            7649        9688    16386268+   7  HPFS/NTFS

Disco /dev/hda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1            4391        4998     4883760   83  Linux
/dev/hda2            4269        4390      979965   82  Linux swap / Solaris
/dev/hda3             128        4268    33262582+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Claro porque hice mal la partición...

No, no estoy apurada y quiero hacerlo bien.

Pasa que la nueva partición está donde Windows...

El disco de Ubuntu tiene 40 Gb y el de Win 80.

Se puede hacer particionar de nuevo?

gracias

Aclaro que la partición que hice nueva es la que dice hda3.

---

### Post by Vero1 on 2007-09-18
Ahora, quisiera hacer una pregunta.

Si tengo instalado Ubuntu por qué hay que usar el LiveCD para redimensionar? No se puede directamente desde mi instalación con gparted?

---

### Post by Mauro22 on 2007-09-18
Tenes que usar el LiveCD si o si, de esta forma el disco duro, donde tenes instalado el Ubuntu, no se monta.


Si vos arrancas normal, no podes usar el gparted, porque el disco esta montado -en uso-. y no te deja hacer nada.

---

### Post by Montsegur87 on 2007-09-18
> **Vero1 said:**
> Ahora, quisiera hacer una pregunta.

Si tengo instalado Ubuntu por qué hay que usar el LiveCD para redimensionar? No se puede directamente desde mi instalación con gparted?
por una cuestion de seguridad. Cuando entras a ubuntu se montan las particiones. Modificar las particiones cuando estan montadas puede llevar a que pierdas datos. Entonces , por precaucion se bootea con el liveCD que no necesita de las particiones montadas para andar y ahi se modifica la estructura.

Modificar las particiones no es una tarea habitual , asi que no te hagas drama que vas a tener que hacer esto cada 2 por 3

---

### Post by Vero1 on 2007-09-18
> **Mauro22 said:**
> Tenes que usar el LiveCD si o si, de esta forma el disco duro, donde tenes instalado el Ubuntu, no se monta.


Si vos arrancas normal, no podes usar el gparted, porque el disco esta montado -en uso-. y no te deja hacer nada.

Gracias Mauro22:)

---

### Post by Vero1 on 2007-09-18
> **Montsegur87 said:**
> por una cuestion de seguridad. Cuando entras a ubuntu se montan las particiones. Modificar las particiones cuando estan montadas puede llevar a que pierdas datos. Entonces , por precaucion se bootea con el liveCD que no necesita de las particiones montadas para andar y ahi se modifica la estructura.

Modificar las particiones no es una tarea habitual , asi que no te hagas drama que vas a tener que hacer esto cada 2 por 3

Gracias Montsegur87.
Lo que no me queda claro es si puedo volver a particionar y si es así cómo hago para que el espacio que estaba libre se integre a lo que ya está en uso, porque cuando asigné ese espacio hizo una partición nueva que es hda3.

gracias

---

### Post by Montsegur87 on 2007-09-18
> **Vero1 said:**
> Gracias Montsegur87.
Lo que no me queda claro es si puedo volver a particionar y si es así cómo hago para que el espacio que estaba libre se integre a lo que ya está en uso, porque cuando asigné ese espacio hizo una partición nueva que es hda3.

gracias
Despues te contesto , me voy a la facu.

---

### Post by Vero1 on 2007-09-18
> **Montsegur87 said:**
> Despues te contesto , me voy a la facu.

ok gracias y que te vaya bien!

p.d.
qué estás estudiando?

---

### Post by Mauro22 on 2007-09-18
Si tenes espacio al lado de una particion usada, elegis la que esta en uso, y le das Resize, y la agrandas o achicas todo lo que quieras.

Ahora si elegis un espacio libre, podes, unicamente, crear particiones nuevas.

---

### Post by Vero1 on 2007-09-18
Mauro22,

originalmente la cosa era así:

En primer lugar había un espacio vacío de 32 Gb
Despues venía Swap 
y al último ext3

Yo hubiera querido que el espacio vacío se integrara a ext3 pero se creó la partición nueva.

En este momento el gparted dice:

Espacio sin asignar....
/dev/hda3(partición nueva)ext3
 /dev/hda2/(swap)
 /dev/hda1(ext3)pero tambien tiene una barra /

puedo eliminar hda3 y hda2(swap) redimensionar hda1 y luego crear swap nuevamente?

---

### Post by Mauro22 on 2007-09-18
Claro, borra la nueva que hiciste, (hda3), borra la swap y deja la ext3 donde tenes ubuntu.


Entonces de esto:

|-------hda3 32GB---------||-------Swap--------||-------Ubuntu---------|

Pasas a esto:

|-------------Libre 32Gb + Swap-----------------||-------ubuntu---------|


Ok?

Despues seleccionas ubuntu, y haces un risize para adelante, y sacas un poco de atras, si queres swap:

|-------------------------------------ubuntu----------------------||--Swap-|


Aplicar y listo

Se entiende??

---

### Post by Vero1 on 2007-09-18
Vos te referis a ubuntu como ext3 con la barrita /?

---

### Post by Mauro22 on 2007-09-18
la extendida 3 con la /, es la que tiene instalado ubuntu, esa es la que NO  tenes que borrar, sino la que tenes que agrandar, señalada como "ubuntu" en los graficos que te hice.

hda3 = la ultima nueva que hiciste, que antes era espacio sin asignar
swap = swap 
ubuntu = /, o sea la particion donde esta instalado ubuntu

---

### Post by Vero1 on 2007-09-18
Mauro, lo de no borrar ubuntu estaba claro, solamente quería aclaracion sobre si te referías a ext3 como ubuntu:)

Bueno, veo si mañana lo intento.

Gracias por todo.

---

### Post by Vero1 on 2007-09-20
Hola Mauro22,

Estoy sin Swap. No hay forma de que me acepte lo que le pongo.

Me dice que tengo que crear un espacio vacío(será para swap), pero cómo se crea un espacio vacío:confused:

saludos

---

### Post by Mauro22 on 2007-09-20
La Swap es opcional, podes crearla como no. Y a veces Ubuntu no usa la swap, si alcanza con la RAM.


Y eso, de que te diga, crear un espacio vacio es medio absurdo. Ya que un espacio sin formato es igual a nada. 


De ultima, si tenes buena cantidad de ram, no hagas la swap

---

### Post by Vero1 on 2007-09-20
Hola Mauro22,

Bueno te diré que al fin pude crear Swap, no sé cómo pero me lo aceptó  
y ocupé el espacio vacío tambien.
Es cierto que no lo pude integrar a lo que ya tenía, pero se creó como
hda3.
Ahora no sé cuál es la situación en realidad.
En la actual particion hay libres unos 2 Gib.
Qué va a pasar cuando allí no quede nada?
Se va a usar la nueva partición?
Perdoná tanta lata pero sos el que mas me está ayudando:)
En el chat me dijeron unas cuantas pavadas con respecto a Swap.
Que no voy a poder bootear mas por ejemplo...

gracias Mauro

---

### Post by Vero1 on 2007-09-21
> **Vero1 said:**
> Hola Mauro22,

Bueno te diré que al fin pude crear Swap, no sé cómo pero me lo aceptó  
y ocupé el espacio vacío tambien.
Es cierto que no lo pude integrar a lo que ya tenía, pero se creó como
hda3.
Ahora no sé cuál es la situación en realidad.
En la actual particion hay libres unos 2 Gib.
Qué va a pasar cuando allí no quede nada?
Se va a usar la nueva partición?
Perdoná tanta lata pero sos el que mas me está ayudando:)
En el chat me dijeron unas cuantas pavadas con respecto a Swap.
Que no voy a poder bootear mas por ejemplo...

gracias Mauro

Ahora hay algo que me preocupa.
Cuando corro df no aparece para nada la nueva partición y en baobab tampoco...

---

### Post by Montsegur87 on 2007-09-21
> **Vero1 said:**
> En el chat me dijeron unas cuantas pavadas con respecto a Swap.
Que no voy a poder bootear mas por ejemplo...
Cuack

---

### Post by Vero1 on 2007-09-21
Montsegur87, te volviste un patito?:)

Una pregunta:

El espacio que tenía vacío y que ya no lo está porque creó una nueva partición, resulta que en sus propiedades dice que NO está montado, motivo por el cual creo que no se visualiza en ningun lado.

Sabés cómo se puede montar? Porque la opción que tiene(en gris) es desmontar...

gracias

---

### Post by Mauro22 on 2007-09-21
Antes que nada, no te salio bien la edicion de particiones, porque arriba dices que en la actual te quedan 2 Gb, y que se te formò hda3.
Tendrias que volver a editar las particiones para que quede como queres, porque si se llena esa particion actual no va a empezar a usar la otra. 
Lo que podes hacer, es empezar a usar hda3 para meter los datos, dejando los 2GB actuales para paquetes.


Para montar podes usar:

vas a la consola y pones:

```
sudo gedit /etc/fstab
```

Al final del todo, pones:

si la particion es fat:
```

/dev/hdxx /montaje vfat iocharset=utf8,umask=000 0 0
```

si la particion es ntfs:

```
/dev/hdxx /montaje ntfs nls=utf8,umask=0222 0 0
```

En cualquier caso, hdxx, representa el disco, suplantando las xx por numero de disco y particion, ejemplo hda3
y /montaje, reemplazalo por el punto de montaje que quieras, ejemplo /home/mi_usuario/mi disco hda3

guardas los cambios, y volves a montar todo con:

```
sudo mount -a
```

---

### Post by Vero1 on 2007-09-21
Mauro,

Se aclaró el problema en el chat.
Pasa que la nueva partición no está montada.
Me dieron las instrucciones ya para hacer el trabajo.
Hoy no lo voy a hacer porque tengo la cabeza que parece un zapallo.
Te agradezco por tus datos.
Si me sale bien pongo Solved(espero que sí)

Gracias por todo.

---

### Post by Montsegur87 on 2007-09-22
> **Vero1 said:**
> Montsegur87, te volviste un patito?:)
Todavia no , pero pronto. Me parecio chistoso el comentario "el swap te rompe todo".

---

### Post by Vero1 on 2007-09-22
Pues te diré que a mi no me tranquiliza mucho porque si te dicen cualquier verdura...

Por ejemplo, 3 versiones diferentes de como montar una partición.

Uno que se olvidó de dar un dato...

En fin, espero me salga bien.

saludos:)

---

### Post by Mister X on 2007-09-22
> **Vero1 said:**
> Pues te diré que a mi no me tranquiliza mucho porque si te dicen cualquier verdura...

Por ejemplo, 3 versiones diferentes de como montar una partición.

Uno que se olvidó de dar un dato...

En fin, espero me salga bien.

saludos:)

si, es cierto, en esos casos no viene mal pegarle una leida al manual y te sacas todas las dudas...

```
man mount
```

saludos

---

### Post by Vero1 on 2007-09-22
Muchas gracias Mister X, lo veré.

---

### Post by Montsegur87 on 2007-09-22
Cuando modifiques las particiones y los montajes/mounts , para testear que no tengas nada mal configurado proba

```
sudo mount -a
```

Si te tira algun mensaje es que tenes algun error (el mensaje mismo te lo explica).

En cuanto al tema de la informacion a medias guiate por foros con muchos usuarios , si alguien te manda fruta generalmente hay otros 20 que te dicen que se mando cualquiera

---

### Post by Vero1 on 2007-09-22
ok muchas gracias. Cuando haga el trabajito te informo de los resultados.
En cuanto a lo que decís de los foros, actualmente estoy en 2. Argentina y España y tenés razón, se corrigen unos a otros.

La cosa es llegar a una buena definición de lo que hay que hacer.


saludos:)

---

### Post by Vero1 on 2007-09-23
Hola Montesegur87,

Hice la prueba que me indicaste y me dice ésto

mount: el punto de montaje /media/Veronica2 no existe


cómo interpreto ésto? porque si corro df me dice ésto:

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hda1              4806936   2639256   1923492  58% /
varrun                  257824       220    257604   1% /var/run
varlock                 257824         0    257824   0% /var/lock
procbususb              257824       112    257712   1% /proc/bus/usb
udev                    257824       112    257712   1% /dev
devshm                  257824         0    257824   0% /dev/shm
lrm                     257824     33788    224036  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             30716248  13616596  17099652  45% /media/sda1
/dev/sda5             30716248   2221736  28494512   8% /media/sda5
/dev/sda6             16386268     66752  16319516   1% /media/sda6
/dev/hda3             33262084    180240  31392208   1% /media/veronica2

---

### Post by Hei Ku on 2007-09-23
la carpeta /media/Veronica2 esta creada?
porque el montaje lo tenes que hacer en una carpeta que ya esta creada, no se arma en el momento del montaje. Desde ya que tiene que ser una carpeta vacia.

---

### Post by Vero1 on 2007-09-23
No Hei Ku, no me han dicho de crear ninguna carpeta.
Le puse Veronica2 porque no me aceptaba Veronica nada mas, ya que estaba creada.

Puedo crearla ahora y si es así cómo se hace?

gracias

---

### Post by Mauro22 on 2007-09-23
para crear la carpeta necesitas tener permisos de superusuario. Para ello, abris la consola y pones:

```
sudo mkdir /media/veronica2
```

Dale enter y te pide el password, lo pones y listo.

Si queres fijarte si te salio, solo pones:

```
cd /media/veronica2
```

si no hay error, te salió!

---

### Post by Vero1 on 2007-09-23
Hola Mauro22,

Pero no voy a hacer lío, porque presuntamente ya se montó esta partición. Fijate en lo que le mandé a Montsegur87.

Al final figura hda3 /media/ Veronica2. Esta no es la carpeta?

Porque yo ya hice un mkdir /media/Veronica2 y luego mount /dev/Veronica2 -t ext3.

---

### Post by Mauro22 on 2007-09-23
Podes leer y escribir en esa carpeta??
Se monta al inicio, o tenes que hacerlo a mano??

---

### Post by Vero1 on 2007-09-23
En el escritorio tengo una sola carpeta y es de Veronica.

Veronica2 no existe.

Además si veo en Equipo aparece Veronica2 pero está entre las particiones de Windows que son sda y no entre hda, aunque dice hda3.

No sé si todo ésto te aclara algo.

---

### Post by Mauro22 on 2007-09-23
si haces 

```
cd /media/veronica2
```

en la consola y despues pedis un listado con 

```
ls
```



que te sale?

---

### Post by Vero1 on 2007-09-23
bash: cd: /media/Veronica2: No existe el fichero ó directorio

---

### Post by Mauro22 on 2007-09-23
> **Vero1 said:**
> Hola Montesegur87,

Hice la prueba que me indicaste y me dice ésto

mount: el punto de montaje /media/Veronica2 no existe


cómo interpreto ésto? porque si corro df me dice ésto:

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hda1              4806936   2639256   1923492  58% /
varrun                  257824       220    257604   1% /var/run
varlock                 257824         0    257824   0% /var/lock
procbususb              257824       112    257712   1% /proc/bus/usb
udev                    257824       112    257712   1% /dev
devshm                  257824         0    257824   0% /dev/shm
lrm                     257824     33788    224036  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             30716248  13616596  17099652  45% /media/sda1
/dev/sda5             30716248   2221736  28494512   8% /media/sda5
/dev/sda6             16386268     66752  16319516   1% /media/sda6
/dev/hda3             33262084    180240  31392208   1% /media/veronica2


Fijate que ahi dice /media/veronica2

y ahora pones

bash: cd: /media/Veronica2: No existe el fichero ó directorio


Para linux, veronica2 y Veronica2, son carpetas distintas...

por lo tanto podes tener veronica2, con el disco montado.
Pero al hacer cd /media/Veronica2, te dice q no existe.


Chequea siempre las mayusculas y minusculas. trata de acceder a la que te tiró el "df", o sea veronica2, en minusculas.

---

### Post by Vero1 on 2007-09-23
veronica@veradri-desktop:/media/veronica2$ ls
lost+found
veronica@veradri-desktop:/media/veronica2$

---

### Post by Mauro22 on 2007-09-23
o sea que en /media/veronica2 esta montada la particion hda3.

si puso la carpeta lost+found, es porque esa particion esta en formato ext2 o ext3.
Asi que la podras usar con linux sin problemas...



Pero al estar separada de la particion donde esta ubuntu, podrias usar la hda3, como particion para datos y no sobrecargar la particion del sistema

---

### Post by Vero1 on 2007-09-23
Mauro, dos cosas.
Nunca formateè en ext2.

La partición hda3 tiene 32 Gb y la del sistema tiene libres 2 Gb.

La idea era poder integrar esos 32 Gb a los 2 Gb pero no se pudo.

Mi idea era utilizar la nueva partición cuando no me quedara mas espacio en hda...

---

### Post by Mauro22 on 2007-09-23
*Para juntar las dos particiones, tenes que 

  - iniciar gparted desde el live cd
  - si las particiones aparecen con un candadito, clic derecho desmontar
  - borrar la hda3, 
  - seleccionar la que tiene ubuntu, dale resize o redimensionar
  - en el grafico la estiras todo lo que de.
  - Aplicar, y listo


* Si queres usarla asi, para guardar datos va joya!!

* Si queres saber en que formato esta, hace:

```
df -T
```

"Con la T mayuscula"

Ahi te sale que tipo de formato tiene, ext2, ext3, etc etc

Salu2

---

### Post by Vero1 on 2007-09-23
Mauro,

En un principio traté de redimensionar la partición del sistema pero no me lo permitió.
Se podía redimensionar la partición del Swap nada mas.
No sé ahora que está todo particionado si me lo va a permitir.

Todo está formateado como ext3.

Bueno, mañana veré lo del CD a ver qué puedo hacer.

Gracias, te informaré.

saludos:)

---

### Post by Mauro22 on 2007-09-23
[img]http://www.pic2up.net/SBQCCbU.jpg[/img]

OK


En la imagen ves los candados que te estaba contando. ??


Eso significa q esta montado.

Graficamente podes hacer de todo con la particion, pero si esta montado, no podes aplicar los cambios.

Por eso, hace clic derecho desmontar

Suerte!

---

### Post by Vero1 on 2007-09-23
[[IMG]http://img388.imageshack.us/img388/7943/gpartedxf6.th.png[/IMG]](http://img388.imageshack.us/my.php?image=gpartedxf6.png)

Así está el mío.

---

### Post by Mauro22 on 2007-09-24
Lo que tenes que hacer, es:

1) desmontar todas las particiones y desactivar el intercambio.

2) Borar hda3 (veo que tenes 700mb usados)

3) seleccionas hda1, y haces:

    * clic en mover, y en el grafico que te aparece, moves la particion hacia la izquierda y la agrandas hacia la derecha.

    o

    * haces clic en mover/redimensionar y la agrandas hacia la izquierda


De forma que te queda la swap adelante y el resto todo es hda1

---

### Post by Vero1 on 2007-09-24
Mauro, justamente acabo de probar con el LiveCD.

No me aparece el gráfico para nada, por lo que no pude hacer nada, solamente desmonté hda3 y otra vez quedó vacío.

Cómo hago aparecer el gráfico?

saludos

---

### Post by Mauro22 on 2007-09-24
cuando elegis una particion desmontada (que no tenga el candado) se te habilita el boton de Mover/Redimensionar.

Si haces clic en ese boton te aparece algo como esto 

[img]http://www.pic2up.net/SxQJBOb.png[/img]



Las flechas negras en las puntas del grafico, significa que podes mover la particion, achicandola o agrandandola.

Al borra la hda3, y hacer lo de arriba con la hda1, tendrias que tenes los 32Gb vacios delanta de la particion, entonces, solo arrastras la flecha negra de la izquierda, hasta la izquierda.


Se entiende? sino avisame!

---

### Post by Vero1 on 2007-09-24
Claro yo esperaba ver otro gráfico que me apareció una vez...

Creo haber entendido Mauro.

Despues de almorzar probaré y te digo.

Gracias

---

### Post by Vero1 on 2007-09-24
Mauro mas problemas.

Primero: no me aparecen 2 flechas si no 1 sola sobre el lado derecho. Al llevarla hacia la izquierda llega hasta 16Gib. El resto queda libre de nuevo. O sea no puedo anexar todo el espacio de los 32 Gib.

Segundo: Al sacar el CD sale en una pantalla negra:
File system check failed

Hay un log en var/log/fsck/checkfs que pide se repare manualmente.
Traté de correrlo con sudo y sin sudo y no va.

tambien dice

fsck died with exit status 8.

Hace mención tambien de que veronica2 no está montado.

En fin creo que primero hay que arreglar la partición vacía y luego ver el resto. Qué opinás?

saludos

---

### Post by Vero1 on 2007-09-24
Ahora gparted está así:

[[IMG]http://img526.imageshack.us/img526/6762/pantallazonq8.th.png[/IMG]](http://img526.imageshack.us/my.php?image=pantallazonq8.png)

---

### Post by Mauro22 on 2007-09-24
Me parece que tendras que desmontar y borrar la swap.

Ahi te quedaria todo libre, y a lo ultimo la hda1.



Intenta ahi, desmontar hda1 y agrandarla hacia la izquierda todo lo que de.
y Fijate si podes sacarle un poco del lado derecho para crear nuevamente la swap.


No saques nunca el cd, hasta no haber terminado de aplicar los cambios. A veces aparece un signo de exclamacion, pero sale bien.

Avisame, cualquier cosita!

---

### Post by Vero1 on 2007-09-24
Mauro la cosa está desastrosa.

Me quedé sin swap pero aparte no se puede hacer nada con hda1 porque no permite mas de 4 Gb como máximo y la mitad ya está ocupada con todo lo que instalé.

Sigue sacando un informe sobre que no puede hacer el chequeo de los archivos. Que vea /var/log/fsck/checkfs y que repare manualmente

Tambien informa: fsck died with exit status 8.
Run fsck manually (sin -a y -p).

Ahora, ésto que pide que se haga, se hace desde el CD o del disco y desde Terminal? Tenés idea?

Tampoco sé qué es lo que debo reparar...

---

### Post by Mauro22 on 2007-09-24
La verdad es que es rarisimo que no te deje agrandar la particion.


De ultima volve a crear hda3, y una swap y listo


Con respecto al comando, se debe correr en consola.



La verdad que me llama poderosamente la atencion, que no te deje expandir la particion :mad:

---

### Post by Vero1 on 2007-09-24
Bueno veré qué puedo hacer.

Creé una partición para el espacio vacío pero no me lo acepta porque había hecho antes un directorio como Veronica2 y no me acepta ahora veronica2.

Si lo sabés me decís cómo se hace para eliminar un directorio?

Para crearlo es mkdir y para eliminarlo?

Tal vez si lo elimino puedo crear esa partición y crearla de nuevo.

De todas formas no puedo hacer nada hasta no arreglar el entuerto porque no acepta nada.

---

### Post by Vero1 on 2007-09-24
Bueno Mauro,

No te preocupes que ya encontré el comando para eliminar un directorio.

Creé el Swap y no tuve mas remedio que crear un nuevo directorio para hda2(antes espacio sin ocupar).

Espero no tener problemas porque no hice ningun arreglo...

saludos y gracias por tu tiempo.

---

### Post by faktorqm on 2007-09-25
verito, como te va? perdoname que no te di mucha bola.
que paso con las particiones? contame que no tengo tiempo para leer no se cuantas paginas de lo mismo. bajaste el gparted? antes que nada. si necesitas documentacion, preguntame que hoy justamente investigue mucho sobre el tema. salu2!!

---

### Post by Vero1 on 2007-09-25
Hola faktorqm, cómo estas?

Pues las particiones un lío pero ahora ya está.

Solamente tendría que eliminar un montaje, cuyo directorio no está pero me sale una pantalla negra cuando booteo, diciendo que tal montaje no existe...

Ahora voy a sacar un nuevo thread porque hay algo gordo que no sé como arreglar.

Si sabes algo de como eliminar este montaje, bueno, dejo mis oidos abiertos.

gracias y saludos

---

### Post by faktorqm on 2007-09-25
hace una cosa, posteame primero esta instruccion en un terminal:

"cat /etc/fstab >> conf.txt" (sin comillas ;))

y despues "gedit conf.txt" y me copias y me pegas el contenido, aca o en el nuevo. salu2!!

---

### Post by Vero1 on 2007-09-25
El primer comando no responde.

En el segundo, al final, me habían hecho poner lo de Veronica2 y ya lo borré y grabé lo que quedó.

Ahora voy a probar de nuevo el boot y te cuento.

---

### Post by Vero1 on 2007-09-25
No surtió efecto. Sigue ahí. Por Pastebin te estoy enviando el resultado de gedit.

Está bajo el número 38570

Tambien sigue la pantalla negra cuando booteo.

gracias

---

### Post by Vero1 on 2007-09-25
Hola faktorqm,

Ya está solucionado. Eliminé la última línea de fstb que es lo que provocaba el problema y ya no me sale la pantalla negra.

Lo único es que hda2 no estaba montado y lo monté desde Equipo.
Quedó en media/disk. Está bien o hay que cambiar de media?

Gracias

---

### Post by faktorqm on 2007-09-25
lo podes montar donde se te ocurra. ;) 
si queres que se te monte al inicio, agregalo al fstab. salu2!!

---

### Post by Vero1 on 2007-09-25
ok gracias faktorqm.

Hasta otra:)

---

### Post by Vero1 on 2007-09-26
faktorqm,

De vuelta antes de lo esperado:(

Se me ocurrió ver gparted y la partición que creí haber montado, aparece sin montar(la monté desde Equipo(Escritorio) y el swap tampoco está habilitado...

Tengo que montarla desde consola previa creación de una carpeta no?

Por ejemplo:sudo  mkdir/media/veronica2(carpeta)

Despues:

sudo mount/dev/hda2/media/veronica2 -t ext 3

Estaría bien así?

gracias y saludos

---

### Post by faktorqm on 2007-09-28
hola, si, los comandos serian:

```
sudo mkdir /media/veronica2
```

y dopo:

```
sudo mount -t ext3 /dev/hda2 /media/veronica2
```

y listo. Si lo queres agregar en el fstab para no tener que hacer esto cada vez que arrancas la pc, es algo asi:

```
/dev/hda2    /media/veronica2    ext3    defaults    0    0
```

weno, espero que te haya servido. salu2!!!!!

---

### Post by Vero1 on 2007-09-28
Gracias faktorqm, ya lo hice así y por lo menos quedó montado y lo agregué al fstab y no se desmonta en el reboot.

saludos

---

### Post by faktorqm on 2007-09-28
grosssaaaaaaaaaaa salu2!

---

### Post by Vero1 on 2007-09-28
No tanto faktorqm:)

Cuando se me arregla algo se me desarregla otra cosa...

En fin. Será para no aburrirnos? ;)

gracias

---

### Post by vk-cdg on 2007-09-28
Si, tal cual, es definitivamente para no aburrirnos o porque somos mazoquistas.

En la PC del laburo, ya llevo reinstalado Ubuntu como 3 veces (por romper y no saber como solucionarlo sin reinstalar) y otros tantos remiendos luego de que algo dejase de andar. Tanto rompí los cocos que un día llego al trabajo y en mi escritorio tenía un cartel pegado que dice "Si anda... NO LO TOQUES".

En fin, concuerdo con vos que es para no aburrirnos. :)

---

### Post by Vero1 on 2007-09-28
Tratá de hacer caso:popcorn:

---

