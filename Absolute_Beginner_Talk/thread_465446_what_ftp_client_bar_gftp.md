---
title: "what ftp client bar gftp?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-06-05
having some problems with gftp loosing connection to my xbox which the xbox never does when on windows so what ftp program to transfer between pcs etc...
cheers

---

### Post by finer recliner on 2007-06-05
did you try the command line?

$ftp <server>

---

### Post by jimrz on 2007-06-05
> **keef247 said:**
> having some problems with gftp loosing connection to my xbox which the xbox never does when on windows so what ftp program to transfer between pcs etc...
cheers

openssh works nicely for me. openssh-client is installed by default in feisty. you will need to install openssh-server from Synaptic.

you can then access it by going > Places > Connect to server on your top panel, if you are using gnome. I find, that at least for my setup,
identifying the sever by ip address works better than trying to do so by name. then enter your user name, a window will open asking for your password. 
this should open your file browser with access to your target server.

---

### Post by cjssmo on 2007-06-06
sudo apt-get install proftpd

---

### Post by ikonia on 2007-06-06
Opinions are one mans personal opinion.

Your not asking for opinions on anything hard or life changing, search the package manager, install a few ftp clients, try them see which one YOU like and which one meets YOUR requirments, then uninstall the rest.

Once mans gold, is another mans dirt.

This isn't a life changing or system critical decision, so try for your self.

---

### Post by steve.horsley on 2007-06-06
I use nautilus. In the location bar, type 
**[ftp://username@ipaddress](ftp://username@ipaddress)**
e.g. [ftp://steve@1.2.3.4](ftp://steve@1.2.3.4)

---

### Post by morningboat on 2007-06-07
[CrossFTP]("http://www.crossftp.com/") works for me, and is very reliable.

---

