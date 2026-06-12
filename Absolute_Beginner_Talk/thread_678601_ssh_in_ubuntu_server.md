---
title: "ssh in ubuntu server"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mattycakes on 2008-01-26
hello im very new to using linux as in this is my first install
i was reading a tutorial on how to set up a home server with ubuntu server 7.10 so i installed it and just set it up for open ssh and when i say set up i mean i just installed it at the end of the ubuntu install.
in the tutorial it says you can finish the setup by ssh into ubuntu over your network with putty.  so i get putty and put in my user@ip but all i get is a message saying  "network error connection refused".
i called the server "homeserver"  and when i put that in it says "unable to open connection to homeserver host does not exist"
anyway i know this post is long and probably a simple problem to fix but im boggled and i dont know what im doing wrong or not doing and ive been trying to find out how to fix this all day and im tired so any help would be greatly appreciated.
and my apologies if this is a repost.

---

### Post by gvartser on 2008-01-26
do you have a working network on your Ubuntu machine?

Test using ping from your windows machine.

```
ping ip address
```

If you get an answer that its up and running, then It could depend on one of the following things: 
* your ssh server is not up and running.
OR
* Check that you are connecting using port 22 in putty, default it is set to use telnet port.

To start the ssh server:
Logon to the ubuntu locally and start it using: 
```
sudo /etc/init.d/sshd start
```

If you don't get an answer from your ping, then you probably have to check your network setup.

/g

---

### Post by nemilar on 2008-01-26
If you want to ssh to the machine by hostname, you need to add it to your network machine's hosts file (if you want to ssh from windows to homeserver, you need to add "homeserver" to the windows host file, to point it to your IP address of the linux machine).  Or, you can give your entire network a domain name, as described in this tutorial:

[http://www.techthrob.com/tech/dyndns.php]("http://www.techthrob.com/tech/dyndns.php")

As for the other problem, you should see if sshd is accepting connections.  Install nmap:

```
sudo apt-get install nmap
```

and then run

```
nmap [your ip address/domain name] -p 22
```

To see if the port is open/closed.  If you want to setup a domain name for your network, don't forget to forward port 22 in your router!

Can you ssh to localhost on your linux server?

---

### Post by mattycakes on 2008-01-28
ok i pinged the server and got a response but when i enter
sudo /etc/init.d/sshd start  it says cammand not found

---

### Post by emarkd on 2008-01-28
I think it's just

```
sudo /etc/init.d/ssh start
```

---

### Post by Dr Small on 2008-01-28
That would be:
```
sudo /etc/init.d/ssh start
```

Also, please be sure port 22 is open, otherwise you will receive the connectionr refused error.

Dr Small

---

### Post by The Cog on 2008-01-28
If you installed openssh-server, it should start listening straight away. If it is running, you should see it listed in the output from this command (which lists all the running processes with sshd in them):
```
ps -ef | grep sshd
```
but beware that it will likely also list "grep sshd" which is the command you just ran!
The command 
```
sudo netstat -plnt
```
should also show it listening on either :::22 or 0.0.0.0:22.

I think your problem in your original post is that windows doesn't recognise the name homeserver and can't look it up. You could add the name and address to the windows hosts file as a permanent lookup if you like. Add the line:
```
homeserver 1.2.3.4
```
to the file c:\\windows\system32\drivers\hosts (I think that's the right path) and correct the IP addess of course.

---

### Post by gvartser on 2008-01-28
Of course it is 
```
sudo /etc/init.d/ssh start
```

My mistake, sry bout that..

/g

---

### Post by Nythain on 2008-01-28
seriously stupid questions here but.
A. are you running any firewall software? ie Firestarter if you are runnin a Desktop Environment at all, or any other software that would have modified/enabled iptables (wich actually sits pretty empty and idle untill called upon)

B. is port 22 forwarded on your router??? Not sure how important this is in local network but hey, to be on the safe side eh

C. what happens when you use the servers ip address instead of the hostname... ie 192.168.1.X (if you were on a standard lan)

hope any of that possibly helps... guess it isnt much more than whats already been said, just itemized a little bit... really dont think you need to forward ports on your router for local traffic like that, and doing so could actually be more of an exposure risk to teh outside world by redirecting all ssh attempts to your computer

---

### Post by mattycakes on 2008-01-28
a. i am not running any firewall software 
b. i dont think it is but from what i can gather my network doesnt have a domain so i dont think i need to???
c.  when i put in the ip it says network error connection refused

---

### Post by mattycakes on 2008-01-28
ok so i know i said i installed an open ssh server and i did but i went and installed ssh again cause i was getting angry that i couldnt do anything and now i am able to ssh to my server 
so thank you all for the help it is greatly appreciated

---

### Post by PinkFloyd102489 on 2008-01-28
If you still arent able to connect by hostname, do this:


```

sudo apt-get install winbind

```

Then make the bold change in /etc/nsswitch.conf:

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns **wins** mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Afterwards, restart the Winbind server by doing:
```

sudo /etc/init.d/winbind restart

```

You need to do this on both Ubuntu machines in order to get it to work correctly.

---

