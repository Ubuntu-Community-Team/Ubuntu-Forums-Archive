---
title: "Compartir conexion entre dos computadoras"
date: 2007-08-12
forum: Argentina Team
---

### Post by facundocorradini on 2007-08-12
Hola genetes

Necesitaría ayuda para poder compartir la conexión a internet entre dos computadoras con ubuntu.

El modem (de cablemodem) está conectado a un puerto USB de una y quiero poder conectar la otra mediante un cable cruzado.

¿Alguien sabe como puedo hacer esto?

---

### Post by faktorqm on 2007-08-13
Hola, con firestarter (es un front end de iptables) compartir internet es tan facil como tildar una casilla que se llama "compartir internet". Siempre y cuando tengas todo bien configurado ok? 
Sino sabes de donde sacarlo: "sudo apt-get install firestarter", sino "aptitude search firestarter" (todo sin comillas ;))
En la compu que tenes el modem usb tenes que tener una placa de red (posiblemente integrada) con un cable cruzado a la otra pc. 
En la conexion usb no tenes que tocar nada, en la placa de red tenes que poner algo parecido a esto o esto directamente:

direccion ip: 192.168.0.1
mascara de subred: 255.255.255.0

y en la otra pc:

direccion ip: 192.168.0.2
mascara de subred: 255.255.255.0
puerta de enlace: 192.168.0.1
dns1: los dns de tu proveedor (si no sabes cuales son hace "cat /etc/resolv.conf")
dns 2: los dns de tu proveedor

Espero que te haya servido y contame como te fue. Salu2!!!!

---

### Post by facundocorradini on 2007-08-13
Ok.  muchísimas gracias, no se dan una idea de lo que he renegado con iptables tratando de hacerlo andar... si hubiera sabido que habia un front end...

esta tarde lo estaré probando y les cuento los resultados

gracias!

---

### Post by faktorqm on 2007-08-31
nunca contaste los resultados.................... :D:D:D

---

### Post by facundocorradini on 2007-09-02
! cierto, disculpame...

Andubo de diez.

Anyway, una semana después mi hermano compró un router wireless así que ahora tenemos tambien las dos laptops con internet :D

---

### Post by Mataca on 2007-09-02
Facundo, yo tengo lo mismo en casa y dejame sumar algo. Te lo explico en mi idioma por que no soy ningun analista de sistemas :confused:
Estoy usando en casa un programa que es bastante fácil de usar y muy efectivo, se llama SQUID y es un proxy cache.
lo podes bajar de: 
[http://www.squid-cache.org]("http://www.squid-cache.org")
o bien
```
sudo apt-get install squid
```

(Qué lindo es instalar un programa escribiendo una línea en una consola no??)

Este programa almacena los datos que mas usas y los guarda para que no tenga q bajarlos siempre desde las dos pc, es igual que el funcionamiento del cache de un explorador de internet.
También cuando tenés que actualizar el equipo bajas una sola vez los archivos, asi los usas en las dos pc. De esta forma no ocupas mucho ancho de banda.
Tiene un lindo control de acceso (muy útil cuando tenes una hermana de 16 que no tiene idea en donde se mete y toca cualquier cosa) para restrigir las paginas que consideres prohibidas.

Quizá sea mas útil en las redes con muuuchas pc's pero en mi caso teniendo 2 me resultó óptimo y por supuesto es %100 código abierto.

Espero que sirva

---

### Post by faktorqm on 2007-09-02
Bueno, para que no te tengas que gastarte en crear filtros, ni hacerte malasangre, decile que a tu hermana de 16 que yo le enseño como se usa linux y a donde tiene que entrar y a donde no, :lolflag: salu2!! :D

---

### Post by Mataca on 2007-09-02
Estimado Faktorqm 
No entremos en caminos pantanosos, conservemos la caballerosida' por favor, no rompamos este vínculo de confianza que nos une.

Podría responderte una barbaridad, pero dejemoslo así.

---

### Post by faktorqm on 2007-09-02
:mrgreen::biggrin::lolflag:

---

### Post by facundocorradini on 2007-09-02
> Estoy usando en casa un programa que es bastante fácil de usar y muy efectivo, se llama SQUID y es un proxy cache.
lo podes bajar de:
[http://www.squid-cache.org](http://www.squid-cache.org)

Gracias por el consejo, lo voy a probar ni bien pueda. Me parece muy interesante, sobre todo la posibilidad de bajar una sola vez las actualizaciones.

> (Qué lindo es instalar un programa escribiendo una línea en una consola no??)

Aunque sea lo más chocante para quienes vienen de win, a mí me parece lo mejor de linux. 

Muchas gracias.

--------------------------------------------------------------------------------------------------

faktorqm: ese tipo de comentarios es el peor flame que podés meter en un foro. por favor, tratá a los demás con respeto.

---

### Post by faktorqm on 2007-09-02
era un chiste che! tampoco para tanto! una humorada! perdón si los ofendí, no era mi intención. es más, pensé que capaz se copaban y se reían, pero bueno, veo que no....................................
no lo voy a hacer más, o al menos antes me voy a asegurar de que "la victima" sea buena onda y no tenga drama. 
perdon mataca. salu2!!

---

### Post by Mataca on 2007-09-03
Che yo no me ofendí ehh
Soy una persona ironica, mi respuesta quizá no se entendió pero todo bien =)
Que quede clarito, mi hna NO ES OPEN SOURCE es bien propietaria, ovbiamente todos los derechos los tengo yo. Y no los doy ni los vendo ;) (tampoco las licencias)

Abrazo de pingüino

---

