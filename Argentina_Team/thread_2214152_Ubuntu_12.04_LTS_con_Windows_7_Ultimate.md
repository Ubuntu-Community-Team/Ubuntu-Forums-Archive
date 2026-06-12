---
title: "Ubuntu 12.04 LTS con Windows 7 Ultimate"
date: 2014-03-30
forum: Argentina Team
---

### Post by Verry on 2014-03-30
En una PC de escritorio tengo dos discos SATA de 160 GB cada uno. En el primero instalado Windows 7 Ultimate, y en el segundo, sin SO, he instalado Ubuntu 12.04 LTS con la opción de Dual Boot (grub). Pero se me han desacomodado muchas cosas, como la red de windows y las conexiones de red.
Leyendo sugerencias sobre desistalación de Ubuntu encontré la siguiente opción, que detallo a continuación:

En una Terminal, ejecuté:
**Sudo fdisk -lu**
 
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x000daa8b
 
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   157047141    78523539+   7  HPFS/NTFS/exFAT
/dev/sda2       157051440   312576704    77762632+   7  HPFS/NTFS/exFAT
 
Disco /dev/sdb: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pista, 19929 cilindros, 320173056 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x19d919d8
 
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            2048   160617869    80307911    7  HPFS/NTFS/exFAT
/dev/sdb2       160617870   320159384    79770757+   5  Extendida
/dev/sdb5       160617933   313572734    76477401   83  Linux
/dev/sdb6       313572798   320159384     3293293+  82  Linux swap / Solaris

Supongo que el sda es mi disco Western Digital, donde está Windows 7 Ultimate.
El sdb es un Maxtor, sin SO, con una partición previa para Windows y el resto para Linux.

Mi necesidad es separar totalmente lo que hay en los dos discos, y que Grub no tome el control del equipo.
Sé iniciar el equipo con uno u otro, entrando al Setup, así que eso no es problema. Lo que deseo es que no compartan nada los SO.

Agradeceré toda información probada con éxito. Y que me informen por mail, cuando haya una respuesta. He mandado antes varias consultas pero no he recibido respuesta, o bien yo no sé buscarlas, ya que no reviso diariamente los foros.

Muchas gracias de antemano.

PD: en la página del Team Argentina figuro como miembro "propuesto". No sé loq ue significa, será que debo presentar algo?

Nombre completo: José Luis Verrastro
Nick: Verry.

---

### Post by gmunioz on 2014-04-02
Hola José Luis: en general los foros, y este no se aparta de la norma, son un sitio de reunión de usuarios, en este caso de Ubuntu, donde planteados inconvenientes y/o dudas, los usuarios, no técnicos ni desarrolladores de Ubuntu, proponemos soluciones conforme nuestra experiencia.
Estas soluciones no son personalizadas ni se dan por mail, ya que la intención no es intentar solucionar solo lo planteado por un usuario, sino que quede registro y pueda ser utilizado por todos aquellos que puedan presentarlo.
Hechas estas aclaraciones, y al respecto de lo que planteas, en general se acepta que para utilizar más de un sistema operativo en un ordenador, se use un gestor de arranque. Sea este el Grub utilizado por Ubuntu, Lilo, Burg, Gag, etc.. El gestor de arranque inicia el ordenador y cede el control al sistema operativo que es quien realmente, a partir de ese momento tiene el control.
Siempre que se utilicen más e un sistema operativo es necesario un gestor de arranque, a menos que la selección se haga por hardware, lo que no es práctico, procediendo en cada inicio a desconectar el disco del operativo a descartar.
Respecto a compartir entre los sistemas operativos de un ordenador, los operativos de Microsoft, son incapaces de acceder a los sistemas de archivos de Gnu/Linux, si estos son perfectamente capaces de acceder a los sistemas de archivo de Microsoft, para impedirlo basta con desmontarlos.
Terminadas estas generalizaciones, según mi experiencia y lo que interpreto que planteas, tienes estas opciones para evitar el uso del Grub:
1- Instalas Ubuntu en el disco Maxtor, previa desconexión del Western Digital, con el Grub en su mbr. Cada vez que quieras iniciar con Ubuntu deberás desconectar el disco Western Digital. Cada vez que quieras iniciar con Windows, deberás conectarlo, sin necesidad de desconectar el Maxtor, dado que el Grub solo inicia desde el mbr de /dev/sda, y estando los dos conectados /dev/sda es el Western Digital.
2- Instalas Ubuntu con el Grub instalado en su partición / y para iniciar modificas el gestor de arranque de Windows para que tenga una opción de inicio con Ubuntu.
Una vez instalado Ubuntu con el Grub en su partición /, al reiniciar naturalmente inicia Windows 7.
Entonces descarga e instala EasyBCD
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
Inicia EasyBCD, que es free para uso no comercial.
Busca  Add New Entry -> Operating Systems -> Linux/BSD:
        > Type: GRUB 2
        Name: Ubuntu
        Device: (Automatically configured)
