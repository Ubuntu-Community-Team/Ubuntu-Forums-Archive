---
title: "Gutsy No me Reconoce Joystic"
date: 2007-12-08
forum: Argentina Team
---

### Post by pablo0469 on 2007-12-08
Hola, gente, ayer me compre un buen joystic para disfrutar un poco mas el Open Arena y Tremulus, pero no hay caso, GG no me lo levanta ni por casualidad.

Es un Euro Case con conexion USB.

Desde ya, muy agradecido para ver como soluciono este tema (es la primera vez que meto uno de estos perifericos en la PC).

Saludos, y gracias de antemano.

---

### Post by benzema on 2007-12-08
Yo tengo uno y tampoco me va bien,cuando entro al fifa 07 o al gta san andreas se va solo para arriba como si yo apretara para arriba no se que onda

---

### Post by sajnox on 2007-12-09
Hola, proba ejecutar en una consola 

$ lsusb 

asi sacas una lista de lo que reconoce en los puertosUSB

---

### Post by pablo0469 on 2007-12-09
Gracias Sajnox, esto es lo que me tira ese comando:

Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0e8f:0003  
Bus 001 Device 001: ID 0000:0000 

Obviamente, eso es chino basico para mi... y aclaro que en estos momentos, es lo unico que tengo conectado a los 4 puertos USB que tengo en la maquina.


De nuevo, gracias y ojala pueda solucionar este pequeño traspie.

---

### Post by Hei Ku on 2007-12-09
> **pablo0469 said:**
> Gracias Sajnox, esto es lo que me tira ese comando:

Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0e8f:0003  
Bus 001 Device 001: ID 0000:0000 

Obviamente, eso es chino basico para mi... y aclaro que en estos momentos, es lo unico que tengo conectado a los 4 puertos USB que tengo en la maquina.


De nuevo, gracias y ojala pueda solucionar este pequeño traspie.

En argentino basico, del joystick ni noticia. Proba de cambiarlo de puerto USB. Algunas veces, si el joystick es para USB 2.0, no todos los puertos estan habilitados, asi que tenes que probar cambiandolo hasta que lo reconoce. A mi me pasa con mi celular.

Proba cambiandolo de puerto y corriendo lsusb hasta ver algo distinto. Deberia al menos tirarte el nombre del fabricante.

---

### Post by pablo0469 on 2007-12-10
Gracias Hei Ku por traducirmelo al criollo, y ya que lo mencionas, tambien me pasa lo mismo con cualquier dispositivo USB que le quiera enganchar (celulares, camaras, etc.). Mañana voy a ir rotandolo por los puertos e incluso reiniciando la maquina a ver que pasa. Lo mismo con las otras cosas. Todos los dias se aprende algo nuevo.
 
Y si, es un dispositivo USB 2.0, pero creo que por comprarlo apurado y sin mucho tiempo, ahora que leo bien el envoltorio, parece que solo tiene soporte para Windows...
 
Gracias y saludos.

---

### Post by benzema on 2007-12-10
> **pablo0469 said:**
> Gracias Hei Ku por traducirmelo al criollo, y ya que lo mencionas, tambien me pasa lo mismo con cualquier dispositivo USB que le quiera enganchar (celulares, camaras, etc.). Mañana voy a ir rotandolo por los puertos e incluso reiniciando la maquina a ver que pasa. Lo mismo con las otras cosas. Todos los dias se aprende algo nuevo.
 
Y si, es un dispositivo USB 2.0, pero creo que por comprarlo apurado y sin mucho tiempo, ahora que leo bien el envoltorio, parece que solo tiene soporte para Windows...
 
Gracias y saludos.

a el mi no se para que tiene soporte porque me lo regalo un amigo sin caja ni nada,pero no me funca tampoco en linux no se que onda despues voy a preguntar en algun comercio si tienen para este sistema

---

### Post by User21 on 2007-12-11
A mi, me funcionó un joystick genérico USB, una vez que levanté los módulos necesarios, incluso tengo una aplicación que lo setea a tu antojo.
Los modulos son joydev , gameport y analog . Los levantan con sudo modprobe y prueban de hacer funcionar el joystick en algun juego, o de setearlo con las aplicaciones joystick o jscalibrator. Es posible, incluso, que sea necesario instalarse algunas librerias desde synaptic! Solo busquen JOYSTICK en el, y vean que pueden hacer. 

De todas formas, depende del modelo de su joystick! Por las duidas, les dejo este [HowTo]("http://ubuntuforums.org/showthread.php?t=55173&") en ingles. (No lo he testeado!)

PD: si logran hacerlo funcionar, no olviden cargar los módulos al inicio!, simplemente añadiéndolos en modules! sudo gedit /etc/modules

---

