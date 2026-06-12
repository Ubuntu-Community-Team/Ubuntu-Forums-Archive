---
title: "Zip 100 en Ubuntu Server 7.04"
date: 2007-11-10
forum: Argentina Team
---

### Post by Teno on 2007-11-10
Hola a todos, les comento, no se si a alguien de aqui le paso, pero me resulta imposible de creer esto:

Como hobby, tengo un servercito en casa, con Ubuntu Server 7.04...en un P III @ 667 mhz con 256 Mb RAM y dos HDD 20 gb.

Como suelo tener siempre hardware de la vieja escuela dando vueltas en casa, quise probar de poner un ZIP 100 paralelo...y lluvia de chanes... imposible...

Al parecer es un bug del kernel? La cuestion es que no lo puedo montar y punto. Asi que probe con un livecd de Ubuntu 6 y magicamente funciona de maravillas.

No pude encontrar nada en la net sobre la solucion del tema.

Mas info en:

[https://answers.launchpad.net/ubuntu/+source/hal/+question/14098](https://answers.launchpad.net/ubuntu/+source/hal/+question/14098)

Saluditos y espero que el link este bien posteado, si no, algun moderador me lo puede corregir?

---

### Post by User21 on 2007-11-10
Quizas algo de esto sirva de ayuda  (en ingles):

[HowTo: Iomega IDE/ATAPI ZIP drive]("http://ubuntuforums.org/showthread.php?t=29441&highlight=imm+module")

[IomegaZIP Drives in 6.06]("https://help.ubuntu.com/community/IomegaZIPDrive")  (quizas aprendes la mecanica y la apliques en 7.04. Atencion a lo de los modulos)

[ZIP Drives Mini HowTo]("http://www.tldp.org/HOWTO/ZIP-Drive.html")  

Como nunca use una de esas unidades, no puedo mas que remitirte alli. 
Por otro lado, te invito a instalar el paquete modconf:

sudo apt-get install modconf 

y para ejecutarlo :  sudo modconf

Luego intenta cargar los modulos que te parezcan apropiados para tu dispositivo:
Intenta los que hay en la clave kernel/drivers/scsi o danos mas info acerca de las especificaciones de tu drive!!!
Con el, puedes elegir y cargar modulos para Iomega, desde una interfase grafica, en consola. Una vez cargado el modulo, quizas lo detecte de una! Y recuerda agregar esos modulos al inicio!

---

### Post by Teno on 2007-11-11
Si, estuve chusmeando todos esos lugares, y unos cuantos foros mas sobre linux y sobre Debian/Ubuntu y no pude encontrar, por ahora, ninguna solucion.

Lo que mas me llama la atencion es que en Dapper 6.06 anda fantastico, solo tengo que cargar dos modulos, ppa y sg y te diria que en forma casi instantanea, te asigna el sda4 y lo usas fantastico, inclusive funciona hasta el eject.

Cosa de mandinga, o kilombo en los modulos/kernel

Voy a seguir investigando a ver que encuentro.

---

### Post by User21 on 2007-11-12
**Solo para tener todas las posibilidades contempladas:**
una vez que cargas los módulos en 7.04, el kernel detecta el dispositivo? porque si es asi, podes montarlo manualmente en alguna carpeta que hayas creado.
Quizás sos un usuario experimentado y yo aca explicándote estas cosas, pero me voy a tomar el esfuerzo igual:

sudo mount /dev/hda4 /home/usuario/Escritorio/TuCarpeta

donde hda4 seria como reconoce tu dispositivo! 

Si ya intentaste todo esto, pues, perdón por la redundancia! 
No olvides editar el /etc/modules para cargar los modulos desde el arranque! 

xD  Quiero hacerte funcionar ese maldito ZIP!

---

### Post by Teno on 2007-11-12
Si, bueno, mas o menos experimentado.

Efectivamente, veo que el modulo ppa detecta la unidad y todo, pero en un momento tira las siguientes lineas:

scsi 0:0:6:0: Direct-Access IOMEGA ZIP 100 K.05 PQ: 0 ANSI: 2
[152783.175629] scsi 0:0:6:0: Attached scsi generic sg0 type 0
[152803.332801] sd 0:0:6:0: scsi: Device offlined - not ready after error recovery
[152803.333789] sd 0:0:6:0: rejecting I/O to offline device
[152803.334440] sd 0:0:6:0: rejecting I/O to offline device
[152803.335085] sd 0:0:6:0: rejecting I/O to offline device
[152803.335736] sd 0:0:6:0: rejecting I/O to offline device
[152803.336362] sda : READ CAPACITY failed.
[152803.336369] sda : status=0, message=00, host=1, driver=00
[152803.336388] sda : sense not available.
[152803.337892] sd 0:0:6:0: rejecting I/O to offline device
[152803.338513] sda: Write Protect is off
[152803.338532] sda: Mode Sense: 00 00 00 00
[152803.339404] sd 0:0:6:0: rejecting I/O to offline device
[152803.340022] sda: asking for cache data failed
[152803.340041] sda: assuming drive cache: write through
[152803.342618] sd 0:0:6:0: Attached scsi removable disk sda

Inclusive probe con otro ZIP y pasa lo mismo.

Los modulos efectivamente los cargo en /etc/modules, en el orden en que indica en esas paginas que me pasaste (que ya las habia visitado antes de hacer este post, btw)

Lamentablemente el server no tiene X, asi que cualquier cosa grafica significaria meterle un monitor :)

Por otro lado, la notebook no tiene puerto paralelo, pero no me atrevo a pensar que funcionaria.

En estos dias estoy recibiendo un viejo server Dell PowerEdge y lo voy a poner ahi a ver si funca. La verdad, si no funciona, voy a meterle Dapper 6.06 server, pero como es todo por hobby, asi que veremos!!

Che, gracias !!!

---

