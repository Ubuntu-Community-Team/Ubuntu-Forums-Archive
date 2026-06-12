---
title: "Driver install problems"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by captainjojo on 2006-02-03
need to install driver for my linksys WUSB11 ver. 2.8 wireless adaptor, have found driver I think will work but am unable to install! never done this before, Heeeelp

---

### Post by MrCheese on 2006-02-03
You need to be a superuser to install system stuff like drivers - usually on Ubuntu this means "sudo" - eg. sudo *command* which will execute *command* as root.

If your driver is a Windows driver you will need to use ndiswrapper - install this using synaptic. There is a gui config tool for ndiswrapper, install this too. Copy your windows driver to somewhere on the hdd - I use /usr/lib/hotplug/ndis - and point the config tool to this folder. 

Good luck :))

---

### Post by captainjojo on 2006-02-03
Hi Thanks for the reply. I have the windows driver disc that came with the adaptor and have also downloaded and copied to disc a linux driver "at76c503a-cvsroot.tar" . installed nadiswrapper as instructed but can't find the application anywhere on my Ubuntu! am very new to Linux probably just don't know where to look! I also tried to install the Linux driver through the Terminal used instruc's from another thread without any success. Would very much like to get on line using Ubuntu as I only have a wireless connection and am tied of being at Microsoft's mercy!!!

---

