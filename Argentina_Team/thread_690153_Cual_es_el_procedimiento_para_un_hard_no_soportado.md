---
title: "Cual es el procedimiento para un hard no soportado"
date: 2008-02-07
forum: Argentina Team
---

### Post by vk-cdg on 2008-02-07
Buenas, les comento mi inquietud!

Tengo una sintonizadora de TV Genius TV a Go 11 que por lo que pude ver en los listados no está soportada por Linux. Tiene chip Phillips pero aún así no la detecta. 

Hace un tiempo con uno de los chicos de acá del foro, por MSN estuvimos tratando de instalarla pero no hubo caso. Luego de mas de 1 hora de probar cosas sigue sin funcionar.

Quería saber cual es el procedimiento, si existe, para lograr que dicho hardware sea soportado.

Muchas gracias!

---

### Post by User21 on 2008-02-07
En realidad, lo mas factible es que estén soportados los chipsets de la placa, aunque el nombre comercial de la misma no figure en ninguna lista. Eso, es un clon de hardware.
 Como hice yo ? Pues agarre mi placa de TV, en mis manos, y con una lupìta, me puse a leer las denominaciones o inscripciones encima de los chips incrustados en la placa. Citando un ejemplo ficticio: si dice 0221PHC02 y buscando en Internet, averigüe que se trataba de un Tuner Phillips NTSC. Mirando los otros chips, hice lo mismo. Finalmente pude reconocer todos los chips. 
Con eso, cargue el modulo adecuado a la placa con las opciones necesarias, y voilá! PLACA DE TV funcionando!

Necesitas mas ayuda? Agregame a mi msn: [EMAIL="nouserfound@hotmail.com"]nouserfound@hotmail.com[/EMAIL]. 

Vamos a intentarlo al menos! :)

---

