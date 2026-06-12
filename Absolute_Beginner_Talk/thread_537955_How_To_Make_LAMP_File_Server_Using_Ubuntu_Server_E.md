---
title: "How To Make LAMP File Server Using Ubuntu Server Edition"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ComputerExpertVK on 2007-08-29
Hey Everyone!
I need some help! How do you make a LAMP file server with Ubuntu Server Edition 7.04?
I went to [http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui](http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui) but I couldn't configure a static IP address since I couldn't edit the  
auto eth0
iface eth0 inet dhcp

---

### Post by arochester on 2007-08-29
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by zaphu on 2007-08-29
@ComputerExpertVK - I see you had trouble configurating your static IP address as per my [post ]("http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/") on [http://ww.zaphu.com](http://ww.zaphu.com). When editing configuration files you must have privileges to do so. This is why you must use the sudo command when opening the interfaces file with vi. Try this and you should be able to configure you static IP address. If you need some help learning how to use a text editor such as vi there are many good guides on Google. Thanks for visiting [www.zaphu.com](www.zaphu.com), I hope you visit often.

---

### Post by ComputerExpertVK on 2007-08-30
thanks you guys...
zaphu...
besides from the static ip address, your site was really helpful compared to other ones.
THANKS A LOT!!!

---

### Post by ComputerExpertVK on 2007-08-30
How do I add files to my LAMP server to share on my local network with linux, mac, and windows computers?

---

