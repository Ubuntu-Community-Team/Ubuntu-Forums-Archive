---
title: "Ports not open for Windows Client to Linux Server"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by shoutchens on 2007-09-23
Hi All,

I have two computers on the home network.  One is Ubuntu 7.04 and the second is a Windows Vista 
system.  I have a Linksys Broadband Router connecting the two  systems.

On the Ubuntu system, I have configured LAMP, FTPd and Perforce.  From the Windows system, I can 
http and ftp to the Linux box as expected.  However, I am not able to connect to the mySQL or 
Perforce instances on the Linux box.

Perforce (p4) works fine on the Linux box using "localhost:1666" as host and port.  However, trying 
to make the connection to the Perforce instance from the Windows box yields the following message:

[FONT="Courier New"]TCP connect to 192.168.1.105:1666 failed.
connect: 192.168.1.105:1666: WSAECONNREFUSED[/FONT]

From the Linux machine, I use Nmap and receive the info below for localhost.

[FONT="Courier New"]Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-23 11:27 PDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1686 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
953/tcp  open  rndc
1666/tcp open  netview-aix-6
3306/tcp open  mysql
5900/tcp open  vnc[/FONT]

From the Windows machine, using Nmap for the linux box (192.168.1.105) I get:

[FONT="Courier New"]Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-23 09:25 Pacific Daylight Time
Interesting ports on 192.168.1.105:
Not shown: 1690 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5900/tcp open  vnc[/FONT]

Can anyone point me in the right direction to set up the configuration of the two machines, so that 
a Windows client will be able to connect to the Perforce Linux instance on port 1666?  I believe it may be the same problem and solution for the Windows client connecting to the Linux instance of mySQL on port 3306.

Thanks for your help.

Steve

---

### Post by str8line on 2007-09-23
The issue with ports on the network is with the router itself.  You will need to log in to the router GUI (Graphical User Interface) and do port forwarding for your Local Network for those services on the LAMP server.  Even with the embedded firewall of a router turned off there are some ports that need to be configured to allow full access.

A good guide for doing port forwarding can be found at [www.portforward.com]("http://www.portforward.com")

---

### Post by airtonix on 2007-09-24
it has nothing to do with your router.

it has everything to do with your firewall settings on your linux box

you need to install firestarter to easily edit the firewall rules.

> sudo apt-get install firestarterthen run firestarter

> gksudo firestarterthen create rules that allow access from anyone on ports 1666 and 3306.

or if you only want computers in your loclanet to reach it then you need to put in the ip-range of 192.168.0.0/24

so you'll be allowing traffice from 192.168.0.1-192.168.0.254 on ports 1666 and ports 3306.

why does http and ftp work? becuase the install packages create rules for them. 

but mysql does not...becuase it is not usually good practice to expose a mysql server to anything outside of the box it runs on...meaning only progs on same computer should really be accesssing the mysql-server.

this is what the principle behind using php/asp for databse access is all about.


Port Forwarding is only used when you are connecting to a box that does not have the server on it...like when for example I access your mysql server....i would be touching your router first...

and it is here at the router which port forwardind needs to occur so that my traffic destined for a mysqlserver actually gets forwarded to one..

hence the router will forward trafic on a specificed port to the same port(or different) on another computer.

if you dont....i will get an error saying the machine i tried connecting to either has rejected your request(you have no access) or there was no valid mysql-server relply on this port...(meaning no mysql-server on the deivce i touched)

so you want to expose your mysql dbase to the world....go portforwarding.

otherwise leae your router alone and stick with my first suggestion.

---

