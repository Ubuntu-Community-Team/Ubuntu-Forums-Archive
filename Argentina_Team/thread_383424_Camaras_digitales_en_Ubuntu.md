---
title: "Camaras digitales en Ubuntu ?"
date: 2007-03-13
forum: Argentina Team
---

### Post by jayflower on 2007-03-13
:confused: Como para poder quedarme del todo necesito bajar las fotos de la camara, pero la enchufe y no hace como el gran demonio que apenas enciende rompe los cocos preguntando que hacer con el disquito de la camara.... Hay que hacer algo para que la reconozca????Me faltaran algunos paquetes?](*,)  Da fiaca mirar todos los foros.
Thx

---

### Post by beuno on 2007-03-13
¿Que marca/modelo de camara es?

---

### Post by jayflower on 2007-03-13
Es una Samsung Digimax A302. USB of course, y solo necesito qur reconozca el memorystick. Es necesario "montar" ese disco? Le hago un sudo minimount ?:d

---

### Post by beuno on 2007-03-13
Tendria que montarlo automaticamente al conectar la camara (quizas tengas que prenderla, o ponerla en modo "USB").

Sino fijate si se produce algun error en:

/var/log/messages
o
/var/log/dmesg

Todas las camaras digitales que conecte (mas de 10), me las tomo todas al toque, asi que no veo razon para que tu modelo no funcione asi (una busqueda rapida en Google tampoco muestra problemas frecuentes).

Mira los logs o postealos aca.

---

### Post by spg76 on 2007-03-13
[En este thread]("http://www.ubuntuforums.org/showthread.php?t=367990&highlight=Digimax") un usuario planteo un problema similar con una cámara Samsung Digimax (en su caso A40) y después posteo como lo resolvió. En una de esas te sirve.
Saludos.

---

### Post by lavaramano on 2007-03-13
que te tira el lsusb? usas una tarjeta sd o las guardas en la camara? 
estaria bueno que tires mas data y no un 'no me anda la camara, que hago'..

---

### Post by ubuntu27 on 2007-03-13
> **jayflower said:**
> Es una Samsung Digimax A302. USB of course, y solo necesito qur reconozca el memorystick. Es necesario "montar" ese disco? Le hago un sudo minimount ?:d

La camara Samsung Digimaz 301 (no la tuya) es compatible con Unix, Linux.

Tu camara tambien no debe de tener problemas....


[Lista de Hardware Camara Digital soportada por Unix y Linux]("http://www.teaser.fr/~hfiguiere/linux/digicam.html")

En mi caso, todas mias camaras y Video camaras funcionan bien en Ubuntu Edgy, lo autodetecta al insertar USB.

haber, talvez ya lo autodetecto pero, no esta tomando accion.

Anda a Places (Lugar)/Computer (computadora)

Ves alli la camara?


*****
Montar:

 mount -t vfat /dev/sda1 /mnt    ( o donde sea que deseas montarlo) 

editar /etc/fstab y agregar:

/dev/sda1 /media/camera vfat rw,user 0 0



Nota: lo saque desde el foro de LinuxQuestion.org Los que escribieron esto son usuarios de Gentoo.

[http://www.ubuntuforums.org/showthread.php?t=367990&highlight=Digimax](http://www.ubuntuforums.org/showthread.php?t=367990&highlight=Digimax)

---

### Post by jayflower on 2007-03-13
Hi!!

 Oops: found it:

   1. Created a new mount point: $ sudo mkdir /mnt/camera
   2. Mounted the camera: $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000

 I should look a little harder next time!!

                     Andrew

[COLOR=DarkOrange][I]me too. 
P.D.: sinceramente pense que no habia que montarla. por eso pregunte.

[/I][/COLOR]

---

### Post by jayflower on 2007-03-13
Ya esta. Gracias...

---

### Post by ubuntu27 on 2007-03-13
> **jayflower said:**
> Ya esta. Gracias...

Chevere!

y dime, como te va Feisty F?

---

### Post by jayflower on 2007-03-13
aun no va...traduciendo...ya lo vamos a probar! :)

---

### Post by ubuntu27 on 2007-03-14
> **jayflower said:**
> aun no va...traduciendo...ya lo vamos a probar! :)

Osea que aun no estas probando/usando Feisty?
Crei que ya lo estabas probando ya que tu perfil dice que usas Feisty Fawn testing.


Tu eres unas de las personas que esta tracuciendo los apps  en español usando Rosetta?

---

