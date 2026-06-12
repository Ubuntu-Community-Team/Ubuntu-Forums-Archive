---
title: "Instalar Ubuntu y dejar la PC con doble booteo para levantar XP"
date: 2008-03-28
forum: Argentina Team
---

### Post by --Lutari-- on 2008-03-28
Como Dijo Mauro22 ¿Como hago para hacer lo que dice el Título?
Disculpen por tanto Spam =3 Es que soy Realmente Novato en esto...

---

### Post by Mauro22 on 2008-03-28
Llega un momento en la instalacion que Ubuntu te preguntará como quieres particionar el disco (en criollo, hacer lugar para linux)


Tienes varias opciones, la primera (automatica) es descontar X% a la particion de windows para liberar espacio y usarlo para la instalacion de linux.

Tambien puedes particionarlo a tu gusto.



Si en el XP no tienes mucho que perder y/o no sabes mucho de particionar elegi la opcion automatica eligiendo el % de espacio que le quieras dar a linux.


:)

---

### Post by --Lutari-- on 2008-03-28
Eso si lo se pero como Inicio Windows? Nose donde Lei parece que al Iniciar WIndows se destruye algo llamado "GRUB"

---

### Post by Mauro22 on 2008-03-28
Despues de terminar la instalacion, Ubuntu instalara el GRUB (selector de arranque)


GRUB examinará todos los SS.OO. que existan y los agregará a la lista de inicio.


Cada vez que enciendas la PC, aparecerá un menú con todos los SS.OO existentes, tales como linux y win2 etc etc


Solo tienes que elegir el que mas te plazca!


Se "destruye" GRUB si reinstalas/reparas ese windows o instalas otro windows mas aparte!

---

### Post by --Lutari-- on 2008-03-28
Pero no me acuerdo donde dicen que si entrar a Windows se "Destruye el GRUB" y no puedes volver a WIndows

---

### Post by leo_rockway on 2008-03-28
> **Mauro22 said:**
> 
Se "destruye" GRUB si reinstalas/reparas ese windows o instalas otro windows mas aparte!

^

Mauro22 ya te dio la respuesta.

---

### Post by valucha on 2008-03-29
[COLOR="DarkOrchid"]la "destrucción" del GRUB puede suceder si uno tiene más de un sistema operativo y de repente se le ocurre REINSTALAR windows (o como la gente dice, formatear, aunque no es correcto), o que quieras instalar OTRO windows, (ej, windows vista, windows ue, windows 98). Pero en realidad esa "destrucción" no es como tal sino que es algo como "ocultamiento"... Cuando instalas un nuevo windows (REPITO, WINDOWS! NO LINUX) agrega al inicio su propio gestor de arranque (GRUB no es más que otro gestor de arranque que permite seleccionar entre más de un sistema operativo) y se coloca "delante" de nuestro amado GRUB... Qué pasa en ese caso? simplemente se te va a iniciar Windows sin que antes te pregunte nada. Osea, tu hermano ni se va a dar cuenta.
¿Y qué pasó con mi GRUB y mi Ubuntu?... SIguen ahi, intactos, nada más que hay que reparar el GRUB de una forma fácil. Hay taaaaaaaaaaanta gente que se mandó esta macana que está repleto de guías en internet de como solucionarlo, así que si un día llegas y tu hermano te dice " Lutari! formatié Windows!!" con su mejor cara de alegría, vos te tranquilizas, le pedís la compu, buscás en google "reparar grub reinstalacion windows" o algo asi y seguís los pasos y Voilà. :)


Te recomiendo antes de que instales Ubuntu, que investigues un poco acerca de si todo tu hardware va a estar soportado, si que cosas vas a tener que hacer si no lo está. Como para que no te tome por sopresa y capaz podés solucionarlo antes de instalar Ubuntu. 
Tené especial cuidado si tenés:
-UNa placa de video ATI.
-UNa sintonizadora de tv
-SI te conectás a internet via ARNET, es posible que al principiono tengas internet, se soluciona MUY facilmente leyendo un par de guías... hay trillones.
-SI tenes una placa wifi.
-SI tenés una placa de sonido Intel HD.

Y creo que nada más....

Igual te digo que es fácil, solamente tenes que tener ganas de leer mucho y aprender y 
te va a ir de maravillas... 

SUerte :) y bienvenido[/COLOR]

---

