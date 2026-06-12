---
title: "is ssh on by default after install?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by ghmercado on 2007-04-07
just installed 6.10 server.

installed ok then i went back to my winxp machine trying to ssh into it using putty, got 'connection refused'. tried doing '/etc/init.d/ssh start' and i get a 'ssh: connect to host start port 22: connection timed out' message. 

i think it can see the internet anyway, since i can ping yahoo from the console (if that info helps)

obviously need help. much appreciated.

---

### Post by BillGod on 2007-04-07
I am only about 90% sure on this.  I think when I installed it was not evern installed.I had to apt-get install ssh

---

### Post by AndyCooll on 2007-04-07
No it isn't installed by default. You need to install openssh-server.

:cool:

---

### Post by az on 2007-04-07
> **AndyCooll said:**
> No it isn't installed by default. You need to install openssh-server.

:cool:


The ssh client is installed by default, so you can ssh *out* of your new server, but the ssh server is not installed, so ssh is not listening by default (no one can ssh *into* your machine).

If you install the ssh metapackage (sudo apt-get install ssh) it will install the openssh-server package.

---

### Post by kc5hwb on 2007-04-07
I installed the openssh-server package thru Synaptic, rebooted and it was on.  I didn't have to start it.  Putty worked fine connecting to it after a reboot ( I guess I could have attempted to start it instead of rebooting, but I installed a few other things also and just decided to reboot)

---

### Post by ghmercado on 2007-04-08
1st question on ubuntuforums and it has resulted in immediate success. many thanks to all you guys.

---

### Post by LaurelLynn on 2007-04-08
Dear ghmercado,

Don´t forget to generate a set of encryption keys, see here for instructions:

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

If you use only default keys, that may actually be no real protection at all.

Laurel Lynn

---

### Post by ghmercado on 2007-04-08
thanks so much again foxy albeit pixelated lynn!

---

