---
title: "Recomendación para una VPN ?"
date: 2007-01-16
forum: Argentina Team
---

### Post by jpmorelli on 2007-01-16
Qué cliente de VPN me recomiendan, la verdad que encuentro paquetes sobre el tema pero no se cual esta bueno . Alguno usa alguno ?

---

### Post by marianom on 2007-01-17
Eso depende a que servidor vpn te quieras conectar: checkpoint, cisco, pptp, openvpn.

Tira algún dato más y lo vamos viendo.

---

### Post by felipelerena on 2007-01-17
ya habia habido un post de uluga al respecto [http://ubuntuforums.org/showthread.php?p=1848585&highlight=vpn#post1848585](http://ubuntuforums.org/showthread.php?p=1848585&highlight=vpn#post1848585)
ahi respondo tu pregunta y hay un par de links copados

---

### Post by jpmorelli on 2007-01-17
Es una vpn (pptp) bajo Windows, se agradece el link felipe, parto desde ahi a ver si me sale.
Muchas gracias. ;)

---

### Post by felipelerena on 2007-01-17
muchas de nadas, cualquier cosa avisa que el pibe que se sienta al lado mio lo tiene configurado en dapper

---

### Post by felipelerena on 2007-01-18
y? como te fue?

---

### Post by jpmorelli on 2007-01-25
Sory Felipe, recien entre al thread por el link del tutorial asi que también me entero de tu pregunta.
Como te imaginarás, recién bajo la info, después te comento que ondina.

---

### Post by marianom on 2007-02-20
jmorelli, con tu permiso copo el thread con un problema particular de mi vpn.
Instalé el cisco gracias a los links de felipe y durante un tiempo me pude conectar sin problemas con uno de mis clientes que tiene el cisco vpn.
El tema es que con la actualización de kernel el vpn no funciona más (ya que necesita los headers del kernel actual para trabajar). Así que bajé los headers actuales, desinstalé el vpn y lo reinstalé con los nuevos. Todo salió ok.
Pero cuando lo ejecuto:

```
mariano@mishima:/etc/init.d$ sudo vpnclient connect cliente1
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Enter a group password: 
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Illegal seek
Initializing the VPN connection.
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```

Busqué en la web para ver como resolver ese error del bindeo y como era lógico todos dicen (3 páginas en la web: una en alemán que no se leer, una en checo (??) el cual sé leer menos y la tercera un foro donde estaba la respuesta) que con lsof -i<puerto> busque que aplicación está tomando el puerto y la mate.
El tema es que 
```
mariano@mishima:/etc/init.d$ lsof -i:500
mariano@mishima:/etc/init.d$ 

```
no devuelve nada como pueden ver.

¿Alguien tiene alguna sugerencia para que pueda resolver mi pequeño problema? ¿Alguien conoce otro método válido para encontrar que está ocupando ese bendito puerto así lo puedo arreglar?

Gracias.

---

### Post by beuno on 2007-02-20
No uso ninguna VPN, asi que es medio al azar esto.

Me da la impresion que te falta configurar algo ya que no deberia hacer bind a 0.0.0.0, sino a una IP existente coo 127.0.0.1 o la IP de la maquina.

---

### Post by jpmorelli on 2007-02-20
yo usé un cliente pptp ya que tenía que conectarme a una red guindows y no tenía muy claro si el cliente de Cisco funcionaba, y me conecté pero a partir de ahi debo tener algún sufijo de DNS mal declarado, o el proxy mismo porque no podía ver ningún recurso compartido, aunque la VPN me decía que estaba conectada.
Usé un cliente de un repositorio particular de un chabón que me pareció copado, pero la verdad me encantaría aprenderlo como lo hacés vos vía comando. Seguiremos informando....

Lo que yo probé:
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml")

---

### Post by marianom on 2007-02-20
Una opción alternativa es vpnc (tiene un GUI también Kvpnc) que está en los repositorios y sirve para Swan/PPTP/Cisco/Openvpn. Yo me quedé colgado en mis intentos contra Cisco (se desconecta por timeout sin otro mensaje de error) y PPTP (se queda conectando para siempre). 
Pero que mi momentanea mala experiencia no prive a nadie de intentarlo.

---

### Post by marianom on 2007-02-20
Bueno, luego de tanto intentar distintas opciones algo salió. Lo posteo por si alguna vez alguien lo necesita.
Como les conté anteriormente, estaba teniendo un error de puerto ocupado al intentar conectar con el ciscovpn.
Intenté luego con vpnc (que es soft libre y está en los repositorios) y me dió una serie de errores varios entre los cuales, en el mejor de los casos, estaba también el del puerto 500 ocupado.
Como no tuve forma de encontrar que ocupaba el puerto justo que yo lo necesitaba, en las opciones de vpnc encontré la salvación.

```
mariano@mishima:~$ sudo vpnc --local-port=0
Enter IPSec gateway address: 10.23.1.0
Enter IPSec ID for 10.23.1.0: Cliente1
Enter IPSec secret for Cliente1@10.23.1.0: 

Enter username for 10.23.1.0: clienteproyecto
Enter password for clienteproyecto@10.23.1.0: 

VPNC started in background (pid: 9063)...

```

Como ven está la opción --local-port=0, la cual le indica al vpnc que use un puerto random (¡¡¡si no puedes con ellos, uneteles!!!).

El resto de las opciones: cliente, pass, etc las ingrese manualmente pero se puede armar un conf file con toda la información de relevancia para no tener que tipearla siempre.

---

