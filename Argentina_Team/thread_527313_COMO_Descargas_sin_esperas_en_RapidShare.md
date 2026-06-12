---
title: "COMO: Descargas sin esperas en RapidShare"
date: 2007-08-16
forum: Argentina Team
---

### Post by User21 on 2007-08-16
**COMO: Descargas en RAPIDSHARE con UBUNTU.**

Los archivos de gran tamaño que se alojan en Rapidshare, generalmente vienen partidos en archivos RAR de menor tamaño! En win2 podías bajarlos uno detrás del otro, cambiando la dirección MAC de la placa de red.
En Ubuntu, con el mismo principio, logré hacerlo de esta forma:

Antes que nada, instalamos una pequeña aplicación desde los repositorios:

```
$ sudo aptitude install macchanger 
```Guardamos en los marcadores de Firefox la pagina donde tenemos los links que queremos descargar. Cerramos el Firefox. Abrimos una consola y tipeamos:

```
$ sudo /etc/init.d/networking stop  
```Esto detiene la red. Inmediatamente a eso, desenchufo la alimentación del módem.
Ahora cambiamos la MAC, tipeando:

```
$ sudo macchanger -r eth0
```Una vez ejecutado el cambio de MAC, volvemos a enchufar nuestro módem. Re-arrancamos la conexión con:

```
$ sudo /etc/init.d/networking start
```La conexión se va a restaurar inmediatamente, y 15 segundos después, se desconectará. NO HAGAS NADA!
Al volver automáticamente la conexión, ya podremos seguir bajando nuestros archivos desde Rapidshare, los cuales guardamos en los marcadores, para tener fácil acceso a ellos.

Al principio suele parecer algo engorroso enchufar y desenchufar el módem, PERO ES MUCHO MEJOR QUE ESPERAR los 40-100 minutos, entre cada parte de archivo! 

**NOTA**: Puede que este mismo principio funcione en otros sitios además de Rapidshare. Por otro lado, los que saben mas de scripting, pueden hacerse un script que detenga el proceso, y pida al usuario que apague el módem, y luego le pregunte acerca de reiniciar el servicio de red. Quienes lo hagan, FAVOR DE COMPARTIRLO!

Enjoy, Ubuntu!

---

### Post by facundocorradini on 2007-08-16
genial........ apoyemos la piratería en una comunidad de software libre....
.............................................................................
...................
...

---

### Post by marianom on 2007-08-16
Está por demás claro que esta comunidad no alienta no da soporte a la piratería (más allá que es un tema discutible[1] la ilegalidad misma del proceso e incluso el uso de la palabra "piratería" -ver rms para más info[2]- para describir esta actividad)

Yo entiendo que User21 NO está hablando de bajar películas/software que sería ilegal/inmoral/poco ético[3] obtener por rapidshare. 
No es así, User21?


[1] pero no discutible en este foro por favor, hay lugares más apropiados. Gracias.
[2] [Misinterpreting Copyright - The rhetoric of maximization by Richard Stallman]("http://www.gnu.org/philosophy/misinterpreting-copyright.html").
[3] ver link anterior.

---

### Post by leo_rockway on 2007-08-16
> **facundocorradini said:**
> genial........ apoyemos la piratería en una comunidad de software libre....

no necesariamente pirateria. pueden ser peliculas que uno mismo hizo o peliculas libres (como elephants dream). lo mismo respecto al software.

---

### Post by User21 on 2007-08-16
[I]"Está por demás claro que esta comunidad no alienta ni da soporte a la piratería (más allá que es un tema discutible[1] la ilegalidad misma del proceso e incluso el uso de la palabra "piratería" -ver rms para más info[2]- para describir esta actividad)

Yo entiendo que User21 NO está hablando de bajar películas/software que sería ilegal/inmoral/poco ético[3] obtener por rapidshare. 
No es así, User21? "[/I] 
 
>>> ASI ES, misssamigoosss... solo me referia a archivos de gran tamaño! Me exprese mal en el principio... Ya fue corregido. ¬_¬

---

### Post by sdm_cacto on 2007-08-16
> **User21 said:**
> [I]"Está por demás claro que esta comunidad no alienta ni da soporte a la piratería (más allá que es un tema discutible[1] la ilegalidad misma del proceso e incluso el uso de la palabra "piratería" -ver rms para más info[2]- para describir esta actividad)

Yo entiendo que User21 NO está hablando de bajar películas/software que sería ilegal/inmoral/poco ético[3] obtener por rapidshare. 
No es así, User21? "[/I] 
 
>>> ASI ES, misssamigoosss... solo me referia a archivos de gran tamaño! Me exprese mal en el principio... Ya fue corregido. ¬_¬

