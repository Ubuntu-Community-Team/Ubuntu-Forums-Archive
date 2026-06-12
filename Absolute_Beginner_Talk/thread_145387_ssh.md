---
title: "ssh"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by awalesminfo on 2006-03-16
hi guys am new to kubuntu and facing problem with ssh when i type usrname@ipaddr it says " ssh: connect to host 192.168.10.110 port 22: Connection refused " plese help me from getting through this:-|

---

### Post by andlinux21 on 2006-03-16
Do you have a router? is the port forwarded?

---

### Post by dvarsam on 2006-03-16
Setup port forwarding on the Router, to send all Port 22 request to the Desktop.
Make sure that the Router's Firewall is allowing Port 22 to come in.

To do this, launch your "Synaptic Package Manager": 

sudo synaptic

And perform a search with the keywords "port forward".

There seem to be several programs there, like "guidedog" for instance.

Check this out too:

	[http://www.linux.org/docs/ldp/howto/...orwarders.html](http://www.linux.org/docs/ldp/howto/...orwarders.html)

Have fun!

---

### Post by mlind on 2006-03-16
if your trying to ssh on your own linux box, you need to install openssh-server package.

---

### Post by steve.horsley on 2006-03-16
192.168.10.110 is not listening for SSH connections on port 22. It is probably not running sshd, the ssh daemon. As mlind says, the the box you are trying to SSH to is an Ubuntu box, installing package openssh-server should do the trick. Beware - there are lots of robots out there that look for SSH servers and just sit there trying passwords all day. You would be wise to look at:
* using certificates insterad of password authentication
* using a firewall to limit who can connect to the server
* using hosts.allow and hosts.deny to limit who can connect to the server

---

### Post by awalesminfo on 2006-03-17
thanks guys i installed all packages needed but still facing the same problem :-| :-| :-|

---

### Post by TheKingofZZT on 2006-03-17
Is the system you're connecting to the one you're on? Have you install OpenSSH on the system you're connecting to?

---

### Post by patrick295767 on 2006-03-17
1/Try to ping it first the pc 

2/ make sure that openssh and ssh installed via apt-get -f -y install 

3/ check your firewall  for port forwarding (dmz nfo)
 
4/ try the ssh 
  
5/ if not working, you can try the rlogin 
rlogin IP_address_distantPC -l username

---

### Post by steve.horsley on 2006-03-17
Do you own / control the PC you are trying to connect to? If not, who does?

Is it on the same LAN, in a different part of the same campus network, or do you need to go across the Internet to reach it?

What packages did you install, and on which machine?

---