### Post by pablo0469 on 2007-12-12
Gracias, User, a ver si entendi bien: instalo el paquete "modprobe" y despues me voy a Synaptic e instalo todos los que vea relacionados con Joystic? 
 
Igualmente hasta el viernes dudo que tenga tiempo para hacer todo esto. Y para ser honesto, tengo ganas de hacer funcionar el joystic mas que nada por mi hijo, que esta muy ilusionado con usarlo en algunos juegos que le he bajado (a los 38 años, obviamente tengo cosas mas importantes que atender :().
 
Gracias de nuevo y saludos.

---

### Post by Hei Ku on 2007-12-12
nop. modprobe se refiere a cargar un modulo del kernel. O sea:

sudo modprobe joydev

y asi siguiendo.
Este comando lo carga por esta vez. Si reinicias la pc no lo vuelve a cargar, eso se hace desde otro lado, pero te sirve para probar, y si te mandas algun moco podes reiniciar y aca no paso nada.

Entonces, instala los paquetes de synaptic, y proba de cargarlos con modprobe, a ver si tenes suerte, y contanos.

---

### Post by User21 on 2007-12-12
Voy de nuevo, en camara lenta:
Con solo ejecutar lsusb deberías ver tu joystick de esta forma:
Bus 00x Device 00x: ID 0e8f:0003   
(No exactamente así, pero con que algo parecido aparezca, es suficiente)
Si sólo logras ver puros ceros, pues intenta cambiando de puerto USB. No todos los joysticks salen con marca: es posible que solo veas números y letras sin sentido para ti, pero significa que ALLÍ hay algo.
Acto seguido:

```
sudo modprobe joydev
sudo modprobe gamepad
sudo modprobe analog
sudo modprobe gameport
```
Una vez hecho eso, instalate el paquete de calibración de joystick:
```
 sudo aptitude install jscalibrator
```
Con él, puedes testear y setear el joystick a tu antojo. 

Finalmente: cada aplicación que vaya a usar el joystick puede que os exija el nombre del dispositivo: el joystick se puede llamar /dev/input/X o /dev/input/joy1 o cosas asi :P Se chequea con lsinput (sudo aptitude install input-utils). 

De todas formas, según el tipo de joystick, gamepad, palanca, o cualquier maldita cosa que éstes usando, puede necesitar distintos módulos! Chequea por mas info en [http://swik.net/Ubuntu/Only+Ubuntu/How+to+Set-up+a+gameport,gamepad+or+joystick+in+Ubuntu/3iqr](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Set-up+a+gameport,gamepad+or+joystick+in+Ubuntu/3iqr)
o googlea con el modelo o marca de tu dispositivo y como hacerlo funcionar en Ubuntu. El joystick que logre usar era un simple analogo de esos de $30  xD marca TaiChiChuan! xD

---

### Post by pablo0469 on 2007-12-13
Gracias por tu tiempo, User, instale el jscalibrator, y cosa extraña, funciona todo, lastima que no en los juegos.

Del modprobe, la consola no acusa ni recibo. Despues con mas tiempo voy a seguir el resto de tus consejos.

Saludos, y de nuevo, muchas gracias (cuando haga todo te cuento como me fue).

---

### Post by User21 on 2007-12-13
Vi por allí también, en Synaptic, una aplicación que setea los comandos de tu joystick y los traduce como entradas de teclado. Qué quiero decir con esto? Convierte el dato ingresado con el joystick o gamepad, a una señal similar a la ingresada con el teclado! Solo configura los juegos como desees, y a cada tecla del joystick asignale una letra o numero.

Que cuál es el paquete ? No me acuerdo, pero sale con la busqueda *joystick* en Synaptic. Ahora estoy en el trabajo!
 Buscalo a través de la descripción. 

Puede que también necesites el paquete xserver-xorg-input-joystick . 

Espero sirva de algo todo esto! No veo la hora de ponerle [solved] a este thread xD

PD: el *sudo modprobe* (vease el SUDO delante xD) no devuelve data en consola. Al hacer *lsmod*, obtienes una lista de los modulos cargados actualmente.

---

### Post by Mafber on 2007-12-15
Cuando conecto mi joystick Euro funciona bien en los juegos que lo probé, play sobre todo

---

### Post by pablo0469 on 2007-12-16
Gracias de nuevo User, mañana veo si con un poco de tiempo soluciono esto. El joystic funciona pero solo para algunos comandos de los juegos, no todos.

Me dijeron que no le de bola a eso que tiene soporte solo para Windows, en realidad es generico y anda en cualquier SO.

Saludos y tranqui, ya le vamos a poner Solved.

---

### Post by facundocorradini on 2008-01-02
Puede que esto les sirva: 

[http://thinkdany.wordpress.com/2007/11/17/joysticks-en-ubuntu/](http://thinkdany.wordpress.com/2007/11/17/joysticks-en-ubuntu/)

---

