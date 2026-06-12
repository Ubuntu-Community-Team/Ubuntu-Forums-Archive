---
title: "Creating a Port"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-09-09
Hey guys. I just kind of started thinking about this, becasue I noticed that you can create ports in FreeBSD. So, what I'm wondering is is that can you create ports in Ubuntu Server? Thanks.

---

### Post by dwhitney67 on 2007-09-09
Your OP is very short and without much detail.  I'll keep my response the same.... yes you can.

---

### Post by drndrw on 2007-09-09
Okay. But then how would you do this? Would you need Apache installed or some other web server?

---

### Post by lespaul_rentals on 2007-09-09
You can't really "create" a port because all ports exist.  But I think you mean "open" a port, correct?  And if so, yes you can.

---

### Post by drndrw on 2007-09-09
Sorry, I did mean open a port. How would I open one then?

---

### Post by steve.horsley on 2007-09-09
Start a server listening on the port in question. 
Which port do you want to open, and why?

---

### Post by drndrw on 2007-09-09
How to I start a sever listening on the port? And I'm not really sure. To be honest, I know little about them. Just to know how would be nice I guess.

---

### Post by schorsch on 2007-09-09
You want to install a web server for example?
```
sudo aptitude install apache2.2-common
sudo /etc/init.d/apache2 start
sudo netstat -anp|grep :80
```
The last command shows that there is a apache listening on port 80. Most servers have a default port that is opened just when the server is started. To get a list of the default ports take a look in the file /etc/services.

---

### Post by drndrw on 2007-09-09
And that would be port 80 or HTTP, correct? So I would run the last command to open a port, only 80 would be another number? And obviously, I don't know much about this, so this would only be over the localhost on my machine or network?

---

### Post by schorsch on 2007-09-09
Well, http is listening on port 80 per default. You can change it in the config of the web server if you want to ... but it might not be clever. And the port is opened by starting the web server (my second command), the third command just checks if the port 80 is opened. Any machine on your network will now be able to connect to port 80 on your localhost.

---

### Post by dwhitney67 on 2007-09-09
> **drndrw said:**
> Sorry, I did mean open a port. How would I open one then?

Please be more specific as to what you want to accomplish.

If you want to develop your own home-made server that opens a particular port, then start by reading the man-page on socket().  After a socket has been successfully created, then the server needs to bind it to a port using bind().  Then the server can accept connections on that port, using accept().

The client must open a socket as well, and then connect to a port (in which there is a server listening for connections).

Servers running as non-root are limited to which ports they can manage.  I believe they cannot bind to a port with a port-number less than 1024.  If running with root-privileges, then any port number can be used.  This explains why a lot of common servers (HTTPD, SSHD, SNMP agent, etc) use port numbers in the lower range.

---

### Post by lespaul_rentals on 2007-09-09
Just to let you know, if you are trying to open a service on your server that is one thing.  But it kind of sounds like you want to open a port just for the heck of it.  I might be wrong though.

If you open a service, such as a web server or FTP server, that will start your server listening on that port.  Here are some examples of some services and their respective ports:

FTP: 21
SMTP: 25
Web: 80
File sharing on Windows: 445
Halo for PC: 2302-2303

See, these ports won't be open (or at least they shouldn't be) unless you have an application using them.  If someone wants to host a game like Halo, ports 2302 and 2303 would be open and listening.  If someone had a web server, port 80 would be open and listening.  If someone had a mail server, port 25 would be open and listening.

So, if you want to "open a port," the way to do that would be start a service that will actively listen.

---

### Post by drndrw on 2007-09-09
Oh, so to use services like FTP and http, I have to first open the port? And on a somewhat unlrelated note, I do play halo so do I need to have the game installed to actually run a game? And on things like http, how would I get it so other people around the world can veiw my web pages? Also, do I need apache installed to open these ports or do I just need to run a command out of the terminal. If so, what command? Would it be one of the bind() like ones listed above?

---

### Post by bwhitaker on 2007-09-09
You probably really don't need to ever worry about opening ports unless you're machine is running a firewall.  When you install a webserver like apache it will listen on a port for you(port 80 by default)   you shouldn't need open a port as the web server will open the port on it's own.  If you would like it to run on another port, in the apache example you would make changes to the httpd.conf file.

This may help you in setting up apache:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)



Just for clarification, you do mean tcp ports(as in networking ports), not the BSD ports projects:
[http://www.freebsd.org/ports/](http://www.freebsd.org/ports/)
[http://www.openbsd.org/ports.html](http://www.openbsd.org/ports.html)
etc

---

### Post by drndrw on 2007-09-10
I'm pretty sure I mean TCP. SO what ports would I need opened if I was to run a hosting service? Or would the apps I need open the ports for me?

---

### Post by lespaul_rentals on 2007-09-21
You need web server software installed if you want a webhost.  Apache is the most common for people such as yourself.  So if you install Apache and get it set up correctly, it will most likely be listening on port 80.

Think of all the different ports as a long line of doors opening to rooms.  If you have some stuff (data) stored in Room 80 (a web server we'll say), you need someone to open the door to let people (basically data packets) in.  So you would have someone open the door to let people in whenever they knocked, you see?

On Linux, by default, all the doors are locked and closed.  So if a person goes to Room 80 to eat lunch, how are they going to get in without a doorkeeper?  However, the doorkeeper can let them in, which is in essence why you need a service running.  Also, simply opening a port and leaving the door wide open is both pointless and a possible security risk.  You need a doorkeeper to keep an eye on what goes on.  Do you see what I'm getting at with my analogy?

So, if you want people to be able to access your web server, you'd need a doorkeeper (Mr. Apache :)), and you'll need to verify that your firewall (if you have any) opens port 80.

---

### Post by drndrw on 2007-09-21
Ah, okay. So a few more questions. Are all of my files then on the internet, or just the ones I have in a certian location (I had apache installed before, so I should understand if you are talking about it)? And what other ports or applications would need to be opened or installed to run a web service? Thanks.

---

### Post by lespaul_rentals on 2007-09-21
Well, it *should* only be the location you specify in your server.  However, if you are concerned about personal data, such as passwords, credit card numbers, and the like, you should't leave those on your web server computer.  Usually, software such as Apache lets you show a folder to the Internet, not your entire computer.

Port 80 is the default web port.  If you are only offering a web server, port 80 should be enough.

---

### Post by dwhitney67 on 2007-09-21
I think 'lespaul_rentals' put everything in simple (layman's) terms for you.  What else is there to understand? Servers that communicate over TCP (or UDP) need to open a port, and typically Apache uses port 80, SSH uses 22, FTP 21, SNMP 161, etc.

Apache, as you know, is a web-server that by default opens and utilizes port 80.  Thus all you have to do (besides installing Apache) to get a web-server running on your personal system is to come up with the content (e.g. images, sound, etc.) that people will see when they connect to your system.

Want to know more about Apache on Ubuntu... [go here]("http://techpatterns.com/forums/about390.html").

---

