---
title: "Arranque dual ubuntu windows en distintos discos"
date: 2016-10-17
forum: Argentina Team
---

### Post by sebapagnu on 2016-10-17
Hola acabo de empzar con linux y elegi el ubuntu 16.04 lts para arrancar.
Tengo a demas un windows7 insalado en un disco sata y como consegui un  disco IDE aproveche para probar linux. El problema es que cuando hago  lainstalacion y le digo que me ponga para instalar junto a win7 no me  genera un arranque dual, es decir cuando reinio la pc solo arranca  ubuntu. 

yo creo que esto es por qu se instalo el grub en el IDE y al estar  seteado este como first boot en el bios directamnte arranca ese.

¿como puedo hacer para corregir el arranque dual con linux y windows? 

-Hasta ahora vi muchos tutos de como reparar el grub y hasta lo que  tengo en claro seria instalarlo en la particion de win7 y que el bios  botee desde ese disco. Pero no se si con eso haria cagada y me joderia  el arranque del mismo windows. 				

pd: Intente botear desde el disco donde tengo windows y solo arranca ubuntu aiuuuudaaaaa

---

### Post by mily2 on 2016-10-17
Hola, bienvenido:

1º. A la hora de instalar selecciona la última opción, la que te deja personalizar la instalación. Es la mejor opción. Ahí seleccionas la partición o particiones donde quieres que se instale Ubuntu (sobre esto tienes muchos tutoriales: lo ideal es crear varias: /usr, /opt, /var, /home y Swap. Esta última sí o sí es obligatoria, el resto las puedes englobar en una) y ahí puedes seleccionar donde se instalará el GRUB.

2º. Tal como describes el GRUB lo tienes en el IDE. Haz un update del GRUB desde la consola, pues debería reconocerte el Windows 7 (fíjate bien en lo que encuentra). No obstante puedes bootear antes de que cargue el MRB pulsando el F11 (consulta el manual de tu placa base por si es otra tecla).

3º. Lo ideal es meter los dos SO en el SATA por tema de velocidad y simplicidad. Puedes probar también a instalar el GRUB en el SATA como te dije en el punto primero. Eso te borrara el arranque del Windows; pero puedes cambiar el orden del arranque posteriormente editando el GRUB (hay bastantes tutoriales sobre ello) o si te da respeto puedes instalar el  grub customizer y hacerlo a golpe de click, si es que quieres que el Windows arranque el primero (también puedes modificar el tiempo de espera). Por otro lado el arranque de Windows 7 se puede recuperar. Yo he recuperado el del XP en alguna ocasión sin ningún problema (se consigue booteando el cd de instalación de Windows y haciendo un fixmbr desde la consola de reparación), imagino que el procedimiento sea parecido (por Internet habrá hasta vídeos por Youtube).

4º. Sobre la PD. Prueba a desconectar el IDE. Si no te arranca el Windows es que tienes el GRUB instalado en el SATA. Como te digo, haz siempre la instalación customizada para evitar sustos de aquí en adelante. Ahora lo que puedes hacer es arrancar Linux y actualizar el GRUB desde consola ( sudo update-grub2 o sudo update-grub). Debería reconocerte el Windows 7. En caso contrario instala la herramienta TestDisk desde la consola y ejecútala.

---

### Post by mily2 on 2016-10-17
Te voy a hacer un minitutorial para ejecutar TestDisk (seguramente tendrás que usarlo si el update no te soluciona nada):

Todo es desde la consola, se saca presionado Ctrl+Alt+t: 

1º. sudo apt-get install testdisk

2º. sudo testdisk
Verás la pantalla de inicio del programa. Ten en cuenta que esta aplicación la podrás manipular con las teclas direccionales (flechas) para elegir una opción, [Enter] para confirmar, y la
tecla [Q] para salir o ir hacia atrás. Selecciona la opción [No Log] y luego presiona [Enter].

3º. Elige el disco duro que contenga la partición de Windows 7, luego seleccionas la opción [Proceed] y presionas [Enter].

4º. Elige el tipo de tabla de particiones. Aquí sólo elige la opción [Intel].
Por si tienes dudas: esto se refiere al tipo de particiones, no al tipo de procesador.

5º. En la siguiente ventana eliges la opción [Advanced]

6º. Seleccionar la partición de inicio de Windows. Es la primera HPFS - NTFS, de 100 mb, pone: "Reservado para el sistema". No tiene pérdida. Luego verás otra HPFS - NTFS, que es la que contiene el resto de archivos de Windows 7.

 7º. En la siguiente ventana sólo elige la opción [BackupBS] y presiona [Enter].

8º. Luego verás una ventana pidiendo confirmación [Y/n], presiona la tecla Y para aceptar. Finalmente sólo presiona la tecla [Q] varias veces hasta salir de la aplicación Testdisk.

9º. Ejecuta el siguiente comando para que la configuración del GRUB tome los cambios hechos:
sudo update-grub2

10º. Reinicia y confirma que todo funcione correctamente, debieras poder ingresar a Windows 7 y también a Ubuntu.

---

