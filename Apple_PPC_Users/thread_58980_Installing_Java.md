---
title: "Installing Java"
date: 2005-08-22
forum: Apple PPC Users
---

### Post by Freddie on 2005-08-22
Hi, I have been following the guide here to install Java: [https://wiki.ubuntu.com/JavaPPC?highlight=%28ppc%29%7C%28java%29](https://wiki.ubuntu.com/JavaPPC?highlight=%28ppc%29%7C%28java%29) . I have installed Java and have added the 'export PATH="$PATH:/opt/IBMJava2-ppc-142/bin"' to all of my users .bashrc file.

I can play the tic tac toe game fine but I can not find (well a .deb version of) -virtual-machine-dummy. Can someone please tell me what I need to get this and anything else I need to do before java will be correctly set up.

---

### Post by slux on 2005-08-23
I couldn't either but the virtual-machine-dummy package isn't so very important IMO as very few Ubuntu packages depend on java since it's non-free. You create such a dummy package with the equivs package though. If you are successfully running java apps and the path is set you should be good to go.

---

### Post by pvz on 2005-08-23
[http://distro.ibiblio.org/pub/linux/distributions/debian/pool/main/j/java-virtual-machine-dummy/](http://distro.ibiblio.org/pub/linux/distributions/debian/pool/main/j/java-virtual-machine-dummy/)

---

### Post by Freddie on 2005-08-23
Odd thing was that I had to add the line to all of my users .bashrc file. A search found ~/.bashrc as well as one in /etc/skul/.bashrc but add the line to them did not make any difference and I had to add it to /root/.bashrc as well as my normal user accounts  one to get it to work. What am I doijng wrong?

---

