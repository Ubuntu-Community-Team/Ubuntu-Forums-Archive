---
title: "No puedo conectarme a Internet"
date: 2007-11-16
forum: Argentina Team
---

### Post by Fikcio on 2007-11-16
Buenas, gente. ¿Qué tal? Ayer instalé el Ubuntu 7.10 (64 bits), mi primera incursión en Linux, y, claro, ya tengo problemas: no puedo conectarme a Internet (¡horror!) y por tanto no puedo descargarme cosas tan vitales como codecs y drivers (que mi *NVIDIA GeForce* reclama).

Les cuento —y advierto que no sé mucho de hardware— que tengo un modem ADSL cuyo nombre, según el Administrador de Dipositivos, es *Globespanvirata USB IAD LAN Modem* ([éste]("http://img.deremate.com.ar/user/images/1659/16596633.jpg")). Leí por ahí que para configurar la conexión se utiliza el programa *pppoeconf* (aunque mi modem es USB), pero he aquí pantallazos de la infeliz secuencia: [uno]("http://i234.photobucket.com/albums/ee308/fikcio/Pantallazo.png"), [dos]("http://i234.photobucket.com/albums/ee308/fikcio/Pantallazo-1.png"), [tres]("http://i234.photobucket.com/albums/ee308/fikcio/Pantallazo-2.png") y (¡ay!) [cuatro]("http://i234.photobucket.com/albums/ee308/fikcio/Pantallazo-3.png"). 

Si necesitan más información, chiflen. Toda ayuda es agradecidísima.

---

### Post by margori on 2007-11-16
Segnu vi en la fotos que pusiste, al programa detecta 1 interface: eth0. Esta no necesariamente es la del modem. Si tenes una placa de red instalada, eth0 seria su nombre.

No tengo experiencia con modems usb, asi que no te puedo ayudar. Buan suerte.

---

### Post by Fikcio on 2007-11-16
> Segnu vi en la fotos que pusiste, al programa detecta 1 interface: eth0. Esta no necesariamente es la del modem. Si tenes una placa de red instalada, eth0 seria su nombre.

Gracias. El problema, creo, es que Linux ni se entera de la presencia del modem. ¿Qué puedo hacer? Recuerden que soy un neófito total, ¿eh?

Usé ethernet en lugar de USB (que conste que no tengo ni la menor idea de qué estoy haciendo) y ahora el *pppoeconf* detecta dos dispositivos, pero con el mismo resultado. El led de PPP permanece apagado.

---

### Post by Fikcio on 2007-11-17
¿Nada, che? O estoy complicadísimo o me gané la antipatía de todo el mundo :confused:.

Agrego algo más: después de haber conectado el modem a la placa de red, apareció, como ya dije, otro dispositivo, y éste ahora aparece tenaz, incluso habiendo desconectado el cable ethernet.

¿Sirve o estoy diciendo*******?

---

### Post by por100pre1 on 2007-11-17
Los módems USB son muy problemáticos en cualquier máquina. El problema se agrava aún más en Linux porque los modems no suelen traer controladores para Linux. Por lo pronto no he encontrado nada sobre ese módem. Por favor espera un poco más a ver si algún usuario sabe que hacer con ese módem. :(

---

### Post by Fikcio on 2007-11-17
Gracias, por100pre1. Mi módem es dual; creo que esto significa que puede conectarse alternativamente por ethernet, ¿no es así? Les paso [una imagen de su posterior]("http://i234.photobucket.com/albums/ee308/fikcio/modem.png"). 

Y, como dije, conecté el módem usando la entrada ethernet, y *pppoeconf* me mostró dos dispositivos. Sin embargo, nada.

¿Alguna idea, por favor?

Muchas gracias.

---

### Post by SLA_leandrin on 2007-11-17
Si es dual, conectalo por la placa de red y debería andar sólo con eso, no tiene nada q ver ppoeconfig ni nada de eso. Si te funcionaba en windows te tiene q funcionar en ubuntu...

---

### Post by por100pre1 on 2007-11-17
> **Fikcio said:**
> Gracias, por100pre1. Mi módem es dual; creo que esto significa que puede conectarse alternativamente por ethernet, ¿no es así? Les paso [una imagen de su posterior]("http://i234.photobucket.com/albums/ee308/fikcio/modem.png"). 

Y, como dije, conecté el módem usando la entrada ethernet, y *pppoeconf* me mostró dos dispositivos. Sin embargo, nada.

¿Alguna idea, por favor?

Muchas gracias.

Disculpa la tardanza estaba en otro subforo. Configura manualmente la conexión como mencionó SLA_leandrin. Abre **Sistema: Administración: Red** o escribe esto en terminal:

```
gksu network-admin
```

Prueba configurar manualmente una conexión. :-k

EDIT: SLA_Leandrin está en lo cierto. Ethernet es la mejor forma de conectarse al módem. :)

