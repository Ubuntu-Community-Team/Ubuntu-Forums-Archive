---
title: "[SOLVED] Firestarter"
date: 2008-01-16
forum: Argentina Team
---

### Post by Vero1 on 2008-01-16
Hola a todos,

Presuntamente configuré Firestarter y digo presuntamente porque no aparece el ícono en el systray a pesar de haberlo marcado.
Cuando hago click en el ícono del escritorio sale el login cada vez, así que no sé si funciona sin login o no.
Despues de loguearme sale la ventana y dice Activo pero no está claro si cuando prendo la máquina y se conecta a Internet, ya sea con Evolution o Firefox, está funcionando.

Traté de correr la ayuda pero parece que no existe porque al hacer click no pasa nada.

Alguien me puede aclarar un poco el panorama?

Gracias de antemano y saludos.

---

### Post by clasificado on 2008-01-16
El Firewall funciona todo el tiempo.

El Firestarter podes encenderlo para hacer configuraciones, y lo cerras en cuanto te molesta; El Firewall sigue funcionando lo mismo.

Si queres que el firestarter inicie lo mismo, podes agregarlo a los programas de inicio de sesión

Ahora, lo del login eso que decis no lo entiendo mucho. Igual en cuanto llego a casa lo miro un poco.

Clasificado.

---

### Post by Vero1 on 2008-01-16
Hola clasificado y gracias por contestar.

Es lo que quería saber, si funcionaba todo el tiempo.

Una pregunta mas: para agregarlo al inicio de sesión, es mediante algun comando en Terminal?

gracias

---

### Post by Mauro22 on 2008-01-16
Sino me equivoco el Firestarter es solo un Front End para el iptables.
Sirve para administrar reglas de forma grafica y ver el estado pero no hace falta que corra todo el tiempo, ya que el iptables se ejecuta junto con el kernel.


Es asi? :confused:

---

### Post by Vero1 on 2008-01-16
Hola Mauro22,

He estado viendo algo de iptables pero me parece re complicado para que yo lo use, teniendo en cuenta que de comandos todavía estoy "verde" :-)

De todas formas me siento mas tranquila si puedo ver los informes de Firestarter y lo acabo de agregar a Inicio de Sesión.

Gracias a vos tambien y saludos.

---

### Post by Moonlit Knight on 2008-01-16
Hola, el firestarter podés configurarlo para que se ponga en el system  tray. Para eso vas a:

 Editar -> Preferencias ->  Interfáz. 

Y ahí tildás las dos opciones que hay. 

Espero que te sirva. 

Saludos

---

### Post by Vero1 on 2008-01-16
Hola Moolit Knight,

Sí éso ya lo tenía marcado pero se pone únicamente si lo abro y yo tenía interés en tenerlo desde el vamos.

Gracias igual por tu comentario.

saludos

---

### Post by Mafber on 2008-01-17
Hola Verónica!!! te paso lo que estas buscando (lo copie de otra página hace un tiempo y no me acuerdo de cual era) 
_Pero NO te aconsejo que lo hagas_!!!
 
Una vez instalado deberemos hacer 2 cosas.
Si queremos que no nos ande pidiendo la clave de root siempre que le iniciamos.

    sudo gedit /etc/sudoers

Y añadimos al final esta linea

   usuario ALL= NOPASSWD: /usr/sbin/firestarter

Donde ‘usuario’ es el nombre de tu usuario

Ahora lo configuraremos para que se inicie al iniciar el pc.
En Gnome:
Sistema - Preferencias - Sesiones. Pestaña ‘Inicio’. Pulsamos ‘Añadir’ e introducimos

sudo firestarter --start-hidden

En KDE:
Escribimos en un terminal

$ echo -e '#'\!'/bin/sh\nsudo firestarter --start-hidden' > ~/.kde/Autostart/firestarter
$ chmod a+x ~/.kde/Autostart/firestarter

Según me explicaron en este foro, no es necesario (y poco recomendable) que inicie el firestarter con el inicio del SO y que quede como residente al lado del reloj (system tray)
Fijate lo que te dijeron Clasificado y Mauro22. El firewall esta funcionando aunque no veas el ícono.
Como te dije: NO te recomiendo que lo hagas... pero lo dejo a tu criterio
Suerte

---

### Post by Vero1 on 2008-01-17
Hola mafber,

Mirá lo que son las cosas. Como no me quedé quieta, googleando encontré justo lo que me estás escribiendo.
Te digo que seguí las instrucciones pero para añadir algo a /etc/sudoers hay que usar otro programa porque así no mas no acepta añadidos. Creo que se llama visudo o algo así. De todas formas lo dejé ahí.
En cuanto a que aparezca en el systray, hice lo que dicen en la Web pero a pesar de ello no aparece y tambien me sigue pidiendo que me loguee. En fin no me voy a hacer mas problemas con el Firestarter.
De todas formas camina aunque no lo vea :-)

Gracias por tomarte la molestia de buscar. 

Yo justo iba a poner solved al tema, pero me enfrasqué con otra cosa que me había traído problemas.

saludos y gracias otra vez

---

### Post by Sit3UserX on 2008-03-08
Puf! Al fin logré dar con algo que me dejara claro el tema del firewall!

Gracias a este trhead ahora entiendo que las iptables son el firewall en si mismo, que puede ser configurado de forma gráfica mediante firestarter, el cual no es necesario que se ejecute desde que el usuario inicia sesión, pues lo que realmente importa son las iptables que se cargan al inicio del sistema!

:)

---

### Post by Vero1 on 2008-03-09
Bueno me alegro por vos entonces :)

saludos

---