Claro, como las fotos de mis vacaciones, yo te entendi al toke no hace falta q te expliques. ;)

---

### Post by por100pre1 on 2007-08-18
Creo que fue una presunción de culpabilidad. Es como hablar de BitTorrent, muchos suelen saltar a hablar sobre piratería con solo escuchar su nombre. Sin embargo, BitTorrent es el metodo usual para descargar Ubuntu Feisty Select DVD y Gentoo 2007.0 DVD entre otros materiales libres. RapidShare posee el mismo potencial aunque sabemos que en la práctica la gente lo usa más para la piratería. :)

---

### Post by undiaperfecto on 2007-08-18
El metodo mas facil es pagarse una premiun :(
un amigo pago una y la usamos al menos 3 personas y nunca hubo drama

---

### Post by luissil on 2008-02-02
Segui tus instrucciones pero no me funciona, al poner:

```
$ sudo /etc/init.d/networking stop
```

me da:

```
 * Deconfiguring network interfaces...                                   [ OK ] 

```

Pero mi conexion sigue activa, sigo teniendo internet y todo eso, tengo 2 computadoras conectadas al modem a traves d un router... no se si eso tenga algo ke ver....:confused:

---

### Post by marianom on 2008-02-02
¿Y que pasa con 

```
sudo ifdown ethx
```

donde *x* es la interface activa (la cual la podes averiguar con ifconfig y/o iwconfig)?

---

### Post by anka on 2008-02-02
bueno.., yo tengo un *.sh en el escritorio de cuando todabia usaba el alfajor (pppoe) y hace eso, es bastante estupido:

#! /bin/bash

sudo pppoe-stop

sleep 3

sudo pppoe-start

le das permisos de ejecucion y sacatelas.., te renueva la ip al toque :P

Asi pude bajar 32 veces seguidas las fotos de mi perra que guardo ahi. Fue un experimento que hice para ver si anda.., nunca mas lo use...

Saludos!

---

### Post by luissil on 2008-02-02
> **marianom said:**
> ¿Y que pasa con 

```
sudo ifdown ethx
```

donde *x* es la interface activa (la cual la podes averiguar con ifconfig y/o iwconfig)?

me da: 

```
ifdown: interface eth0 not configured
```

como es ke la configuro??? o ke?:confused:

---

### Post by leo_rockway on 2008-02-02
no se porque no me funciona el comando ifdown / ifup en ubuntu.

en lugar de eso tengo que usar sudo ifconfig ethx down / up

---

### Post by luissil on 2008-02-02
> **leo_rockway said:**
> no se porque no me funciona el comando ifdown / ifup en ubuntu.

en lugar de eso tengo que usar sudo ifconfig ethx down / up

con el ifconfig si se me desactiva la conexion, despues pongo:

```
sudo macchanger -r eth0
```

pero automaticamente c vuelve a conectar la red...

y rapidshare sigue restringiendo mis downloads....

---

### Post by User21 on 2008-02-04
Seria ideal que nos expliques EXACTAMENTE como te conectás, con qué modem, USB o Ethernet, qué empresa, etc... Así vemos si te podemos ayudar...

---

### Post by luissil on 2008-02-04
> **User21 said:**
> Seria ideal que nos expliques EXACTAMENTE como te conectás, con qué modem, USB o Ethernet, qué empresa, etc... Así vemos si te podemos ayudar...

me conecto a traves de este router via ethernet:
Encore Electronics
Model No. ENRTR-104-2
Product Name: Broadband Router
S/N: 50176090000350
Mac Adrdress: 0014788E47DE

que a su vez esta conectado via ethernet a este modem:
Scientific Atlanta
Webstar
DPX2100 Series Cable Modem
P/N: 4002199
S/N: 102291026
Mac: 000a73a86644

La empresa ke me da internet es: Cablevision S.A. de C.V.

Mi computadora es una Sony Vaio PCG-V505BL

y esta vez al cambiar la MAC me dio:

```
~$ sudo macchanger -r eth0
Current MAC: 08:00:46:ac:da:46 [wireless] (Sony PCWA-C10)
Faked MAC:   ba:f5:ad:5f:35:fd (unknown)
```

espero que alguien me pueda ayudar... gracias...

---

### Post by maxehhh on 2008-02-12
Cambia la MAC de la placa de red posta o solo la "camufla"?

---

### Post by YOGUI on 2008-02-15
Buenas! 
Soy nuevito en esto. Pero según veo en el código (diganme si me equivoco), es como reiniciar el modem o algo así. Esto sirve si tenemos IP dinámica. Puede ser que el problema de luissil sea que tiene IP fija? (Suele ser asi cuando tenemos un router)
Yo tengo IP fija y me parece que no funca...

---

### Post by faktorqm on 2008-02-16
La movida es asi, la enmascara la MAC, no la cambia nunca por que viene grabada en el firmware. Ahora bien, cuando vos cambias la MAC rompes la tabla ARP, que es la que asocia direcciones MAC con direcciones IP en el router. Por lo tanto tenes que desenchufar y volver a enchufar el cable para que el tipo haga de vuelta esa tabla. Como no garpa hacer eso, es lo mismo deshabilitar y volver a habilitar la placa. El ip, puede seguir siendo el mismo o no, pero rapidshare te toma la mac y el ip, si alguno de los dos son iguales capaz no te deja bajar, y menos si te metio algun cookie en el diome. Capaz me equivoque con respecto a rapidshare, pero algomas o menos asi es. No pensaron que si fuera tan facil ya lo hubieran hecho todos? salu2!!

---

### Post by Thalskarth on 2008-02-16
> **YOGUI said:**
> Buenas! 
Soy nuevito en esto. Pero según veo en el código (diganme si me equivoco), es como reiniciar el modem o algo así. Esto sirve si tenemos IP dinámica. Puede ser que el problema de luissil sea que tiene IP fija? (Suele ser asi cuando tenemos un router)
Yo tengo IP fija y me parece que no funca...

Hola, yo tengo IP fija. Y esto me funciona perfectamente tanto con Rapidshare como con Megaupload.

O sea, incluso despues de hacer el truco, la IP sigue siendo la misma, pero me dejan descargar sin dramas...

Es decir, me funciona de 10 :cool:

---

### Post by luissil on 2008-02-18
> **maxehhh said:**
> Cambia la MAC de la placa de red posta o solo la "camufla"?

no entiendo a que te refieres////:confused:

---

### Post by Air23 on 2008-02-22
Hola: a mi tampoco me funciona. Me pasa lo siguiente:
> juan@HAL9000:~$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                   [ OK ] 
juan@HAL9000:~$ sudo macchanger -r eth0
Current MAC: 00:1b:11:11:0c:e7 (unknown)
ERROR: Can't change MAC: interface up or not permission: Device or resource busy


Por una cuestion de comodidad cuando hay que desenchufar el modem, en lugar de hacerlo de la pared, le estoy desenchufando al modem el cable de la corriente (el que va al modem, pasa que el enchufe esta detras de una biblioteca llena de libros). Esto puede ser la causa?

Me conecto con un modem ethernet Motorola SBV5120 SURFboard cablemodem y mi proveedor de internet es telecentro

Alguna sugerencia sobre como puedo hacerlo andar y/o que esta pasando?:confused:

Muchas gracias:)