### Post by faktorqm on 2008-02-07
Yo estuve una banda para hacerla andar, pero por que no sabia. Tengo una pinnacle "algo", pero que tiene un integrado phillips. Para empezar, lo que hice fue ponerla en un pci, arrancar el linux, y poner "lspci". Sino aparecia, la cambiaba de slot pci y hacia lo mismo, hasta que aparecio. :D
Una vez que aparecio, me puse a buscar posts de placas capturadoras en este mismo foro y de ahi instale un par de programas, unas configuraciones, y sali mirando tele. Lo que no me andaba es la sintonizadora, pero no sabia si era mio el problema o de la placa. :(
En marzo cuando termine de rendir los finales de la facu me fijo xD

---

### Post by nemodot on 2008-02-07
Interesantes anecdotas.

Yo tengo una webcam de General Electric que no funciona en linux, pero no tengo la experiencia de ustedes para rebuscarmelas y hacer lo que hay que hacer para que este tipo de hardware funcione.

Conocen algún recurso en internet que puedo usar para al menos intentar hacerla funcionar?

---

### Post by faktorqm on 2008-02-07
La verdad que no, pero lo que tenes que hacer es, postear la marca, EL MODELO, si es usb, o no, y que pasa cuando la enchufas, probablemente nada.
Hace una cosa, enchufala y si es usb, tira el comando "lsusb" en la consola y postea la salida aca a ver si la detecto al menos. De ahi en mas, si te la muestra, busca en el foro wxcam o programas para camaras web que el tema ya se toco. salu2!

---

### Post by nemodot on 2008-02-07
Bueno, puse el comando en un terminal, me imprimio una información, pero no logro reconocer si se trata de mi webcam que es de General electric, y no tengo mas informacion que el cd con los drivers de windows donde dice "MiniCam Pro".

```
esteban@esteban-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0c45:608f Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 5543:0005 UC-Logic Technology Corp. 
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by faktorqm on 2008-02-07
desconectala y tira lsusb a ver cual de los dos desaparece.... :KS salu2!

---

### Post by nemodot on 2008-02-08
Como esperaba, desapareció "Microdia", lo cual es muy raro por que según lo que veo en Internet, Microdia es un tipo de tarjeta de memoria flash.

---

### Post by faktorqm on 2008-02-08
Bueno buenisimo, ya sabes cual es el dispositivo, ahora andate aca e instalate esto:
[http://www.ubuntips.com.ar/2008/01/29/wxcam-10/](http://www.ubuntips.com.ar/2008/01/29/wxcam-10/) y probalo y contanos como te va. salu2!

---

### Post by vk-cdg on 2008-02-08
> **User21 said:**
> En realidad, lo mas factible es que estén soportados los chipsets de la placa, aunque el nombre comercial de la misma no figure en ninguna lista. Eso, es un clon de hardware.
 Como hice yo ? Pues agarre mi placa de TV, en mis manos, y con una lupìta, me puse a leer las denominaciones o inscripciones encima de los chips incrustados en la placa. Citando un ejemplo ficticio: si dice 0221PHC02 y buscando en Internet, averigüe que se trataba de un Tuner Phillips NTSC. Mirando los otros chips, hice lo mismo. Finalmente pude reconocer todos los chips. 
Con eso, cargue el modulo adecuado a la placa con las opciones necesarias, y voilá! PLACA DE TV funcionando!

Necesitas mas ayuda? Agregame a mi msn: [EMAIL="nouserfound@hotmail.com"]nouserfound@hotmail.com[/EMAIL]. 

Vamos a intentarlo al menos! :)

Esta noche llego a casa y te agrego. 
En cuanto tengas un ratito libre (que no tengas otra cosa + importante que hacer) lo vemos.
Mil gracias desde ya.

---

### Post by nemodot on 2008-02-08
> **faktorqm said:**
> Bueno buenisimo, ya sabes cual es el dispositivo, ahora andate aca e instalate esto:
[http://www.ubuntips.com.ar/2008/01/29/wxcam-10/](http://www.ubuntips.com.ar/2008/01/29/wxcam-10/) y probalo y contanos como te va. salu2!

Sucedió lo que sospechaba, ese programa es un software para webcams, y no detectó ninguna, me dio mensajes de error. Lo que parece faltar aca es el driver de la webcam. Esta no aparece en /dev/video0

---

### Post by User21 on 2008-02-09
Sr NEMODOT:

[http://hamacker.wordpress.com/2007/10/22/instalando-uma-webcam-microdia/](http://hamacker.wordpress.com/2007/10/22/instalando-uma-webcam-microdia/)

o sino:

**     Sonix/Microdia Webcam**
Abre una terninal y tipea:
      ```
 lsusb  
```Si lo que aparece es similar a :
       ```

     Bus 002 Device 002: ID 0c45:62c0 Microdia  
``` 1) Instala 'subversion' desde los repositorios. En la terninal tipea:      Code:
      ```
sudo apt-get install subversion  
```    2) Luego tipea: (Especial atención con este punto! Copia la URL completa del enlace, ya que aparece resumida en este post!!!)
                  ```

     svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)
            cd trunk/
            gedit Makefile  
```        3) Edita el Makefile de esta manera:
a INSTALL_MOD_DIR := usb/media
            cambialo por
            INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo

        4) Guardalo y cierralo. En Terminal ingresa:
                ```

     make
            sudo make install
            sudo modprobe uvcvideo
            gstreamer-properties  
```        5) En la seccion VIDEO, selecciona v4l2 y elige USB 2.0 para el dispositivo. Cuando haces el test sobre ese origen de video, deberías ver la imagen de la cam funcionando! Ojalà que asi sea.

Intente siguiendo esa COMO! Suerte!

---

### Post by nemodot on 2008-02-09
Bien, segui paso a paso el tuto que escribiste en el foro.

Hubo un warning durante el Make:
[CODE]WARNING: could not open /home/esteban/trunk/version.h: Invalid argument [/CODE

Pero el resto siguió sin problemas. Hice el make install y no enseño errores.

Luego ejecute los dos comandos, se me abrio una ventana. No había para elegir por ningna parte "USB2.0" , pero si estaba el v4l2 y cuando puse prueba salio este error:
[http://img143.imageshack.us/my.php?image=pantallazozu1.png]("http://img143.imageshack.us/my.php?image=pantallazozu1.png")

---

