---
title: "Ssh"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by prc320 on 2007-05-01
Hi

1. The first problem is how do I know what my host name is?

2. How do I get the man page for this? (ssh)

Any helpers?

Robert

---

### Post by lluisanunez on 2007-05-01
Open a terminal. The first thing to appear is your username + @ + yourmachine.
You can see it also in System > administration > networking > hosts
To see SSH man, type 
```
man SSH
```
and to quit
```
Q
```

---

### Post by Skrynesaver on 2007-05-01
on the command line type hostname, however this isn't going to help you login from outside unless you have a valid domain.

What you are more likely to use is your IP
```
ifconfig -a
```
One of theese will be your external address, it will have inet addr: <somenumbers and .s>
from outside simply ssh username@<somenumbers and .s>

2) man ssh

---

### Post by az on 2007-05-01
If you have an IP address that keeps changing (like if you are on a residential internet connection) use DYNDNS to keep in touch:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by prc320 on 2007-05-01
Skrynesaver

I get the following error message:

symsr1@Toshiba:~$ ssh symsr1@192.168.1.7
ssh: connect to host 192.168.1.7 port 22: Connection refused
symsr1@Toshiba:~$ 


Robert

---

### Post by Bachstelze on 2007-05-01
Is there a SSH server running on 192.168.1.7 ?

---

### Post by bernied on 2007-05-01
You will need to provide more information if you want help that will work for you.
It looks to me like you are trying to establish a connection from somewhere away from the computer that you are connecting to. Is that right? Like, you are trying to connect from work to home?

That IP address you used is a local address, used only on a local network. This is not the address that will be seen by the outside world. That outside IP address is provided by your internet service provider (ISP) and is perhaps only known to your router (that's how you connect to connect to the outside world, right?). So you need to find a way of accessing that address from the outside world. The DynDNS service suggested by az will work, and that DynDNS site will even tell you your current IP address (if I remember correctly), though once you have a dynamic dns setup you don't need to know this.

You also need to have a route from the outside world to the computer that you want to connect to. This is usually configured in the router, so you'd map incoming connections on port 22 to 192.168.1.7

You also need to be running a ssh server on the machine, as has just been pointed out. You can test that this is working properly simply by:
```
ssh localhost
```
from the machine that you are trying to connect to. 

Be careful with this - you are potentially opening up your machine to the outside world. You should do some more reading and understand what you are doing before you set this up.

---

### Post by az on 2007-05-01
> **bernied said:**
> 
You also need to be running a ssh server on the machine, as has just been pointed out. .

The ssh client is installed by default.  So you can ssh out of a machine running Ubuntu.  To ssh *into* a machine running Ubuntu, you need to install the ssh server 

sudo apt-get install ssh

---

### Post by Bachstelze on 2007-05-01
The actual ssh server package is *openssh-server*.

Installing *ssh* will work too, and won't do any harm but trying to have as few useless packages as possible on your system is a good Linux habit.

---

