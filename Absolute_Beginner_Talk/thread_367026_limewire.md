---
title: "limewire"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by 006rocks on 2007-02-21
How do I install limewire for ubuntu? I don't get how to extract it and stuff, please explain.

---

### Post by r4ik on 2007-02-21
Give this a read please,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_Gnutella_Client_.28LimeWire.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_Gnutella_Client_.28LimeWire.29)

Good luck !

---

### Post by 006rocks on 2007-02-21
AHHHH!!! that stuff confuses me...

---

### Post by rsambuca on 2007-02-21
Have you tried reading those guides?  I am not sure what part you could be stuck on.

---

### Post by mahy on 2007-02-21
Do you have the actual rpm package? Then just ran alien on it (sudo alien [package].rpm) to create [package].deb and then install it (sudo dpkg -i [package].deb). Then you have to edit the file /usr/bin/limewire and replace the first line to: #! /bin/bash

---

### Post by r4ik on 2007-02-21
Grab frostwire( [http://www.frostwire.com/download.ph...3.1.4.i586.deb](http://www.frostwire.com/download.ph...3.1.4.i586.deb) )

just download the deb and click on it to install. You also got to install Java to make it work, make sure you have all your repos turned on->

sudo apt-get update
sudo apt-get install sun-java5-plugin

It will pull the rest of what you need automatically.
If you prefer GUI you can use synaptic to install java.

It looks the same as limewire but it's like the limewire full version-> [http://www.frostwire.com/](http://www.frostwire.com/)

credits kerry_s

---