Al terminar ve a &#8220;View Settings&#8221;
Y deberías ver algo similar a lo siguiente:
        > Entry #2
        Name: Ubuntu
        BCD ID: {1d486d61-64cc-12a5-7d94-af2f5df01535}
        Drive: C:\
        Bootloader Path: \NST\AutoNeoGrub0.mbr
Y al reiniciar en el menu de inicio deberás tener a &#8220;Windows 7&#8243; y &#8220;Ubuntu&#8221;.

---

### Post by gmunioz on 2014-04-02
Otro procedimiento para iniciar con Windows 7 sería:
Luego una vez reinstalado Ubuntu, reiniciar una sesión live, abrir una terminal y ejecutar:
> sudo su
mount /dev/sda1 /mnt 
dd if=/dev/sdb5 of=/mnt/linux.bin bs=512 count=1
Con esto lo que haces es montar C:\ donde está Windows (/dev/sda1 en /mnt del live), y copiar el sector de arranque de / (dev/sdb5) en la raiz de C:\, es decir en el disco donde esta instalado Windows.
Luego desde Windows, previo convertirte en administrador:
Inicio --- Todos los programas -- Accesorios -- Símbolo del sistema --- Ejecutar como administrador -- bcdedit /create /d &#8220;Linux&#8221; /application bootsector
Bcedit dará un identificador alfanumérico de esta entrada, ID.
Luego especifica qué partición contiene una copia del archivo linux.bin
bcdedit /set (el ID informado) device partition=c:
Ahora escribes la ruta al archivo
bcdedit /set (el ID informado) path \linux.bin
bcdedit /displayorder (el ID informado) /addlast
bcdedit /timeout 30
Y ya tendrías en el menu de Windows la opción para iniciar Ubuntu.

---

### Post by Verry on 2014-06-01
Salud, Gabriel. Muchas gracias por tu ayuda y colaboración. Todo me ha resultado muy útil, pero he desechado la idea que tenía de tener los dos sistemas operativos  separados e independientes.
Entretanto, durante abril y mayo, no recibí notificaciones de tus instrucciones, por tener problemas de conexión a internet, y también con la configuración de un router TP-LINK que administra mi red Wi-Fi. En suma, ya pude instalar Ubuntu, en su versión 14.04, y también funciona mi red, con acceso a impresora Wi-Fi, que era lo más importante para mí.
Ahora, mi necesidad es migrar bases de datos personales, que he desarrollado en Basic y en Pascal hace mucho tiempo. Tengo instalado LibreOffice Base, y deseo me asesores donde acudir (en qué foro, o subforo, para aprender lo que necesito para la migración. Mi idea es trabajar solo con software libre y con Ubuntu. También necesito me aclares cómo hacer para ser notificado cuando alguién me responda.
Mil gracias nuevamente, y quedo a tu disposición para lo que necesites de mí.

---

### Post by Verry on 2014-06-01
A propósito, cómo se hace para cerrar este hilo de conversación? Acepto sugerencias.

---

