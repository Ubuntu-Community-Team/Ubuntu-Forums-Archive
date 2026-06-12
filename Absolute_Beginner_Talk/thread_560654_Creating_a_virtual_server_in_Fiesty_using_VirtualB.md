---
title: "Creating a virtual server in Fiesty using VirtualBox"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-09-26
I want to create a virtual server that can be integrated into my network in order to get some networking/admin practice. I use virtual box now to try out new distros, run xp, etc. However, I have always used NAT on these machines when creating the virtualbox so they contain a different subnet and ip than the host. Can someone that has done this point me in the right direction? I want the server to appear as another "physical" machine on the same network that can be pinged, monitor traffic, share files, etc. without having to use virtualbox's shared files or ssh.

---

### Post by Dr Small on 2007-09-26
Maybe give it a static IP address, so everything can connect to it that way ?
I dunno, I have never tried that, but I was somewhat curios about your question too.

Dr Small

---

### Post by jba6511 on 2007-09-26
assigning a static ip does not work. It is recognized in network under ubuntu and in network neighborhood in windows xp, but can not be accessed. I also can not ping it from the host or from  another machine. I gave it a static ip different from the host ip address.

---