### Post by sebapagnu on 2016-10-17
Sos un genio! gracias lo voy a probar.... 

pd: Probe con lo de actualizar el grub y nada, aparentemente se abra jodido el arranque de windows. asi que vere mas tarde de probar todo esto.

---

### Post by sebapagnu on 2016-10-18
aparentemente no me estaria detectando windows:

Se encontró una imagen linux: /boot/vmlinuz-4.4.0-43-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-43-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-31-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
hecho

---

### Post by sebapagnu on 2016-10-18
> **mily2 said:**
> 
 7º. En la siguiente ventana sólo elige la opción [BackupBS] y presiona [Enter].



aca solo me aparece "rebuildBS" en vez de "backupBS"  intento con eso y nada

---

### Post by mily2 on 2016-10-18
Tiene que ser backupBS para que funcione.

Recupera el arranque del Windows 7: [http://www.alebentelecom.es/servicios-informaticos/faqs/reparar-boot-de-arranque-windows-7](http://www.alebentelecom.es/servicios-informaticos/faqs/reparar-boot-de-arranque-windows-7)

Yo lo que haría sería salvar los datos en el IDE, o en DVDs si no te alcanza, bootear Ubuntu Live, formatear el SATA desde el Live usando Gparted (creas una partición NTFS para el Windows, y luego otras para el Linux), instalar windows 7 en el SATA y luego instalar Ubuntu en el SATA tal como te puse en el primer post (con el arranque en el SATA). Deja el IDE para almacenar archivos. Seguro que el Windows te agradece el formateo y Linux volará.

Si no estás muy convencido, una vez recuperado el arranque de Windows 7 puedes probar Ubuntu mediante WUBI[ https://help.ubuntu.com/community/Wubi]("https://help.ubuntu.com/community/Wubi"). Si lo instalas así, para no perder excesivo rendimiento desfragmenta el SATA antes (una vez vi un vídeo de una persona que redimensionaba el HD para sacar otra partición e instalaba ahí el WUBI para mejorar el rendimiento; pero ya puestos es preferible instalar en esa partición Ubuntu desde el Live).

También, recuperado el arranque del Windows, si no quieres tocar el SATA vuelve a instalar UBUNTU en el IDE como te dije en el primer post. Puedes desconectar el SATA para asegurate que no te modifique el MRB, si lo haces así haz luego update al GRUB, con el SATA conectado, a ver si te reconoce el Windows. Si no prueba a meterlo a mano editando GRUB. A las muy malas siempre puedes bootear con F11.

---

### Post by gmunioz on 2016-10-27
Sumimasen por la intromisión.
Mi sugerencia es que:
Desconectes el disco IDE, con Ubuntu si mal no leí e inicies con el SATA, si Windows 7 inicia sin problemas. significa que has instalado correctamente Ubuntu en el disco IDE sin perjudicar la instalación del disco SATA.
Conecta nuevamente el disco IDE e inicia con Ubuntu.
En Ubuntu abre una terminal y ejecuta en ella:
> exec sudo -i
nano /etc/grub.d/11_windows_seven

Y en la ventana que se abre de nano, pega o escribe las siguientes líneas:

    > #! /bin/sh -e
    cat << EOF
    menuentry "Windows 7" {
    set root=(hd1,1)
    chainloader +1
    }
    EOF

Donde:
hd1, corresponde a /dev/sdb el disco SATA con Windows cuando Ubuntu inicia del disco IDE, que siempre será /dev/sda
1, corresponde a la primera partición de ese disco, donde generalmente se instala la porción de inicio de Windows 7

Control + O, guarda el archivo. Control + X, cierra nano. Continua ejecutando en la terminal:
 
> chmod +x /etc/grub.d/11_windows_seven
update-grub

A partir de ahora tendría que aparecer Windows 7 en el menu del Grub.

---

### Post by jdesing on 2017-07-23
> **gmunioz said:**
> Sumimasen por la intromisión.
Mi sugerencia es que:
Desconectes el disco IDE, con Ubuntu si mal no leí e inicies con el SATA, si Windows 7 inicia sin problemas. significa que has instalado correctamente Ubuntu en el disco IDE sin perjudicar la instalación del disco SATA.
Conecta nuevamente el disco IDE e inicia con Ubuntu.
En Ubuntu abre una terminal y ejecuta en ella:


Y en la ventana que se abre de nano, pega o escribe las siguientes líneas:

    

Donde:
hd1, corresponde a /dev/sdb el disco SATA con Windows cuando Ubuntu inicia del disco IDE, que siempre será /dev/sda
1, corresponde a la primera partición de ese disco, donde generalmente se instala la porción de inicio de Windows 7

Control + O, guarda el archivo. Control + X, cierra nano. Continua ejecutando en la terminal:
 


A partir de ahora tendría que aparecer Windows 7 en el menu del Grub.

Hola, he seguido tus pasos y al menos ahora me sale el Grub al iniciar el sistema pero al seleccionar Windows me da un error. Yo tengo 2 Discus duros SATA, 1 para Windows y otro para Ubuntu.

Me podrías ayudar con la configuración del archivo?

---

