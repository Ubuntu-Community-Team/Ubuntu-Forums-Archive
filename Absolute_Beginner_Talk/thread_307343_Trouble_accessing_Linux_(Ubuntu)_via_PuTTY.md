---
title: "Trouble accessing Linux (Ubuntu) via PuTTY"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by gt4play on 2006-11-26
Hi all,

I am a definite newbie to Ubuntu, but I'm not sure if this issue constitutes a newbie forum entry...but here goes.

Currenty I have a 3-computer network at home.  Two machines are dedicated windows (1 as XP Pro and te other 2000) while the 3rd is a part windows (XP Pro), part ubuntu.  I'm trying to setup CVS server on my Ubuntu machine and gain access to that server from my other two windows machines via SSH.

Sooo, I'm trying to use PuTTY to (1st) try and gain passworded access to my linux machine from my XP machine.  As a reference (and it seems to be useful) I found this link:

[http://www.unixwiz.net/techtips/putty-openssh.html](http://www.unixwiz.net/techtips/putty-openssh.html)

I can't even make it beyond the first step of simply logging into my linux machine withOUT ssh.  I get a "Network Error:  Connection Refused" dialog.

I'm a software developer, not a networking pro.  So I'm learning as a go.  But I'm convinced this is a networking issue.

From my Ubuntu terminal, these commands yield the following...

hostname >>> unix-storage
hostname -i >>> 127.0.1.1

From my XP terminal, these commands yeild the following...

ping 127.0.1.1 >>> a successful ping
ping unix-storage >>> "Ping request could not fine host unix-storage"

It might be useful to note that the same scenario occurs if I trying pinging my XP machine from the Ubuntu terminal; IP address works fine, hostname fails.

Can somebody help point me in the right direction?  

Thanks much!

-Chris

---

### Post by zaratustra on 2006-11-26
got ssh server in runlevel @ machine u want to ssh @?

---

### Post by NetworkGuy on 2006-11-26
Did you install openssh (server) package from synaptic.  By default Ubuntu doesn't install that package.

---

### Post by justifier on 2006-11-26
127.0.1.1 is local host on any machine in the world, you got a ping back because you were pinging your self, as for ssh, i don't know, i could do to set it up too but that should awnser your ping part, do you have all samba and smb packages installed? this some times helps with windows and stuff on the network

---

### Post by zaratustra on 2006-11-26
this should solve it...
install openssh if you don't have it... do it with synaptic if you aren't familiar with console front-end of APT.
I don't know the package name, (ain't ubuntu user), but search for openssh
and install it. 
Then do this
```
#sudo /etc/init.d/sshd start
```to get ssh deamon in runlevel
*** /etc/init.d/sshd maybe isn't path to the script so check that and change if neccessary
```
#ssh your_host -l yourusrname
```test it from other machine
```
#sudo /etc/init.d/sshd stop
```stop deamon

---

### Post by gt4play on 2006-11-26
All so far seem to be very useful pieces of info, but I'm thinking my issues (thus far) have nothing to do with SSH.  All I'm (initially) trying to do (and failing miserably at) is login to my Linux machine from an XP machine using Putty (a simple username and password).  Technically, once I go the route of SSH, there are no passwords...but if I can't do a simple login to my linux machine remotely first, SSH is hopeless.

BTW, I have installed OpenSSH via the following:

sudo apt-get install openssh-server

But I have not taken the additional steps (yet) mentioned here.  I will definitely be all over that once I have confirmed I'm able to do a simple remote login.

As for the IP for localhost, I should have known that (duh).  So, clearly if I cannot ping either machine using the hostname, this should clearly pose a problem, no?

Thanks!

---

### Post by digitalntburn on 2006-11-26
If ICMP echo is disabled on your Ubuntu system (*which I believe it is by default*) then the ping will not return to the Windows systems.

On the Ubuntu box:
[LIST=1]
[*]Open Network Tools.
[*]Select the Port Scan tab.
[*]Enter your hostname and click Scan Ports.
[/LIST]
SSH should be listed on port 22.

---