---

### Post by Fikcio on 2007-11-17
Gracias a ambos. ¿Qué significa [esto]("http://i234.photobucket.com/albums/ee308/fikcio/interfaz.png")? Esa IP ahí es un buen síntoma, ¿no?

> Si es dual, conectalo por la placa de red y debería andar sólo con eso, **no tiene nada q ver ppoeconfig** ni nada de eso.

No entiendo. ¿Desde dónde, entonces, entro mi nombre de usuario y contraseña?

>  Si te funcionaba en windows te tiene q funcionar en ubuntu...

Pero en Windows lo uso con USB.

Ah, y esto es lo que me tira *ifconfig* (habiendo desconectado el cable ethernet, ¿eh?):

```
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:9F:FA:D6  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:FC:9F:FA:D6  
          inet addr:169.254.12.7  Bcast:169.254.255.255  Mask:255.255.0.0
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          Interrupt:20 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:960 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:71040 (69.3 KB)  TX bytes:71040 (69.3 KB)


```

¿Les sirve? ¿Y alguien se explica por qué apareció *y permaneció* un nuevo dispositivo (*eth0:avah*) después de haber probado por ethernet? Qué cosa, che.

Gracias.

---

### Post by SLA_leandrin on 2007-11-17
> **Fikcio said:**
> 
No entiendo. ¿Desde dónde, entonces, entro mi nombre de usuario y contraseña?



Si es dual significa que cuando lo conectas por placa de red está funcionando como router. El router tiene una dirección en donde lo configurás, ahi mismo le ingresás el usuario y contraseña. Esta dirección varía según el router (marca y modelo), googleala y la vas a encontrar. Por ej. para el q viene en arnet la dirección es 10.0.0.2, preguntale al que te vendió el modem o a tu prooveedor.

Saludos.

---

### Post by faktorqm on 2007-11-18
Necesito mas datos sobre el modem, busca el manual en google y postea el link, o una foto de atras del modem, no de adelante, ya que de adelante no brinda ninguna informacion sobre el dispositivo.
Si tiene una etiqueta abajo/al costado/arriba postea que dice.
Lo de la placa de red es normal. olvidate de eso, lo vemos despues.
salu2!!

---

### Post by Fikcio on 2007-11-19
¡Estoy enviando esto desde Ubuntu! El problema era el cable ethernet, que no era tal (seh, me zarpé en imbécil). Parece que por USB es irresoluble, ¿no? 

De todos modos, *SOLVED*. Muchas gracias a todos.

E inmediatamente voy a molestarlos con otra pregunta (y otra, y así durante un tiempo. Eventualmente aportaré).

---

### Post by pablo0469 on 2007-11-19
Que sea un "modem router" no significa que este configurado como "router", casi seguro lo tenes en modo "monousuario", porque la mayoria viene con esta configuracion de fabrica, y mucho mas si te lo dio algun proveedor.

Eso es lo que me paso a mi, y hasta que no lo hice configurar como router, con Ubuntu tenia que usar el:

sudo pppoeconf

Lo mejor que podes hacer para aprovechar bien tu modem es llamar al que te lo vendio o alguien que sepa, revise su configuracion, y eventualmente que te lo configure como "router" o modo "multiusuario o DCHP". No pierdas tiempo en llamar a tu proveedor, porque no dan soporte para ese tipo de configuraciones (porque con el modem asi, hasta podes compartir la conexion).

Si no sabes, no metas mano en la pag de configuracion del modem, ni siguiendo un tutorial, porque corres el riesgo de quedarte sin conexion si no tenes la opcion "reboot & save original settings" o algo asi (volver a la configuracion inicial.

Espero no haberte mareado mas, Saludos y segui posteando.

---

### Post by xpelaox on 2007-11-19
> **Fikcio said:**
> ¡Estoy enviando esto desde Ubuntu! El problema era el cable ethernet, que no era tal (seh, me zarpé en imbécil). Parece que por USB es irresoluble, ¿no? 

De todos modos, *SOLVED*. Muchas gracias a todos.

E inmediatamente voy a molestarlos con otra pregunta (y otra, y así durante un tiempo. Eventualmente aportaré).

JAJAJAj Le conectaste un cable de telefono nomral? yo hize eso una vez xD

---

### Post by Fikcio on 2007-11-19
> **xpelaox said:**
> JAJAJAj Le conectaste un cable de telefono nomral? yo hize eso una vez xD

¡Ja! Efectivamente. Qué bueno no ser el único.

pablo0469: también me toca hacer malabares con esto: se conecta cuando se le antoja y tengo que usar --a veces-- el pppoeconf y pon. Confío en solucionarlo solo, pero se verá. Gracias.

---

