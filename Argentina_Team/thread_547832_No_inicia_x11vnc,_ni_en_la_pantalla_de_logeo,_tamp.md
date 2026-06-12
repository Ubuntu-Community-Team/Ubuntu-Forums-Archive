---
title: "No inicia x11vnc, ni en la pantalla de logeo, tampoco una vez dentro de la sesión."
date: 2007-09-10
forum: Argentina Team
---

### Post by verahert on 2007-09-10
El problema es el siguiente segui esta guia:

>     

$ sudo apt-get install x11vnc

$ sudo x11vnc -storepasswd mipassword /etc/x11vnc.pass

$ sudo gedit /etc/X11/gdm/Init/Default

Agregar esta linea:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900

El x11vnc levanta on login, pero después gdm lo mata. Para deshabilitar ese comportamiento:

$ sudo gedit /etc/X11/gdm/gdm.conf

Y cambiar esta línea :

#KillInitClients=true

dejarla así:

KillInitClients=false

Funciono pero ayer me decidi a usar la pc por remote y me lleve la sorpresa de que no levanta ni en el login ni una vez logeado en el escritorio, me cerciore de que esté todo como lo habia dejado, pero el problema persiste no me levanta x11vnc :( , lo que si me paso, no se si servirá, es que hace unos dias (ya estaba instalado x11vnc) tuve un drama con la gdm.config y la tuve que restaurar pero todo esta tal cual estaba, la verdad es que no se ya que inventar para solucionarlo.

Saludos y desde ya muchas gracias.

---

### Post by faktorqm on 2007-09-12
no entiendo tu problema.
si necesitas levantarlo al inicio, tenes que hacer un script o lo que tengas que hacer y ponerlo en gdm.conf o /etc/init.d/rc.local.
si no te levanta cuando lo inicias, postea exactamente que haces para que pase eso. 
Si te levanta, y desde afuera no podes iniciar sesion, revisa la configuracion de la red, si tenes router/switch el tema de los puertos.
Sino es nada de esto, es un garron ajjajaja salu2!

---

### Post by verahert on 2007-09-12
Bueno gente el problema lo solucione haciendo una instalacion nueva del ubuntu y anda, pero luego de instalar programas y personalizarlo al ubuntu, tengo otro problema con el x11vnc, el problema es:

- Prendo la pc1 inicia el sistema y queda en la pantalla de logeo de usuario, voy a una pc2 en la red hago vncviewer la ip, me aparece para ingresar la clave del vnc la ingreso y entra a la pantalla de logueo de usuario que habia quedado la pc1 , escribo mi usuario y mi password me logueo y automaticamente se me cierra el vncviewer y no me deja conectarme mas a la pc1, voy a pc1 y esta adentro de la sesion. 

Segun la guia que segui para evitar que gdm mate al x11vnc habia que editar /etc/X11/gdm/gdm.conf y poner el KillInitClients=false sin comentar, hice todo eso pero no hay caso.

Espero no ser confuso es algo raro, cuando tenia la instalacion limpia no me lo hacia andaba bien una vez que instale un par de programas con el automatix ¬¬ me lo empezo a hacer, ha tambien instale el look de ubuntustudio por si puede servir como dato.

Desde ya muchas gracias! 

Saludos.

---

### Post by faktorqm on 2007-09-13
no le heches la culpa al automatix que no tiene nada ke ver. solo es un simple instalador de aplicaciones.
lo que contas es raro, por que lo del killinitclients tambien lo vi. instalaste algun firewall? firestarter, iptables, o algo de eso?
fijate que programas instalaste, si tienen ke ver con algo del gdm, o del manejador de ventanas, es medio raro lo que te pasa. tenes activado beryl ocompiz o compiz-fusion? salu2!

---

### Post by verahert on 2007-09-13
Na jaja era un chiste lo de automatix :), mira instale las aplicaciones con automatix sea codecs y aplicaciones comunes y despues el look de ubuntu studio, nada mas que eso, y ningun firewall ni tampoco iptables.

Saludos

---

