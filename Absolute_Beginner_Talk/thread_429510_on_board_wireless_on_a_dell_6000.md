---
title: "on board wireless on a dell 6000"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by bionome on 2007-05-01
I load the latest version on my dell 6000 and everything works great but I alway have to do sudo iwconfig after each reboot. How do I keep the settings to stay all the time I'm new to linux and want to learn.

Thanks

---

### Post by DSn0wMan on 2007-05-01
To keep you settings you will have to add them to /etc/network/interfaces. If you are using Ubuntu 7.04 it is no longer necessary to configure wireless from the command line, or configuration files. I have Dell Inspiron 6000 and all I had to do was click on the gnome-networkmanager applet on the tool bar, select my network, and then give it my WPA passphrase.

---

### Post by bionome on 2007-05-02
Thanks I got it working.

---

