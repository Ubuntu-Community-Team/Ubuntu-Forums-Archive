---
title: "Crear un servidor radio Icecast2 + Internet DJ Console Ubuntu 7.10"
date: 2007-10-29
forum: Catalan Team
---

### Post by kernic on 2007-10-29
Instalar servidor Icecast2 + Internet DJ Console

Ubuntu Desktop Gutsy Gibbon 7.10

Instalar Icecast2

Obrir un terminal (identificar-se com a root)

$ sudo su

entrar el password

Instalar el servidor Streamer Icecast2

$ apt-get install icecast2

editar el fitxer de configuració .xml

$ cd /etc/icecast2/
$ gedit icecast.xml

Editar icecast.xml a les linies següents:

<clients>10</clients> (escollir el numero de clients que podran escoltar a la vegada)

<authentication>
        <!-- Sources log in with username 'source' -->
        <source-password>hackme</source-password> (entrar el password)
        <!-- Relays log in username 'relay' -->
        <relay-password>hackme</relay-password> (entrar el password)

        <!-- Admin logs in with the username given below -->
        <admin-user>admin</admin-user>
        <admin-password>hackme</admin-password> (entrar el password)
    </authentication>

Guardar i sortir.

Per engegar el servidor escriure dins d'una terminal el següent:

$ sudo /etc/init.d/icecast2 start

Per parar:

$ sudo /etc/init.d/icecast2 stop

INSTALAR INTERNET DJ CONSOLE (CLIENT STREAMER PER EMETRE A INTERNET)

Funciona amb Audio Jack. Per activar automàticament Jack a la vegada que engegues IDJC escriure el següent en una terminal:

$echo "/usr/bin/jackd -d alsa -r 44100" >~/.jackdrc

Obrir un terminal (identificar-se com a root)

$ sudo su

entrar el password

Intalar Internet DJ Console

$ apt-get install IDJC

per executar el programa:

descarregar la versió idjc_0.7.2 clicant [http://ubuntuforums.org/attachment.php?attachmentid=48291&d=1193664797]("http://ubuntuforums.org/attachment.php?attachmentid=48291&d=1193664797")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48292&stc=1&d=1193664987[/IMG]

Per a configurar clicar el butó de server:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48293&stc=1&d=1193664988[/IMG]

Type: Icecast2
Host: (escriure ip del servidor, normalment localhost o 127.0.0.1)
Port: 8000
Mount: directa.mp3

Reomplir informació a "Stream Info"

Ja tenim el servidor a punt i ja es poden afegir cançons tant a la pista 1 com a la 2.

Per a que s'executi automàticament el icecast2 cada només engegar-se l'ordinadó s'ha de crear un script:

$ sudo gedit /usr/local/sbin/icecast.pl

enganxar el següent:
--------------------------
#!/usr/bin/perl

#### Icecast 2 #########

$ICECAST_CONFIG_XML="/opt/icecast/etc/icecast.xml";

$ICECAST="/opt/icecast/bin/icecast";

foreach (`$ICECAST -b -c $ICECAST_CONFIG_XML`) { print $_;};

### FIN ####
--------------------------
guardar

canviar els permisos:

$ chmod 555 /usr/local/sbin/icecast.pl

fet.

El servidor ja està en marxa!!! sort

---