---

### Post by Thalskarth on 2008-02-23
> **Air23 said:**
> Me conecto con un modem ethernet Motorola SBV5120 SURFboard cablemodem y mi proveedor de internet es telecentro

Que raro... o sea, yo tambien tengo Telecentro y el mismo Modem. Y desenchfo el cable tambien desde el lado del modem, ya que el toma de la pared esta muy escondido... y me funciona todo perfecto....

---

### Post by mr-29a on 2008-04-26
Muchas gracias User21 por esta solucion solo me registre para agradecerte

---

### Post by Fibonacci on 2008-04-26
> **luissil said:**
> me conecto a traves de este router via ethernet:
Encore Electronics
Model No. ENRTR-104-2
Product Name: Broadband Router
S/N: 50176090000350
Mac Adrdress: 0014788E47DE

que a su vez esta conectado via ethernet a este modem:
Scientific Atlanta
Webstar
DPX2100 Series Cable Modem
P/N: 4002199
S/N: 102291026
Mac: 000a73a86644

La empresa ke me da internet es: Cablevision S.A. de C.V.

Mi computadora es una Sony Vaio PCG-V505BL

y esta vez al cambiar la MAC me dio:

```
~$ sudo macchanger -r eth0
Current MAC: 08:00:46:ac:da:46 [wireless] (Sony PCWA-C10)
Faked MAC:   ba:f5:ad:5f:35:fd (unknown)
```

espero que alguien me pueda ayudar... gracias...

No sé, estoy especulando.
¿Qué tal si intentas quitar (temporalmente, claro) el router y conectar directamente el computador al módem?

---

### Post by majatu on 2008-04-26
Pero cambiar la MAC es ilegal supuestamente... los proveedores de inet te pueden dar de baja al servicio porque les estas alterando info q ellos usan. o al menos algo asi entiendo yo.

mejor esperar para bajer q poder tener peroblemas y #-o

---

