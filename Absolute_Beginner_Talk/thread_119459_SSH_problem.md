---
title: "SSH problem"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by harakiri on 2006-01-19
I am not able to ssh to my DCF account. If I try using ssh the following error is encountered.
> ssh: connect to address 10.195.246.241 port 22: Connection refused
lost connection

actually there is nothing like ssh in
> /etc/init.d/
How do i install ssh? and there are unmet dependencied for ssh (using synaptic) so i am not able to install it. I need ssh urgently
help please...
:((

---

### Post by bscbrit on 2006-01-19
In Synaptic, select 'Settings -> Repositories -> Settings' and then select 'Show disabled software sources'.  Then ensure that all repositories are selected.  Try to install SSH again - although there shouldn't be any 'unmet' dependencies for SSH from a basic installation.

Which files are missing?

---

### Post by bscbrit on 2006-01-19
After installing SSH, make sure that it is activated (sudo /etc/init.d/ssh start).  If you have a firewall, make sure that port 22 (SSH) is allowed through it.

---

### Post by Biased turkey on 2006-01-19
SSH has 2 packages: the server ( openssh-server ) and the client ( openssh-client ) packages.
The system initiating the connection needs the client package installed and the system you want to access must have the server package installed and running.

---

### Post by harakiri on 2006-01-20
I managed to install nd get ssh working. I uninstalled openssh-client and reinstalled it along with other files. Then it gave me no error. One more problem down.
bye hav a nice time

---

