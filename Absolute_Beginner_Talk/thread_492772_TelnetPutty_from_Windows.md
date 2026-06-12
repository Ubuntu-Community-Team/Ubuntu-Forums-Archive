---
title: "Telnet/Putty from Windows"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by ggnanaraj on 2007-07-05
I'm unable to telnet

---

### Post by splintercellguy on 2007-07-05
We need more information to assist you. What client are you using? What error do you get? Stuff like that.

---

### Post by ggnanaraj on 2007-07-05
I'm unable to telnet/putty from Windows to Ubuntu.  However, ping works fine...

I've also installed telnetd using ' sudo apt-get install telnetd'...

When I telnet to localhost get the following message:

root1@root1-desktop:/etc/init.d$ telnet 10.232.52.22
Trying 10.232.52.22...
telnet: Unable to connect to remote host: Connection refused
root1@root1-desktop:/etc/init.d$ 

Any pointers to resolve this?

Thanks in advance.

---

### Post by splintercellguy on 2007-07-05
Please don't make more than one thread. Are you sure the IP is correct, and the telnet server is up? Is connectivity ok?

---

### Post by nitro_n2o on 2007-07-05
AFAIK, 
putty is a SSH  client not telnet 
you need openssh setup on your machine, so: 
```
sudo apt-get install openssh-server openssh-client
```

---

### Post by ggnanaraj on 2007-07-05
> **nitro_n2o said:**
> AFAIK, 
putty is a SSH  client not telnet 
you need openssh setup on your machine, so: 
```
sudo apt-get install openssh-server openssh-client
```

You can use putty as a 'telnet' or 'ssh' client.

When I give 'sudo apt-get install openssh-server openssh-client', I get the following message:
[INDENT]root1@root1-desktop:/etc/init.d$ sudo apt-get install openssh-server openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
root1@root1-desktop:/etc/init.d$ 
[/INDENT]

I have downloaded both server & client for openssh.  However, when I try to install openssh-client, I get the following message - that it is already installed.

[INDENT]root1@root1-desktop:/etc/init.d$ sudo apt-get install openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root1@root1-desktop:/etc/init.d$ 
[/INDENT]

However, trying to install openssh-server gives the following message:
[INDENT]root1@root1-desktop:/etc/init.d$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
root1@root1-desktop:/etc/init.d$ [/INDENT]

The listing of the downloaded openssh files are found below:
[INDENT]root1@root1-desktop:~/Desktop$ ls -l openssh*
-rw-r--r-- 1 root1 root1 536704 2007-07-05 20:10 openssh-client_4.2p1-7ubuntu3.1_i386.deb
-rw-r--r-- 1 root1 root1 205490 2007-07-05 20:09 openssh-server_4.2p1-7ubuntu3.1_i386.deb
root1@root1-desktop:~/Desktop$ [/INDENT]

Am I missing something here?

---

### Post by ggnanaraj on 2007-07-17
> **splintercellguy said:**
> We need more information to assist you. What client are you using? What error do you get? Stuff like that.

I'm trying to telnet from windows to ubuntu.  My inhouse support people say that 'ubuntu workstation' does not allow telnet or FTP.  They have said that Ubuntu server is to be installed.  Is this so?

Please see [http://ubuntuforums.org/showthread.php?t=492775](http://ubuntuforums.org/showthread.php?t=492775) for more information about this issue.

TIA.

---

### Post by albatroz2k on 2007-09-26
Could you finally install openssh-server?
I am having the same problem, but with xUbuntu 7.04 Feisty Fawn

---

### Post by Adramelech on 2007-09-26
Did you allowed the ssh service on the ubuntu firewall?

---

### Post by albatroz2k on 2007-09-26
Solved my issue.
The solution?

Type
sudo apt-get update  
before
sudo apt-get install ssh

---

### Post by ggnanaraj on 2007-10-15
> **Adramelech said:**
> Did you allowed the ssh service on the ubuntu firewall?

How can I do this?

Thanks in advance.

---

### Post by wormser on 2007-10-15
Install Firestarter to control your firewall.

```
sudo apt-get install firestarter
```

Then System> Administration> Firestarter.  Now open up port 22 for an inbound traffic policy.  If you have a router you will have to port forward the same port.

---

### Post by steve.horsley on 2007-10-15
If you haven't installed a firewall then don't worry about it. If you have, then you need to configure that firewall appropriately, and how to do it depends on which firewall you have installed.

It is not right that you need to install Ubuntu server. It is possible to install the telnet server on both the desktop anf the server editions of Ubuntu. Although I and others would suggest using SSH instead of telnet, it's realy your choice.

First, let's see what is actually listening. Enter the command:
netstat -lt
and post the output here. What we are looking for is something listening on either telnet or ssh. My guess is that nothing is listening though. So the next question is, which did you install - the telnet server or ssh server?

---

