---
title: "Connecting to Fesisy wireless from windows box over secureCrt ?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by boardtc on 2007-10-03
I am still trying to get my ubuntu feisty box operational.

I installed a wireless dongle which works well. In /etc/network/interfaces my inet addr for rausb0 is 192.168.2.4. I can ping this from my windows box.

I want to setup securecrt on my windows box to connect to the linux box. When I set a connection for this ip uising ssh2 and try and connect I get:

---------------------------
SecureCRT
---------------------------
Connection to session TYK failed :

The remote system refused the connection.  This probably means that the remote system does not
provide the service you are attempting to access,or that the service is being provided on a different
port.

Does anyone know how i can get this working?

Thanks, Tom.

---

### Post by dwhitney67 on 2007-10-04
Your Linux box probably does not have a Secure Shell (SSH) server running.  To enable that, run the following command:

$ sudo apt-get install ssh openssh-server

---

### Post by boardtc on 2007-10-16
That worked perfectly, thank you!

Now looking at [http://www.nomachine.com](http://www.nomachine.com) for gui access....got server installed and client, just need to workout how to set keys....

---

### Post by dwhitney67 on 2007-10-16
X-window applications can be run using an ssh-client.  From Linux, one would connect to the remote server using:

[FONT="Courier New"]$ ssh -X remoteServer[/FONT]

The -X indicates to tunnel through the X-window info through the port used by SSH.

If you want to setup keys for your remote server, thus obviating the need to specify a password when you login, you will need to generate a public-key that can be installed on the remote server.  To do that you need to:

[FONT="Courier New"]$ ssh-keygen -C user@myHostName[/FONT]
<where myHostName is the hostname of the local system; answer yes or hit 'enter' for each question asked>

[FONT="Courier New"]$ gedit ~/.ssh/id_rsa.pub[/FONT]
<copy the entry in that file>

[FONT="Courier New"]$ ssh -X remoteServer[/FONT]
<type in the password>

[FONT="Courier New"]$ gedit ~/.ssh/authorized_hosts[/FONT]
<paste entry from id_rsa.pub and save file>

[FONT="Courier New"]$ exit[/FONT]
<exit the current session on remoteServer>
[FONT="Courier New"]
$ ssh -X remoteServer[/FONT]
<you should not be prompted for a password this time>

---

### Post by boardtc on 2007-10-17
i installed as you suggested and it connected fine...i'm not sure what your last post was for...over my head anyway....just trying to figure out now how to connect nomachine client to server.....

---

